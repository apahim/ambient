# GCP HCP Weekly Status Rollup — 2026-04-10

## Summary
- Total active issues: 100
- Issues updated this week: 100
- Issues created this week: 31
- Issues resolved this week: 25

## Issues Created This Week
| Ticket | Summary | Status | Assignee |
|--------|---------|--------|----------|
| GCP-600 | Build nodepool adapter for NodePool lifecycle management on GCP | New | Chaitanya Kandagatla |
| GCP-599 | Build HyperFleet Adapter for HostedCluster lifecycle management | New | Chaitanya Kandagatla |
| GCP-598 | Zero Egress for GCP HCP Infrastructure | New | Unassigned |
| GCP-597 | Assess GSCC Adoption for GCP HCP Infrastructure | New | Unassigned |
| GCP-596 | Demo for broader org | New | Unassigned |
| GCP-595 | Assess AI Agent Orchestration System for SDLC | New | Unassigned |
| GCP-594 | Map AI-Assisted SDLC Process | New | Unassigned |
| GCP-593 | Implement audit trail for internal secret lifecycle events in GCP HCP | New | Chaitanya Kandagatla |
| GCP-592 | Define and implement signing key rotation for GCP HCP HostedClusters | New | Chaitanya Kandagatla |
| GCP-591 | Implement pull secret provisioning for GCP HCP HostedClusters | New | Chaitanya Kandagatla |
| GCP-590 | Implement signing key management for GCP WIF HostedCluster token signing | New | Chaitanya Kandagatla |
| GCP-589 | Provision a publicly accessible GCS-based OIDC issuer for GCP WIF token validation | New | Chaitanya Kandagatla |
| GCP-588 | Spike: Determine signing key strategy for GCP WIF (signing-key-adapter vs HO-native OIDC upload) | New | Chaitanya Kandagatla |
| GCP-587 | Automate Hypershift NS Record Delegation for Customer Ingress Zones | New | Patrick Martin |
| GCP-586 | Document "Normal" promotion proccess and "Fast" promotion proccess | New | Unassigned |
| GCP-585 | Upgrade HyperFleet components from v0.1.0 to v0.2.1 in gcp-hcp-infra | New | Chaitanya Kandagatla |
| GCP-584 | Enable Cloud SQL for HyperFleet API with Auth Proxy sidecar | New | Chaitanya Kandagatla |
| GCP-583 | Migrate CI scripts to WIF authentication and revoke static key | New | Unassigned |
| GCP-582 | Create WIF infrastructure for CI authentication | New | Unassigned |
| GCP-581 | Establish Security Foundations for GCP HCP Service | New | Unassigned |

## Issues Resolved This Week
| Ticket | Summary | Status | Assignee |
|--------|---------|--------|----------|
| GCP-478 | Spike: Develop an implementation-plan for  GcpHcp HyperFleet Adapters | Closed | Chaitanya Kandagatla |
| GCP-334 | [CLM] Components Deployment | Closed | Chaitanya Kandagatla |
| GCP-361 | Error handling and audit trail for CLM deployments | Closed | Unassigned |
| GCP-451 | GCP-300 stabilization and hardening | In Progress | Cristiano Veiga |
| GCP-462 | Create GCP hosted cluster documentation for HyperShift repository | Closed | Unassigned |
| GCP-242 | Manage databases used in GCP HCP  | Closed | Unassigned |
| GCP-218 | How to get images onto GCP HCP clusters | Closed | Unassigned |
| GCP-236 | On-cluster optional components for GCP HCP | Closed | Unassigned |
| GCP-384 | Investigate CI Service Account Key Rotation Strategy | Closed | Cristiano Veiga |
| GCP-86 | Deploy & Integrate New OpenShift Cluster Lifecycle Manager Backend | Closed | Unassigned |
| GCP-324 | Production Infrastructure Management - Root Cluster Provisioning | Closed | Patrick Martin |
| GCP-574 | Evaluate Atlantis → Terraform HCP Cloud migration | Closed | Patrick Martin |
| GCP-576 | Evaluate Tekton → Prow migration for e2e pipelines | Closed | Patrick Martin |
| GCP-575 | Evaluate Grafana → GCP Cloud Monitoring/Dashboards migration | Closed | Patrick Martin |
| GCP-180 | Regional Infrastructure Tooling and Automation | Closed | Patrick Martin |
| GCP-340 | GCP Hosted Control Plane Documentation in the Hypershift Repository | Closed | Cristiano Veiga |
| GCP-577 | Define progressive promotion strategy and validation gates | Closed | Patrick Martin |
| GCP-325 | SPIKE: Collaborate with APPSRE on HCM-wide infra tooling plans | Closed | Unassigned |
| GCP-578 | SPIKE: Evaluate compute platform for promotion automation | Closed | Patrick Martin |
| GCP-572 | Establish progressive promotion rollout for GCP HCP releases | Closed | Patrick Martin |

