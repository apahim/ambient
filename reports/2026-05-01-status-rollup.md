# GCP HCP Weekly Status Rollup — 2026-05-01

## Summary
- Total active issues: 50+
- Issues updated this week: 50+
- Issues created this week: 13
- Issues resolved this week: 13

## Key Highlights This Week

### Security Focus
A major security audit was completed, resulting in the creation of **Epic GCP-645: Security Audit Remediation** with 10 child stories covering:
- Secrets management improvements (embedded keys, Terraform outputs)
- Infrastructure hardening (securityContext, IAM least privilege)
- CI/CD security (binary checksum verification)
- Component security (diagnose agent, cluster-admin roles)

### Progressive Rollout Completion
The progressive rollout framework epic was successfully completed this week with 6 stories closed:
- GCP-538: Design rollout model
- GCP-540: E2E health check suite
- GCP-541: ArgoCD promotion pipeline
- GCP-542: Terraform promotion pipeline
- GCP-543: End-to-end validation
- GCP-586: Promotion process documentation

### Disaster Recovery Planning
New epic **GCP-642: DR Assessment and Architecture Decision** was created with initial spike work for Velero/OADP deployment.

## Status Changes This Week

| Ticket | Summary | Previous Status | Current Status | Assignee |
|--------|---------|-----------------|----------------|----------|
| GCP-633 | Create Definition of Ready documentation | In Progress | Closed | Unassigned |
| GCP-631 | Document DoD and DoR for AI-assisted SDLC | In Progress | Closed | Unassigned |
| GCP-586 | Document "Normal", "Fast", and "Freeze" promotion processes | In Progress | Closed | Unassigned |
| GCP-543 | End-to-end validation: demo gating tests and full pipeline dry run | In Progress | Closed | Patrick Martin |
| GCP-542 | Implement promotion pipeline for Terraform-based changes | In Progress | Closed | Patrick Martin |
| GCP-541 | Implement promotion pipeline for ArgoCD-based changes | In Progress | Closed | Patrick Martin |
| GCP-540 | Implement platform E2E health check suite | In Progress | Closed | Patrick Martin |
| GCP-538 | Design rollout model: sector metadata, rollout ordering, gates | In Progress | Closed | Patrick Martin |
| GCP-521 | Backlog spring cleaning | In Progress | Closed | Kat Keane |
| GCP-460 | Configure PagerDuty team, service, and escalation policy | In Progress | Closed | Jim DAgostino |
| GCP-431 | HyperShift: Add CNCC support for GCP Workload Identity Federation | In Progress | Closed | Amador Pahim Segundo |
| GCP-430 | CNO: Wire GCP WIF credentials for CNCC in HyperShift HCP mode | In Progress | Closed | Amador Pahim Segundo |
| GCP-319 | Integrated Alerting Framework | In Progress | Closed | Jim DAgostino |

## Blockers

Issues with no update in >14 days (excluding Done/Closed/Resolved):

| Ticket | Summary | Days Since Update | Assignee |
|--------|---------|-------------------|----------|
| GCP-620 | Update GCP-523 with new workflow plan | 15+ | Jim DAgostino |
| GCP-619 | Document components that make use of Go Crypto, SSL, or PyCrypto | 16+ | Bill Montgomery |
| GCP-618 | Document any uses of SSH that are in use today | 14+ | Bill Montgomery |
| GCP-617 | GCP HCP - PQC for Q1 | 16+ | Bill Montgomery |
| GCP-616 | Create Ambient Workflow for Backlog Health and Epic Planning | 16+ | Unassigned |
| GCP-615 | Document Service vs OCP Component Vulnerability Boundaries | 16+ | Unassigned |
| GCP-614 | Define Vulnerability Response Process and SLAs | 16+ | Unassigned |
| GCP-613 | Implement Runtime Vulnerability Scanning with ACS | 16+ | Unassigned |
| GCP-611 | Integrate Dependency Scanning into Build Pipelines | 16+ | Unassigned |
| GCP-609 | Evaluate ACS for GCP HCP Vulnerability Scanning | 16+ | Unassigned |
| GCP-608 | Hosted Cluster Upgrade Lifecycle | 15+ | Unassigned |
| GCP-607 | Create Jira Task Template for internal work standardization | 15+ | Kat Keane |
| GCP-600 | Build nodepool adapter for NodePool lifecycle management on GCP | 21+ | Chaitanya Kandagatla |
| GCP-599 | Build HyperFleet Adapter for HostedCluster lifecycle management | 15+ | Chaitanya Kandagatla |

