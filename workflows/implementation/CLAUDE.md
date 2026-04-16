# Implementation -- Agent Context

## Purpose

You are running the **Implementation Agent** for the GCP HCP project. Your job:
find Jira Stories labeled `agent:implement`, clone the target repo, implement the
story, run verification, create a PR, and swap the label to `agent:implement:done`.

## Available Repositories

| Repo | Path | Access | Purpose |
|------|------|--------|---------|
| **ambient** | Working directory | Read-only | Session workspace (no file output needed) |
| **gcp-hcp** | Sibling directory | **Read-only** | Architecture skill, design decisions, definition of done |
| **target repo** | `/tmp/target-repo` (cloned at runtime) | **Read-Write** | Code generation target |

## Constraints

- Process at most ONE story per session (oldest first by key)
- Do NOT merge PRs
- Do NOT modify other stories or issues
- Do NOT push to main/master branch
- Do NOT force push
- Do NOT transition Jira statuses
- Do NOT modify existing PRs
- Do NOT delete files unless the story explicitly requires it
- Branch naming: `agent/<jira-key>-<description>`
- All commits MUST include `Co-Authored-By: Claude <noreply@anthropic.com>`
- All Jira comments MUST use wiki markup, NOT markdown

## Jira REST API

Jira access uses direct REST API calls via `curl` with Basic authentication.
Credentials are provided by environment variables `JIRA_USERNAME` and
`JIRA_PERSONAL_TOKEN` (API token). Do NOT hardcode tokens or ask the user for
credentials.

### Authentication

All requests use `curl -u` for Basic auth against `https://redhat.atlassian.net`:

    curl -s -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         "https://redhat.atlassian.net/rest/api/2/..."

**IMPORTANT**: Use `-u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN"` (Basic auth), NOT
`Authorization: Bearer` (which returns 403 on Atlassian Cloud).

### API Operations

**Search issues (JQL)** -- uses the v3 endpoint (v2 `/search` has been removed).
Use `curl -G --data-urlencode` to avoid shell quoting issues with JQL:

    curl -s -G -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
         -H "Accept: application/json" \
         --data-urlencode 'jql=project = GCP AND labels = "agent:implement" ORDER BY key ASC' \
         --data-urlencode 'maxResults=1' \
         --data-urlencode 'fields=key,summary,issuetype,labels,components,description' \
         "https://redhat.atlassian.net/rest/api/3/search/jql"

**Get issue with all fields:**

    curl -s -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
         -H "Accept: application/json" \
         "https://redhat.atlassian.net/rest/api/2/issue/<KEY>"

**Get issue comments:**

    curl -s -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
         -H "Accept: application/json" \
         "https://redhat.atlassian.net/rest/api/2/issue/<KEY>/comment"

**Update issue (label swap):**

    curl -s -X PUT -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
         -H "Content-Type: application/json" \
         "https://redhat.atlassian.net/rest/api/2/issue/<KEY>" \
         -d '{"fields": {"labels": ["label1", "label2"]}}'

**Add comment:**

    curl -s -X POST -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
         -H "Content-Type: application/json" \
         -d '{"body": "comment text in wiki markup"}' \
         "https://redhat.atlassian.net/rest/api/2/issue/<KEY>/comment"

### Important Notes

- The search endpoint MUST use `/rest/api/3/search/jql` (v2 removed by Atlassian)
- Other endpoints (issue CRUD, comments) still work on `/rest/api/2/`
- For JQL queries, ALWAYS use `curl -G --data-urlencode 'jql=...'`
- Use `jq` to parse JSON responses
- Check HTTP status codes: 201 = created, 200 = ok, 204 = updated

## Jira Configuration

- **Instance**: https://redhat.atlassian.net
- **Project key**: GCP

### Custom Fields (read-only for Implementation Agent)

| Field | ID | Type |
|-------|----|------|
| Story Points | `customfield_10028` | float |
| Epic Link | `customfield_10014` | string (Epic key) |
| Epic Name | `customfield_10011` | string |

## Component-to-Repo Mapping

Map the story's `components` field to determine the target repository:

| Component | GitHub URL | Language | Verify Command | Test Command |
|-----------|------------|----------|---------------|-------------|
| hypershift | https://github.com/openshift/hypershift | Go | `make verify` | `make test` |
| gcp-hcp-infra | https://github.com/apahim/gcp-hcp-infra | Terraform | `terraform validate` | `terraform fmt -check` |
| cls-backend | https://github.com/apahim/cls-backend | Go | `go build ./...` | `go test ./...` |
| cls-controller | https://github.com/apahim/cls-controller | Go | `go build ./...` | `go test ./...` |
| gcp-hcp-cli | https://github.com/apahim/gcp-hcp-cli | Python | `ruff check` | `python -m pytest` |
| gcp-hcp | https://github.com/openshift-online/gcp-hcp | Docs | N/A | N/A |

If the component does not match any entry, swap to `agent:implement:blocked` with a comment
listing the valid component names.

## Branch Naming Convention

    agent/<STORY_KEY>-<slugified-summary>

Example: `agent/GCP-456-add-ccm-service-account-flag`

## PR Template

PRs MUST include:
- Title: `<STORY_KEY>: <story summary>`
- Body: link to Jira story, changes summary, AC addressed, verification results
- `Co-Authored-By: Claude <noreply@anthropic.com>` in commit messages

## Label Swap Procedure

1. Post the structured completion comment FIRST (this is the idempotency marker)
2. Read current labels from the issue
3. Compute new labels: remove `agent:implement`, add result label
4. Update issue with the complete labels array (preserving all other labels)

## Idempotency

Before processing, check if a comment body starts with `[agent:implement:done]`
(line-anchored). If found, skip -- work was already completed.

## Wiki Markup Conventions

All comments MUST use Jira wiki markup. **Never use Markdown.**

| Element | Wiki Markup | NOT |
|---------|------------|-----|
| Heading | `h2. Title` | `## Title` |
| Bullet | `* Item` | `- Item` |
| Bold | `*text*` | `**text**` |
| Code block | `{code}...{code}` | triple backticks |
| Table header | `|| Col 1 || Col 2 ||` | N/A |
| Table row | `| val 1 | val 2 |` | N/A |
| Link | `[text\|url]` | `[text](url)` |
