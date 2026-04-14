# GCP HCP Ambient Workflows

Agentic workflow definitions for the GCP HCP architecture lifecycle, designed for the [Ambient Code Platform](https://github.com/ambient-code) (ACP)

## Relationship to gcp-hcp

This repo contains **workflow definitions and scheduled session configurations** that automate architecture activities defined in [gcp-hcp/docs/architecture-workflow.md](https://github.com/apahim/gcp-hcp/blob/main/docs/architecture-workflow.md). The gcp-hcp repo owns the architecture decisions, implementation plans, and skills. This repo owns the orchestration layer.

## Structure

```
workflows/                          # ACP workflow definitions (git-consumed)
  health-check-status-rollup/       # Stage 1: Weekly Jira status rollup (Activity 9)
    .ambient/ambient.json           # Workflow metadata, prompts, result artifacts
    .claude/settings.json           # Tool permissions and plugin config
    CLAUDE.md                       # Agent context and constraints

scheduled-sessions/                 # ScheduledSession API payloads (reference)
  weekly-status-rollup.json         # Friday 14:00 UTC cron definition

reports/                            # Auto-generated reports (committed by agent sessions)
  YYYY-MM-DD-status-rollup.md       # Weekly status rollup output
```

## Workflows

| Workflow | Stage | Activity | Schedule | Status |
|----------|-------|----------|----------|--------|
| `health-check-status-rollup` | 1 (Read-Only) | 9 (Communication & Alignment) | Friday 14:00 UTC | Active |

## Usage

### Manual test (local)

```bash
cd /path/to/ambient
claude --workflow workflows/health-check-status-rollup
```

### Deploy as ScheduledSession (ACP)

```bash
# Submit the session definition to ACP API
curl -X POST https://<acp-api>/api/v1/scheduled-sessions \
  -H "Authorization: Bearer $(cat .ambient.key)" \
  -H "Content-Type: application/json" \
  -d @scheduled-sessions/weekly-status-rollup.json
```

## Security

- `.ambient.key` is gitignored and must never be committed
- Jira credentials are injected via environment variables at session creation time, not stored in git
- All Stage 1 workflows are **read-only** — they query but never modify Jira or external repos