## Component Distribution

Most issues do not have components assigned. Of the active issues with components:

| Component | Open | In Progress | Done |
|-----------|------|-------------|------|
| gcp-hcp-infra | 1 | 0 | 0 |
| Retrospective action items | 1 | 0 | 0 |
| (No component) | 48+ | 10+ | 13 |

## Epics Progress

| Epic | Summary | Status | Stories Completed This Week |
|------|---------|--------|----------------------------|
| GCP-645 | Security Audit Remediation (2026-04-29) | New | 0 (10 new stories created) |
| GCP-642 | DR Assessment and Architecture Decision | New | 0 (newly created) |
| GCP-631 | Document DoD and DoR for AI-assisted SDLC | Closed | Epic completed |
| GCP-627 | [CLM] Customer Facing API/CLI | New | 0 |
| GCP-623 | [CLM] Adapters Tech Debt | New | 0 |
| GCP-617 | GCP HCP - PQC for Q1 | New | 0 |
| GCP-598 | Zero Egress for GCP HCP Infrastructure | New | 0 |
| GCP-597 | Assess GSCC Adoption for GCP HCP Infrastructure | New | 0 |
| GCP-596 | Demo for broader org | New | 0 |
| GCP-595 | Assess AI Agent Orchestration System for SDLC | New | 0 |
| GCP-594 | Map AI-Assisted SDLC Process | New | 0 |
| GCP-587 | Automate Hypershift NS Record Delegation | In Progress | 0 |
| GCP-573 | Mature infrastructure tooling and resolve tech-debt from M2 | New | 0 |
| GCP-572 | Establish progressive promotion rollout | Closed | 6 stories (epic completed) |
| GCP-549 | Migrate gcp-hcp-infra E2E Pipeline from Tekton to Prow | New | 0 |
| GCP-319 | Integrated Alerting Framework | Closed | Epic completed |

## Active Work This Week

### In Progress
- **GCP-643**: Bump Go version in e2e pipeline to 1.25.7 (Patrick Martin)
- **GCP-636**: Hypershift operator: upload OIDC discovery documents to GCS (Chaitanya Kandagatla)
- **GCP-630**: Operationalize Agentic SDLC for GCP HCP (Christoph Blecker)
- **GCP-621**: Determine process to request GCP org policy constraint exceptions (Christoph Blecker)
- **GCP-524**: Konflux Builds and AR Pull-Through Cache for Infrastructure Images (In Progress)
- **GCP-527**: Spike: Konflux Build Pipeline Setup (In Progress)

### In Review
- **GCP-635**: Make JWKS file optional in hypershift CLI when OIDC issuer URL is provided (Chaitanya Kandagatla)
- **GCP-619**: Document components that make use of Go Crypto, SSL, or PyCrypto (Bill Montgomery)
- **GCP-618**: Document any uses of SSH that are in use today (Bill Montgomery)
- **GCP-599**: Build HyperFleet Adapter for HostedCluster lifecycle management (Chaitanya Kandagatla)
- **GCP-588**: Spike: Determine signing key strategy for GCP WIF (Review)

## Recommendations

1. **Security Epic GCP-645**: Prioritize triaging and assigning the 10 security remediation stories from the recent audit
2. **Stale Issues**: Review and update the 14 issues with no activity in >14 days, particularly around vulnerability scanning and ACS evaluation
3. **Component Tagging**: Consider adding component labels to issues to improve tracking and distribution visibility
4. **Epic Planning**: Several new epics (GCP-595, GCP-594, GCP-596) around AI-assisted SDLC need story decomposition
5. **DR Planning**: Epic GCP-642 needs story breakdown and planning for disaster recovery implementation
