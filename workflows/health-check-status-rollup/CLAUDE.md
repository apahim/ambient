# Health Check Status Rollup — Agent Context

## Purpose

You are running a **Stage 1 (Read-Only) Architecture Health Check** for the GCP HCP project, specifically **Activity 9: Communication & Alignment** from the architecture workflow.

Your job: generate a weekly status rollup report from Jira and save it to this repo.

## Available Repositories

Your workspace has two repos cloned:

| Repo | Path | Access | Purpose |
|------|------|--------|---------|
| **ambient** | Working directory | Read-write | Save reports here |
| **gcp-hcp** | Sibling directory | **Read-only** | Architecture decisions, implementation plans, skills, team conventions. Contains `CLAUDE.md`, `.claude/settings.json`, and the upstream Jira plugin configuration. |

The gcp-hcp repo provides context for interpreting Jira data (e.g., mapping tickets to design decisions or implementation plans). Use it as reference but do NOT modify it.

## Constraints

- **Read-only**: You MUST NOT create, modify, transition, or close any Jira tickets.
- **No external repo changes**: You MUST NOT push changes to any repo other than this one.
- **No secrets in output**: Do not include API tokens, keys, or credentials in reports.

## Jira Configuration

- **Jira instance**: https://issues.redhat.com (Cloud: redhat.atlassian.net)
- **Project key**: GCP
- **Contact**: asegundo@redhat.com

### Custom Fields

| Field | ID |
|-------|----|
| Story Points | `customfield_12310243` (float) |
| Epic Link | `customfield_12311140` |
| Epic Name | `customfield_12311141` |
| Parent Link | `customfield_12313140` |

## Report Format

Save the report to `reports/YYYY-MM-DD-status-rollup.md` using today's date.

The report must include these sections:

```markdown
# GCP HCP Weekly Status Rollup — YYYY-MM-DD

## Summary
- Total active issues: N
- Issues updated this week: N
- Issues created this week: N
- Issues resolved this week: N

## Status Changes This Week
| Ticket | Summary | Previous Status | Current Status | Assignee |
|--------|---------|-----------------|----------------|----------|

## Blockers
Issues with status "Blocked" or flagged, or with no update in >14 days.

| Ticket | Summary | Days Since Update | Assignee |
|--------|---------|-------------------|----------|

## Component Distribution
| Component | Open | In Progress | Done |
|-----------|------|-------------|------|

## Epics Progress
| Epic | Total Stories | Done | In Progress | To Do | % Complete |
|------|-------------|------|-------------|-------|------------|
```

## How to Generate

1. Invoke the `jira:status-rollup` skill for the GCP project with a 7-day window.
2. If the skill produces raw data, format it into the report template above.
3. For stale items, query issues with `updated <= -14d AND status != Done AND status != Closed`.
4. Save the report file.

## Success Criteria

Per Activity 9 success metrics:
- All ticket status changes reflected in the report
- No stale data (report matches current Jira state)
- Report published (file saved to reports/ directory)
