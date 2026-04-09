# GCP HCP Weekly Status Rollup — 2026-04-09

## Summary
- **Total active issues**: 100
- **Issues updated this week**: 100
- **Issues created this week**: 36
- **Issues resolved this week**: 23

## Recent Activity Highlights

### Newly Created Issues (Last 7 Days)
The team created 36 new issues this week, with significant focus on:
- NodePool and HostedCluster adapter implementation
- Security improvements (zero egress, security command center, secret management)
- AI-assisted SDLC process mapping and assessment

| Ticket | Summary | Status | Created |
|--------|---------|--------|---------|
| GCP-600 | Implement nodepool adapter for NodePool lifecycle management on GCP | New | 2026-04-09 |
| GCP-599 | Implement hostedcluster adapter for cluster lifecycle | New | 2026-04-09 |
| GCP-598 | Zero Egress for GCP HCP Infrastructure | New | 2026-04-09 |
| GCP-597 | GCP Security Command Center Adoption | New | 2026-04-09 |
| GCP-596 | Demo for broader org | New | 2026-04-09 |
| GCP-595 | Assess AI Agent Orchestration System for SDLC | New | 2026-04-09 |
| GCP-594 | Map AI-Assisted SDLC Process | New | 2026-04-09 |
| GCP-593 | Implement audit trail for internal secret lifecycle events in GCP HCP | New | 2026-04-09 |
| GCP-592 | Define and implement signing key rotation for GCP HCP HostedClusters | New | 2026-04-09 |
| GCP-591 | Implement pull secret provisioning for GCP HCP HostedClusters | New | 2026-04-09 |

### Recently Resolved Issues (Last 7 Days)
23 issues were resolved this week, including:

| Ticket | Summary | Resolution | 
|--------|---------|-----------|
| GCP-180 | Regional Infrastructure Tooling and Automation | Done |
| GCP-340 | GCP Hosted Control Plane Documentation in the Hypershift Repository | Done |
| GCP-242 | Manage databases used in GCP HCP | Duplicate |
| GCP-218 | How to get images onto GCP HCP clusters | Duplicate |
| GCP-574 | Evaluate Atlantis → Terraform HCP Cloud migration | Duplicate |
| GCP-576 | Evaluate Tekton → Prow migration for e2e pipelines | Duplicate |
| GCP-575 | Evaluate Grafana → GCP Cloud Monitoring/Dashboards migration | Duplicate |
| GCP-236 | On-cluster optional components for GCP HCP | Obsolete |
| GCP-384 | Investigate CI Service Account Key Rotation Strategy | Obsolete |
| GCP-324 | Production Infrastructure Management - Root Cluster Provisioning | Won't Do |

## Status Distribution

Current status distribution of all 100 active issues:

| Status | Count | Percentage |
|--------|-------|------------|
| New | 64 | 64% |
| In Progress | 26 | 26% |
| To Do | 6 | 6% |
| Refinement | 3 | 3% |
| Review | 1 | 1% |

## Blockers and Stale Issues

**40 issues** have not been updated in more than 14 days and are not resolved. These require attention:

