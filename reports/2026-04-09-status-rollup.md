# GCP HCP Weekly Status Rollup — 2026-04-09

## Summary
- Total active issues: 186
- Issues updated this week: 130
- Issues created this week: 32
- Issues resolved this week: 24

## Status Changes This Week
_Note: Jira Cloud API v3 does not provide easy access to historical status transitions. This section would require changelog queries for each issue, which is rate-limited. Recommend using Jira automation or webhooks for real-time status change tracking._

## Blockers
Issues with status "Blocked" or flagged, or with no update in >14 days.

| Ticket | Summary | Days Since Update | Assignee |
|--------|---------|-------------------|----------|
| GCP-510 | Implement GCP NodePool CLI Commands | 17 | Unassigned |
| GCP-509 | Add GCP E2E Test Coverage | 17 | Unassigned |
| GCP-508 | Implement GCP Spot/Preemptible Node Termination Handler | 17 | Unassigned |
| GCP-507 | Integrate Infrastructure Cleanup into GCP Cluster Destroy | 17 | Unassigned |
| GCP-506 | Implement GCP KMS Secret Encryption | 17 | Unassigned |
| GCP-505 | Implement Scale-from-Zero for GCP NodePools | 17 | Unassigned |
| GCP-504 | Add GCP NodePool Platform Conditions | 17 | Unassigned |
| GCP-503 | Implement OrphanDeleter Interface for GCP | 17 | Unassigned |
| GCP-491 | Implement Slack PR daily digest for team repositories | 22 | Unassigned |
| GCP-487 | Create gcp-hcp-cli repository under openshift-online | 15 | Unassigned |
| GCP-486 | Submit graduation PR for gcp-hcp-cli | 16 | Unassigned |
| GCP-483 | Add etcd_server_quota_backend_bytes to HyperShift Telemetry MetricsSet | 23 | Unassigned |
| GCP-476 | Determine if we want to create GCP HCP Team in Jira Cloud (using Teams functionality) | 20 | Kat Keane |
| GCP-465 | Swap out Jira MCP server to interact with Jira Cloud | 14 | Christoph Blecker |
| GCP-460 | Configure PagerDuty team, service, and escalation policy | 14 | Jim DAgostino |
| GCP-433 | cls-nodepool-controller does not recover from Pub/Sub IAM propagation delay | 19 | Unassigned |
| GCP-431 | HyperShift: Add CNCC support for GCP Workload Identity Federation | 14 | Amador Pahim Segundo |
| GCP-430 | CNO: Wire GCP WIF credentials for CNCC in HyperShift HCP mode | 14 | Amador Pahim Segundo |
| GCP-426 | Bump vendored CAPG to serve v1beta2 CRDs | 17 | Unassigned |
| GCP-421 | Bump openshift-external-dns version in HyperShift and add DNSEndpoint CRD to rendered manifests | 19 | Patrick Martin |

## Component Distribution
| Component | To Do | In Progress | Done |
|-----------|-------|-------------|------|
| No Component | 67 | 6 | 0 |
| gcp-hcp-automation | 20 | 1 | 0 |
| Retrospective action items | 1 | 1 | 0 |

_Note: Only showing active (non-Done/Closed) issues._

