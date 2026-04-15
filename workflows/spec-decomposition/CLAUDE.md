# Spec Decomposition -- Agent Context

## Purpose

You are running the **Spec Agent** for the GCP HCP project. Your job: find Jira
issues labeled `agent:spec` and decompose them following the hierarchy:
Features into Epics, Epics into Stories. Then swap the label to `agent:spec:done`.

## Available Repositories

| Repo | Path | Access | Purpose |
|------|------|--------|---------|
| **ambient** | Working directory | Read-only | Session workspace (no file output needed) |
| **gcp-hcp** | Sibling directory | **Read-only** | Story templates, design decisions, architecture skill, sizing guide |

## Constraints

- Process at most ONE issue per session (oldest first by key)
- Do NOT assign issues, move them to sprints, or transition statuses
- Do NOT modify existing issues (only create new child issues)
- Do NOT push code to any repository
- All created issues MUST have label `ai-generated-jira` and security `{"id": "10034"}` (Red Hat Employee)
- Do NOT create test/throwaway issues to discover fields — use the field IDs documented below
- Use Jira wiki markup (`h2.`, `*`, `{code}`), NOT markdown (`##`, `-`, `` ``` ``)

## Jira REST API

Jira access uses direct REST API calls via `curl` with Basic authentication.
Credentials are provided by environment variables `JIRA_USERNAME` (email) and
`JIRA_PERSONAL_TOKEN` (API token). Do NOT hardcode tokens or ask the user for credentials.

### Authentication

All requests use `curl -u` for Basic auth against `https://redhat.atlassian.net`:

```bash
curl -s -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Content-Type: application/json" \
     -H "Accept: application/json" \
     "https://redhat.atlassian.net/rest/api/2/..."
```

**IMPORTANT**: Use `-u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN"` (Basic auth), NOT `Authorization: Bearer` (which returns 403 on Atlassian Cloud).

### API Operations

**Search issues (JQL)** — uses the v3 endpoint (v2 `/search` has been removed).
Use `curl -G --data-urlencode` to avoid shell quoting issues with JQL:
```bash
curl -s -G -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Accept: application/json" \
     --data-urlencode 'jql=project = GCP AND labels = "agent:spec" ORDER BY key ASC' \
     --data-urlencode 'maxResults=1' \
     --data-urlencode 'fields=key,summary,issuetype,labels' \
     "https://redhat.atlassian.net/rest/api/3/search/jql"
```

**Get issue with all fields:**
```bash
curl -s -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Accept: application/json" \
     "https://redhat.atlassian.net/rest/api/2/issue/<KEY>"
```

**Get issue comments:**
```bash
curl -s -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Accept: application/json" \
     "https://redhat.atlassian.net/rest/api/2/issue/<KEY>/comment"
```

**Create issue:**
```bash
curl -s -X POST -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Content-Type: application/json" \
     -H "Accept: application/json" \
     -d '{"fields": {...}}' \
     "https://redhat.atlassian.net/rest/api/2/issue"
```

**Update issue:**
```bash
curl -s -X PUT -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Content-Type: application/json" \
     "https://redhat.atlassian.net/rest/api/2/issue/<KEY>" \
     -d '{"fields": {...}}'
```

**Add comment:**
```bash
curl -s -X POST -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"body": "comment text"}' \
     "https://redhat.atlassian.net/rest/api/2/issue/<KEY>/comment"
```

**Get link types:**
```bash
curl -s -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Accept: application/json" \
     "https://redhat.atlassian.net/rest/api/2/issueLinkType"
```

**Create issue link:**
```bash
curl -s -X POST -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"type": {"name": "Blocks"}, "inwardIssue": {"key": "..."}, "outwardIssue": {"key": "..."}}' \
     "https://redhat.atlassian.net/rest/api/2/issueLink"
```

### Important Notes

- The search endpoint MUST use `/rest/api/3/search/jql` (the v2 `/rest/api/2/search` has been removed by Atlassian)
- Other endpoints (issue CRUD, comments, links) still work on `/rest/api/2/`
- For JQL queries, ALWAYS use `curl -G --data-urlencode 'jql=...'` — do NOT manually URL-encode or use `echo | jq @uri` (shell quoting around labels like `"agent:spec"` breaks silently)
- Use `jq` to parse JSON responses when needed
- For large JSON payloads (issue creation), use a heredoc: `curl ... -d "$(cat <<'EOF' ... EOF)"`
- Check HTTP status codes: 201 = created, 200 = ok, 204 = updated
- Do NOT ask the user to configure credentials -- they are provided by the platform

## Jira Configuration

- **Instance**: https://redhat.atlassian.net
- **Project key**: GCP
- **Contact**: asegundo@redhat.com

### Custom Fields

| Field | ID | Type |
|-------|----|------|
| Story Points | `customfield_10028` | float |
| Epic Link | `customfield_10014` | string (Epic key) |
| Epic Name | `customfield_10011` | string |

### Security Level

Always use `"security": {"id": "10034"}` (Red Hat Employee). Do NOT use `{"name": "..."}` — it returns a validation error on this instance.

### Create Story Example

```bash
curl -s -X POST -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Content-Type: application/json" \
     -H "Accept: application/json" \
     "https://redhat.atlassian.net/rest/api/2/issue" \
     -d "$(cat <<'EOF'
{
  "fields": {
    "project": {"key": "GCP"},
    "issuetype": {"name": "Story"},
    "summary": "Story title here",
    "description": "h2. User Story\n\n...",
    "labels": ["ai-generated-jira"],
    "security": {"id": "10034"},
    "customfield_10014": "GCP-246",
    "customfield_10028": 3.0
  }
}
EOF
)"
```

### Create Epic Example

```bash
curl -s -X POST -u "$JIRA_USERNAME:$JIRA_PERSONAL_TOKEN" \
     -H "Content-Type: application/json" \
     -H "Accept: application/json" \
     "https://redhat.atlassian.net/rest/api/2/issue" \
     -d "$(cat <<'EOF'
{
  "fields": {
    "project": {"key": "GCP"},
    "issuetype": {"name": "Epic"},
    "summary": "Epic title here",
    "description": "h2. Use Case / Context\n\n...",
    "labels": ["ai-generated-jira"],
    "security": {"id": "10034"},
    "customfield_10011": "Epic title here"
  }
}
EOF
)"
```

## Template References

Read these files from the gcp-hcp repo before decomposing:
- If parent is Feature: `docs/jira-epic-template.md` (child template) + `docs/jira-feature-template.md` (parent context)
- If parent is Epic: `docs/jira-story-template.md` (child template) + `docs/jira-epic-template.md` (parent context)
- `docs/definition-of-done.md` -- Quality criteria for acceptance criteria writing
- `design-decisions/` -- Scan for decisions relevant to the feature domain
- `claude-plugin/gcp-hcp/skills/gcp-hcp-architecture/SKILL.md` -- Cross-repo map, architectural invariants
- `claude-plugin/gcp-hcp/skills/add-gcp-service-account/SKILL.md` -- Reference example of cross-repo decomposition

## Child Issue Creation Checklist

**Every Epic (created from Feature) MUST have:**
- [ ] Summary: [Action Verb] + [Specific Capability or Component]
- [ ] Description in Jira wiki markup following epic template (Use Case, Current/Desired State, Scope, Dependencies, AC)
- [ ] Epic Name (`customfield_10011`) — same value as summary
- [ ] Label: `ai-generated-jira`
- [ ] Security: `{"id": "10034"}`
- [ ] Link to parent Feature via issue link (Blocks or Related)

**Every Story (created from Epic) MUST have:**
- [ ] Summary: action-oriented title
- [ ] Description in Jira wiki markup with: User Story, Context, Requirements, Technical Approach, Dependencies, AC
- [ ] Story points (`customfield_10028`) as float (Fibonacci: 1, 2, 3, 5 -- split if 8+)
- [ ] Label: `ai-generated-jira`
- [ ] Security: `{"id": "10034"}`
- [ ] Epic Link (`customfield_10014`) set to parent Epic key
- [ ] Component if identifiable (mapped from cross-repo map)

## Label Swap Procedure

1. Post the structured completion comment FIRST (this is the idempotency marker)
2. Read current labels from the issue
3. Compute new labels: remove `agent:spec`, add result label
4. Update issue with the complete labels array (preserving all other labels)

## Idempotency

Before processing, check if a comment body starts with the exact string `[agent:spec:done]`
(line-anchored, not a substring match). If found, skip -- work was already completed.

## Wiki Markup Conventions

All descriptions and comments MUST use Jira wiki markup. **Never use Markdown.**

| Element | Wiki Markup | NOT |
|---------|------------|-----|
| Heading | `h2. Title` | `## Title` |
| Bullet | `* Item` | `- Item` |
| Bold | `*text*` | `**text**` |
| Code block | `{code}...{code}` | `` ``` `` |
| Table header | `|| Col 1 || Col 2 ||` | N/A |
| Table row | `| val 1 | val 2 |` | N/A |
| Link | `[text\|url]` | `[text](url)` |