| Ticket | Summary | Days Since Update | Assignee |
|--------|---------|-------------------|----------|
| GCP-483 | Add etcd_server_quota_backend_bytes to HyperShift Telemetry MetricsSet | 23 | Unassigned |
| GCP-491 | Implement Slack PR daily digest for team repositories | 22 | Unassigned |
| GCP-476 | Determine if we want to create GCP HCP Team in Jira Cloud (using Teams functionality) | 20 | Kat Keane |
| GCP-168 | OpenShift PullSecret Generation/Management | 19 | Unassigned |
| GCP-381 | Slack workflow for Demo thread every sprint | 19 | Unassigned |
| GCP-139 | Control Plane Cost Estimation | 19 | Unassigned |
| GCP-414 | Documentation: Update guides and troubleshooting docs for ImageRegistry | 19 | Christoph Blecker |
| GCP-421 | Bump openshift-external-dns version in HyperShift and add DNSEndpoint CRD to rendered manifests | 19 | Patrick Martin |
| GCP-433 | cls-nodepool-controller does not recover from Pub/Sub IAM propagation delay | 19 | Unassigned |
| GCP-341 | SPIKE: Research and Design for Distributed Tracing Implementation | 19 | Amador Pahim Segundo |
| GCP-122 | Establish process to reliably sync our merged ADR/DDR docs to central HCM architecture repo | 18 | Unassigned |
| GCP-204 | Support Private and Public Clusters | 18 | Unassigned |
| GCP-224 | Create AI code review agent rules for gcp-hcp-infra | 18 | Unassigned |
| GCP-225 | AI code review process documented and accepted | 18 | Unassigned |
| GCP-226 | AI test development best practices documentation | 18 | Unassigned |
| GCP-249 | Schedule a domain/tooling knowledge/AI practices learned session (or three) | 18 | Unassigned |
| GCP-305 | Audit MC workloads for missing resource requests/limits | 18 | Unassigned |
| GCP-342 | SPIKE: Research and Design for Structured Logging Implementation | 18 | Unassigned |
| GCP-361 | Error handling and audit trail for CLM deployments | 18 | Unassigned |
| GCP-412 | Unit Tests: Add comprehensive test coverage for ImageRegistry components | 18 | Christoph Blecker |
| GCP-413 | E2E Testing: Verify full image registry lifecycle on GCP | 18 | Christoph Blecker |
| GCP-503 | Implement OrphanDeleter Interface for GCP | 17 | Unassigned |
| GCP-504 | Add GCP NodePool Platform Conditions | 17 | Unassigned |
| GCP-505 | Implement Scale-from-Zero for GCP NodePools | 17 | Unassigned |
| GCP-506 | Implement GCP KMS Secret Encryption | 17 | Unassigned |
| GCP-507 | Integrate Infrastructure Cleanup into GCP Cluster Destroy | 17 | Unassigned |
| GCP-508 | Implement GCP Spot/Preemptible Node Termination Handler | 17 | Unassigned |
| GCP-510 | Implement GCP NodePool CLI Commands | 17 | Unassigned |
| GCP-426 | Bump vendored CAPG to serve v1beta2 CRDs | 17 | Unassigned |
| GCP-509 | Add GCP E2E Test Coverage | 17 | Unassigned |
| GCP-486 | Submit graduation PR for gcp-hcp-cli | 16 | Unassigned |
| GCP-487 | Create gcp-hcp-cli repository under openshift-online | 15 | Unassigned |
| GCP-416 | Investigate IngressController Configuration for GCP Hosted Clusters | 15 | Unassigned |
| GCP-460 | Configure PagerDuty team, service, and escalation policy | 14 | Jim DAgostino |
| GCP-368 | Add E2E test for GCP Cloud Controller Manager | 14 | Cristiano Veiga |
| GCP-465 | Swap out Jira MCP server to interact with Jira Cloud | 14 | Christoph Blecker |
| GCP-410 | HCCO: Implement GCP credential propagation package and ImageRegistry secret | 14 | Christoph Blecker |
| GCP-430 | CNO: Wire GCP WIF credentials for CNCC in HyperShift HCP mode | 14 | Amador Pahim Segundo |
| GCP-431 | HyperShift: Add CNCC support for GCP Workload Identity Federation | 14 | Amador Pahim Segundo |
| GCP-299 | Spike: Audit Ancillary OCP Components for GCP Compatibility | 14 | Unassigned |

### Key Concerns
- **High unassigned count**: 27 of the 40 stale issues (67.5%) are unassigned
- **Long stale duration**: Several issues have been stale for 3+ weeks
- **Critical areas affected**: Testing (E2E), documentation, security, and infrastructure cleanup

## Component Distribution

Distribution of active issues across components:

| Component | Count |
|-----------|-------|
| No Component | 83 |
| hypershift-operator-gcp | 10 |
| gcp-hcp-automation | 7 |

**Note**: 83% of issues have no component assigned, suggesting an opportunity to improve issue categorization.

## Week-over-Week Trends

### Positive Trends
- ✅ Strong resolution activity: 23 issues resolved this week
- ✅ Active development: 100 issues updated in the past 7 days
- ✅ High creation rate: 36 new issues created, indicating active planning and discovery

### Areas for Attention
- ⚠️ Large backlog of unassigned issues in the "New" status (64 issues)
- ⚠️ 40 stale issues requiring review and prioritization
- ⚠️ Component assignment needs improvement (83% without components)
- ⚠️ Many documentation and testing tasks in the stale backlog

## Recommendations

1. **Address stale issues**: Review and triage the 40 issues stale for >14 days
2. **Assignment review**: Focus on assigning the 27 unassigned stale issues
3. **Component tagging**: Improve component assignment for better tracking
4. **Backlog grooming**: Address the 64 issues in "New" status to move them to active work or backlog

---

*Report generated on 2026-04-09 by GCP HCP Weekly Status Rollup workflow*
*Data source: Jira project GCP (https://redhat.atlassian.net)*
