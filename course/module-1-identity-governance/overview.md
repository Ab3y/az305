# Module 1: Identity, Governance & Monitoring (25-30%)

**Theme: "Identity is the Control Plane — Everything Else Follows"**

---

## Why This Module Comes First

Identity and governance form the foundation of every Azure deployment. You cannot design secure compute, storage, or networking without first understanding authentication, authorization, and organizational hierarchy. This module establishes the mental model for all subsequent design decisions.

---

## Learning Objectives

After completing this module, you will be able to:

- Design a logging and monitoring solution using Azure Monitor, Log Analytics, and Application Insights
- Recommend authentication solutions for cloud, hybrid, and external identity scenarios
- Design authorization strategies using RBAC, managed identities, and Key Vault
- Create a governance hierarchy with management groups, policies, and compliance controls
- Apply identity governance patterns including PIM and access reviews

---

## Lessons

| # | Lesson | Duration | Focus |
|---|--------|----------|-------|
| 1 | [Logging and Monitoring](lesson-1-logging-monitoring.md) | 60 min | Log Analytics, Azure Monitor, Application Insights, routing logs |
| 2 | [Authentication and Authorization](lesson-2-auth.md) | 75 min | Entra ID, B2B/B2C, RBAC, managed identity, Key Vault |
| 3 | [Governance](lesson-3-governance.md) | 60 min | Management groups, Azure Policy, PIM, compliance |

---

## Hands-On Labs

| # | Lab | Bicep Template | Estimated Time |
|---|-----|---------------|----------------|
| 1 | Deploy Log Analytics workspace with data collection rules | [log-analytics-workspace.bicep](../../infra/log-analytics-workspace.bicep) | 20 min |
| 2 | Create custom RBAC role and assign to managed identity | [custom-rbac-role.bicep](../../infra/custom-rbac-role.bicep) | 15 min |
| 3 | Deploy Key Vault with Private Link and managed identity access | [keyvault-with-private-link.bicep](../../infra/keyvault-with-private-link.bicep) | 20 min |
| 4 | Deploy Azure Policy initiative for compliance | [azure-policy-initiative.bicep](../../infra/azure-policy-initiative.bicep) | 15 min |

### Supporting Scripts
- [Configure diagnostic settings](../../scripts/az-cli/configure-diagnostic-settings.sh) (Azure CLI)
- [Create RBAC assignments](../../scripts/az-cli/create-rbac-assignments.sh) (Azure CLI)
- [Identity & governance examples](../../scripts/examples/01-identity-governance.ps1) (PowerShell)
- [Configure Policy initiative](../../scripts/powershell/Configure-PolicyInitiative.ps1) (PowerShell)
- [Enable PIM](../../scripts/powershell/Enable-EntraPIM.ps1) (PowerShell)
- [Security audit queries](../../scripts/kql/security-audit.kql) (KQL)

---

## Knowledge Check

Complete the [Module 1 Knowledge Check](knowledge-check.md) after finishing all lessons. Target score: **80%+** before moving to Module 2.

---

## Key Architecture Patterns

### Enterprise Logging Architecture
```
                                    +------------------+
                                    |   SIEM (Sentinel)|
                                    +--------^---------+
                                             |
+---------------+    Diagnostic    +---------+---------+
| Azure         |    Settings      |    Event Hub      |
| Resources     +----------------->+   (real-time)     |
+---------------+                  +-------------------+
|               +----------------->+-------------------+
+---------------+    Diagnostic    | Log Analytics     |<--- Azure Monitor
                     Settings      | Workspace         |     Alerts
                                   | (centralized)     |
                +----------------->+-------------------+
                     Diagnostic    +-------------------+
                     Settings      | Storage Account   |
                +----------------->| (archive 7+ yrs)  |
                                   +-------------------+
```

### Zero Trust Identity
```
External Users ──> Microsoft Entra ID ──> Azure Resources
Internal Users ──>  (Conditional Access, PIM) ──> (Key Vault, SQL, Storage)
Applications  ──> Managed Identity ──> RBAC/Data Plane Access
```

### Governance Hierarchy
```
Root Management Group
  ├── Platform (networking, monitoring)
  ├── Landing Zones
  │     ├── Corp (internal apps)
  │     ├── Online (external apps)
  │     └── SAP (specialized)
  ├── Sandbox (experimentation)
  └── Decommissioned
```

---

## Exam Tips

| Keyword in Question | Answer Points To |
|---------------------|-----------------|
| "Multiple subscriptions" + "logging" | Single centralized Log Analytics workspace |
| "7+ years retention" | Storage Account (Log Analytics max = 730 days interactive) |
| "Real-time SIEM" | Event Hub streaming |
| "External partners" | Entra B2B with access packages |
| "Consumer-facing app" | Entra External ID (B2C replacement) |
| "Zero secrets in code" | Managed identity |
| "FIPS 140-2 Level 3" | Key Vault Premium |
| "Compliance framework" | Policy initiative (not individual policy) |
| "Just-in-time access" | PIM |
| "Periodic review of access" | Access Reviews |

---

## Official Microsoft Resources

### MS Learn Path
[AZ-305: Design identity, governance, and monitor solutions](https://learn.microsoft.com/training/paths/design-identity-governance-monitor-solutions/) (2 hr 25 min, 3 modules)
- [Design governance](https://learn.microsoft.com/training/modules/design-governance/)
- [Design authentication and authorization solutions](https://learn.microsoft.com/training/modules/design-authentication-authorization-solutions/)
- [Design a solution to log and monitor Azure resources](https://learn.microsoft.com/training/modules/design-solution-to-log-monitor-azure-resources/)

### Case Studies
Complete these scenario-based exercises from the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):
- [Design a governance solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/01-Governance.html)
- [Design authentication and authorization solutions](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/06-Authentication.html)
- [Fabrikam Residences — Logging and monitoring](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/07-Access.html)

### Practice Assessment
[Take the free AZ-305 practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) — identity and governance questions make up 25-30% of the exam.

---

## Microsoft Learn Path

[AZ-305: Design identity, governance, and monitor solutions](https://learn.microsoft.com/training/paths/design-identity-governance-monitor-solutions/)