## Epics Progress
| Epic | Total Stories | Done | In Progress | To Do | % Complete |
|------|---------------|------|-------------|-------|------------|
| GCP-587: Automate Hypershift NS Record Delegation for Customer Ingress Zones | 2 | 1 | 0 | 1 | 50% |
| GCP-573: Mature infrastructure tooling and resolve tech-debt from M2 | 3 | 0 | 0 | 3 | 0% |
| GCP-572: Establish progressive promotion rollout for GCP HCP releases | 2 | 2 | 0 | 0 | 100% |
| GCP-562: Adopt Cincinnati for cluster version resolution and upgrades | 4 | 0 | 3 | 1 | 0% |
| GCP-549: Migrate gcp-hcp-infra E2E Pipeline from Tekton to Prow | 12 | 0 | 0 | 12 | 0% |
| GCP-544: Migrate dashboarding from Grafana to GCP Cloud Monitoring | 4 | 0 | 0 | 4 | 0% |
| GCP-537: Implement Progressive Rollout Framework for Cross-Environment and Cross-Region Change Propagation | 8 | 0 | 0 | 8 | 0% |
| GCP-532: Terraform Cloud Migration | 4 | 0 | 0 | 4 | 0% |
| GCP-524: Image Management | 11 | 0 | 0 | 11 | 0% |
| GCP-502: Close CAPG Implementation Gaps for GCP Platform Parity in HyperShift | 9 | 0 | 0 | 9 | 0% |
| GCP-451: GCP-300 stabilization and hardening | 3 | 1 | 0 | 2 | 33% |
| GCP-392: Cost Visibility and Management for GCP HCP | 1 | 1 | 0 | 0 | 100% |
| GCP-388: Eliminate Cross-Cluster Network Dependencies | 3 | 3 | 0 | 0 | 100% |
| GCP-340: GCP Hosted Control Plane Documentation in the Hypershift Repository | 1 | 1 | 0 | 0 | 100% |
| GCP-337: [CLM] Core Cluster Lifecycle Adapters | 6 | 1 | 1 | 4 | 17% |
| GCP-336: [CLM] Internal Secrets Management | 6 | 0 | 0 | 6 | 0% |
| GCP-335: Synthetic Monitoring & Availability Tracking | 1 | 0 | 0 | 1 | 0% |
| GCP-334: [CLM] Components Deployment | 5 | 5 | 0 | 0 | 100% |
| GCP-330: Deployment Tooling Strategy and Configuration Management | 2 | 2 | 0 | 0 | 100% |
| GCP-328: Tooling Access Evaluation | 4 | 4 | 0 | 0 | 100% |
| GCP-326: Production Secret Storage Strategy | 1 | 0 | 0 | 1 | 0% |
| GCP-324: Production Infrastructure Management - Root Cluster Provisioning | 1 | 1 | 0 | 0 | 100% |
| GCP-322: Enable Storage Operator (CSI) for GCP Hosted Control Planes | 4 | 3 | 0 | 1 | 75% |
| GCP-320: Automated Remediation Platform Scaffolding | 21 | 21 | 0 | 0 | 100% |
| GCP-319: Integrated Alerting Framework | 6 | 5 | 0 | 1 | 83% |
| GCP-318: Golden Signal Metrics & Operational Dashboards | 6 | 4 | 2 | 0 | 67% |
| GCP-317: Standardized Structured Logging | 1 | 0 | 0 | 1 | 0% |
| GCP-316: Distributed Tracing & Transaction Definition | 1 | 0 | 0 | 1 | 0% |
| GCP-315: Enable Image Registry Operator for GCP Hosted Control Planes | 11 | 6 | 1 | 4 | 55% |
| GCP-314: GCP Ingress Support for HyperShift Hosted Clusters | 1 | 0 | 0 | 1 | 0% |
| GCP-311: Implement GCP Cloud Controller Manager for LoadBalancer and Node Management | 5 | 4 | 1 | 0 | 80% |
| GCP-304: Audit and set resource requests/limits for all Management Cluster components | 1 | 0 | 0 | 1 | 0% |
| GCP-303: Add GCP support to remaining OCP components needed for GCP HCP service | 1 | 0 | 0 | 1 | 0% |
| GCP-282: Cloud Network Config Controller: GCP Workload Identity Federation | 3 | 1 | 2 | 0 | 33% |
| GCP-255: GCP-HCP CLI, CLS Backend, CLS Controller Pilot demo readiness | 15 | 15 | 0 | 0 | 100% |
| GCP-254: GCP E2E Tests Configuration in the HyperShift Repository | 20 | 15 | 0 | 5 | 75% |
| GCP-242: Manage databases used in GCP HCP  | 1 | 0 | 1 | 0 | 0% |
| GCP-212: Add GCP Platform Support for HyperShift NodePools | 2 | 2 | 0 | 0 | 100% |
| GCP-203: Measure & Refine Agentic Adoption | 1 | 1 | 0 | 0 | 100% |
| GCP-202: Develop Shared Agentic Assets for Team Scalability | 3 | 2 | 1 | 0 | 67% |
| GCP-201: Optimize E2E Test Suite with Agentic Tooling | 2 | 1 | 0 | 1 | 50% |
| GCP-200: Establish AI-Assisted Review Workflow | 4 | 2 | 0 | 2 | 50% |
| GCP-184: GCP / Red Hat account linking | 1 | 0 | 0 | 1 | 0% |
| GCP-180: Regional Infrastructure Tooling and Automation | 24 | 23 | 0 | 1 | 96% |
| GCP-92: Management Cluster Lifecycle | 1 | 1 | 0 | 0 | 100% |
| GCP-91: HCP GCP - Observability | 2 | 0 | 0 | 2 | 0% |
| GCP-90: HCP GCP - e2e test framework | 2 | 2 | 0 | 0 | 100% |
| GCP-89: [M1] HCP GCP - Region Creation Tooling / Automation | 23 | 23 | 0 | 0 | 100% |
| GCP-87: GCP API Gateway Customer-Facing Frontend Service | 4 | 4 | 0 | 0 | 100% |
| GCP-86: Deploy & Integrate New OpenShift Cluster Lifecycle Manager Backend | 2 | 2 | 0 | 0 | 100% |
| GCP-85: GCP HCP Component deployment framework | 1 | 1 | 0 | 0 | 100% |
| GCP-84: [HO] - Hosted Cluster Deployment / Configuration | 8 | 8 | 0 | 0 | 100% |
| GCP-82: [HO] - GCP-HCP Production Readiness | 1 | 1 | 0 | 0 | 100% |
| GCP-81: [HO] PSC Infrastructure for GCP HCP | 15 | 15 | 0 | 0 | 100% |
| GCP-79: [HO] - GCP Platform foundation for HyperShift | 11 | 11 | 0 | 0 | 100% |

---

_Report generated by Ambient workflow on 2026-04-09_
_Jira instance: https://redhat.atlassian.net | Project: GCP_