## Blockers & Stale Issues
Issues with no update in >14 days.

| Ticket | Summary | Days Since Update | Status | Assignee |
|--------|---------|-------------------|--------|----------|
| GCP-483 | Add etcd_server_quota_backend_bytes to HyperShift Telemetry MetricsSet | 23 | New | Unassigned |
| GCP-491 | Implement Slack PR daily digest for team repositories | 22 | New | Unassigned |
| GCP-476 | Determine if we want to create GCP HCP Team in Jira Cloud (using Teams functionality) | 20 | New | Kat Keane |
| GCP-168 | OpenShift PullSecret Generation/Management | 20 | To Do | Unassigned |
| GCP-381 | Slack workflow for Demo thread every sprint | 20 | New | Unassigned |
| GCP-139 | Control Plane Cost Estimation | 20 | To Do | Unassigned |
| GCP-414 | Documentation: Update guides and troubleshooting docs for ImageRegistry | 20 | New | Christoph Blecker |
| GCP-421 | Bump openshift-external-dns version in HyperShift and add DNSEndpoint CRD to rendered manifests | 20 | New | Patrick Martin |
| GCP-433 | cls-nodepool-controller does not recover from Pub/Sub IAM propagation delay | 20 | New | Unassigned |
| GCP-341 | SPIKE: Research and Design for Distributed Tracing Implementation | 20 | To Do | Amador Pahim Segundo |
| GCP-122 | Establish process to reliably sync our merged ADR/DDR docs to central HCM architecture repo  | 19 | New | Unassigned |
| GCP-204 | Support Private and Public Clusters | 19 | New | Unassigned |
| GCP-224 | Create AI code review agent rules for gcp-hcp-infra | 19 | New | Unassigned |
| GCP-225 | AI code review process documented and accepted | 19 | New | Unassigned |
| GCP-226 | AI test development best practices documentation | 19 | New | Unassigned |
| GCP-249 | Schedule a domain/tooling knowledge/AI practices learned session (or three) | 19 | New | Unassigned |
| GCP-305 | Audit MC workloads for missing resource requests/limits | 19 | New | Unassigned |
| GCP-342 | SPIKE: Research and Design for Structured Logging Implementation | 19 | New | Unassigned |
| GCP-412 | Unit Tests: Add comprehensive test coverage for ImageRegistry components | 19 | New | Christoph Blecker |
| GCP-413 | E2E Testing: Verify full image registry lifecycle on GCP | 19 | New | Christoph Blecker |
| GCP-503 | Implement OrphanDeleter Interface for GCP | 18 | New | Unassigned |
| GCP-504 | Add GCP NodePool Platform Conditions | 18 | New | Unassigned |
| GCP-505 | Implement Scale-from-Zero for GCP NodePools | 18 | New | Unassigned |
| GCP-506 | Implement GCP KMS Secret Encryption | 18 | New | Unassigned |
| GCP-507 | Integrate Infrastructure Cleanup into GCP Cluster Destroy | 18 | New | Unassigned |
| GCP-508 | Implement GCP Spot/Preemptible Node Termination Handler | 18 | New | Unassigned |
| GCP-510 | Implement GCP NodePool CLI Commands | 18 | New | Unassigned |
| GCP-426 | Bump vendored CAPG to serve v1beta2 CRDs | 17 | To Do | Unassigned |
| GCP-509 | Add GCP E2E Test Coverage | 17 | New | Unassigned |
| GCP-486 | Submit graduation PR for gcp-hcp-cli | 17 | To Do | Unassigned |

## Component Distribution
| Component | Open | In Progress | Done |
|-----------|------|-------------|------|
| No Component | 71 | 0 | 0 |
| Retrospective action items | 1 | 0 | 0 |
| gcp-hcp-automation | 23 | 0 | 0 |
| hypershift-operator-gcp | 5 | 0 | 0 |

## Status Distribution
| Status | Count |
|--------|-------|
| New | 100 |
