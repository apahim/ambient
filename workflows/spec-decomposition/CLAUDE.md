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
- All created issues MUST have label `ai-generated-jira` and security `{"name": "Red Hat Employee"}`
- Use Jira wiki markup (`h2.`, `*`, `{code}`), NOT markdown (`##`, `-`, `` ``` ``)

## Jira MCP Tools

Jira access is provided by the platform's `mcp-atlassian` MCP server (connected
via the Ambient Jira integration). The tools are deferred and must be loaded
explicitly before use.

**MANDATORY first step** -- load the Jira tools by running:

```
ToolSearch("select:mcp__mcp-atlassian__jira_search,mcp__mcp-atlassian__jira_get_issue,mcp__mcp-atlassian__jira_create_issue,mcp__mcp-atlassian__jira_update_issue,mcp__mcp-atlassian__jira_add_comment,mcp__mcp-atlassian__jira_create_issue_link,mcp__mcp-atlassian__jira_get_link_types")
```

If the select query returns no matches, try a broader search:

```
ToolSearch("+mcp-atlassian", 20)
```

Do NOT search for tools using generic keywords like "jira" -- that will not find
MCP tools. Do NOT write Python scripts or curl commands to access the Jira API.
Do NOT ask the user to configure credentials. The tools are provided by the
platform integration.

## Jira Configuration

- **Instance**: https://issues.redhat.com (Cloud: redhat.atlassian.net)
- **Project key**: GCP
- **Contact**: asegundo@redhat.com

### Custom Fields

| Field | ID | Type |
|-------|----|------|
| Story Points | `customfield_12310243` | float |
| Epic Link | `customfield_12311140` | string (Epic key) |
| Epic Name | `customfield_12311141` | string |
| Parent Link | `customfield_12313140` | string (parent key) |

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
- [ ] Epic Name (`customfield_12311141`)
- [ ] Label: `ai-generated-jira`
- [ ] Security: `{"name": "Red Hat Employee"}`
- [ ] Parent Link to Feature (`customfield_12313140`)

**Every Story (created from Epic) MUST have:**
- [ ] Summary: action-oriented title
- [ ] Description in Jira wiki markup with: User Story, Context, Requirements, Technical Approach, Dependencies, AC
- [ ] Story points (Fibonacci: 1, 2, 3, 5 -- split if 8+)
- [ ] Label: `ai-generated-jira`
- [ ] Security: `{"name": "Red Hat Employee"}`
- [ ] Epic Link to parent Epic (`customfield_12311140`)
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
