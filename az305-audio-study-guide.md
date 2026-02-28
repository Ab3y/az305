# AZ-305: Designing Microsoft Azure Infrastructure Solutions

**Audio-Friendly Study Guide**

This comprehensive study guide is organized for sequential audio playback. All content is presented in narrative format without tables, diagrams, or images.

**Navigate using bookmarks:**
Each module, lesson, and subsection has a bookmark anchor for easy navigation.

---

## Table of Contents

- [Syllabus](#syllabus)
- [Module 1: Overview](#module-1-overview)
- [Module 1: Lesson 1 - Logging and Monitoring](#module-1-lesson-1---logging-and-monitoring)
- [Module 1: Lesson 2 - Authentication and Authorization](#module-1-lesson-2---authentication-and-authorization)
- [Module 1: Lesson 3 - Governance](#module-1-lesson-3---governance)
- [Module 1: Knowledge Check](#module-1-knowledge-check)
- [Module 2: Overview](#module-2-overview)
- [Module 2: Lesson 1 - Relational Data](#module-2-lesson-1---relational-data)
- [Module 2: Lesson 2 - Non-Relational Data](#module-2-lesson-2---non-relational-data)
- [Module 2: Lesson 3 - Data Integration](#module-2-lesson-3---data-integration)
- [Module 2: Knowledge Check](#module-2-knowledge-check)
- [Module 3: Overview](#module-3-overview)
- [Module 3: Lesson 1 - Backup and Disaster Recovery](#module-3-lesson-1---backup-and-disaster-recovery)
- [Module 3: Lesson 2 - High Availability](#module-3-lesson-2---high-availability)
- [Module 3: Knowledge Check](#module-3-knowledge-check)
- [Module 4: Overview](#module-4-overview)
- [Module 4: Lesson 1 - Compute Solutions](#module-4-lesson-1---compute-solutions)
- [Module 4: Lesson 2 - Application Architecture](#module-4-lesson-2---application-architecture)
- [Module 4: Lesson 3 - Migrations](#module-4-lesson-3---migrations)
- [Module 4: Knowledge Check](#module-4-knowledge-check)
- [Module 5: Overview](#module-5-overview)
- [Module 5: Lesson 1 - Network Topology and Connectivity](#module-5-lesson-1---network-topology-and-connectivity)
- [Module 5: Lesson 2 - Network Security](#module-5-lesson-2---network-security)
- [Module 5: Lesson 3 - Load Balancing](#module-5-lesson-3---load-balancing)
- [Module 5: Knowledge Check](#module-5-knowledge-check)

---

<a id="syllabus"></a>

## Syllabus

# AZ-305 Self-Paced Training Course

**Designing Microsoft Azure Infrastructure Solutions**

---

## Course Overview

- **Attribute**: **Certification** | **Details**: Microsoft Certified: Azure Solutions Architect Expert
- **Attribute**: **Exam Code** | **Details**: AZ-305
- **Attribute**: **Passing Score** | **Details**: 700 / 1000
- **Attribute**: **Duration** | **Details**: 120 minutes, 40-60 questions
- **Attribute**: **Prerequisite** | **Details**: AZ-104 Azure Administrator Associate
- **Attribute**: **Format** | **Details**: Multiple choice, case studies, drag-and-drop, build list

This self-paced course is organized into **5 modules** aligned with the AZ-305 exam domains. Each module contains lessons, knowledge checks, hands-on labs, and exam tips.

---

## Exam Domain Weights

- **#**: 1 | **Domain**: Identity, Governance & Monitoring | **Weight**: 25-30% | **Module**: [Module 1](module-1-identity-governance/overview.md)
- **#**: 2 | **Domain**: Data Storage Solutions | **Weight**: 20-25% | **Module**: [Module 2](module-2-data-storage/overview.md)
- **#**: 3 | **Domain**: Business Continuity Solutions | **Weight**: 15-20% | **Module**: [Module 3](module-3-business-continuity/overview.md)
- **#**: 4 | **Domain**: Infrastructure & Compute Solutions | **Weight**: 30-35% (part 1) | **Module**: [Module 4](module-4-compute-apps/overview.md)
- **#**: 5 | **Domain**: Networking & Migrations | **Weight**: 30-35% (part 2) | **Module**: [Module 5](module-5-networking-migrations/overview.md)

---

## Recommended Study Plan

### Week 1-2: Foundations (Module 1)
- [ ] Complete all 3 lessons in Module 1
- [ ] Deploy Log Analytics workspace lab
- [ ] Deploy custom RBAC role lab
- [ ] Deploy Key Vault with Private Link lab
- [ ] Score 80%+ on Module 1 knowledge check

### Week 3-4: Data (Module 2)
- [ ] Complete all 3 lessons in Module 2
- [ ] Deploy SQL elastic pool lab
- [ ] Deploy Cosmos DB multi-region lab
- [ ] Deploy storage account lifecycle lab
- [ ] Score 80%+ on Module 2 knowledge check

### Week 5-6: Resilience (Module 3)
- [ ] Complete all 2 lessons in Module 3
- [ ] Deploy Recovery Services Vault lab
- [ ] Deploy SQL failover group lab
- [ ] Score 80%+ on Module 3 knowledge check

### Week 7-8: Compute & Apps (Module 4)
- [ ] Complete all 3 lessons in Module 4
- [ ] Deploy Container Apps lab
- [ ] Deploy APIM lab
- [ ] Score 80%+ on Module 4 knowledge check

### Week 9-10: Networking & Review (Module 5)
- [ ] Complete all 3 lessons in Module 5
- [ ] Deploy hub-spoke network lab
- [ ] Deploy Application Gateway WAF lab
- [ ] Score 80%+ on Module 5 knowledge check
- [ ] Take Microsoft's free practice assessment

### Week 11-12: Final Prep
- [ ] Review all quick reference cards in [docs/quick-reference-cards.md](../docs/quick-reference-cards.md)
- [ ] Complete all 100+ practice questions in [docs/practice-questions.md](../docs/practice-questions.md)
- [ ] Re-do any labs where you scored below 80%
- [ ] Take the [official practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- [ ] Schedule your exam

---

## How to Use This Course

### Each Module Contains

- **Component**: **README.md** | **Description**: Module overview, learning objectives, key concepts
- **Component**: **Lessons** | **Description**: Deep-dive content with architecture diagrams and decision matrices
- **Component**: **Knowledge Check** | **Description**: 10-15 scenario-based questions per module with explanations
- **Component**: **Labs** | **Description**: Hands-on exercises using Bicep templates from the `infra/` folder

### Study Approach

1. **Read the lesson** — understand the "why" behind each design decision
2. **Study the diagrams** — architecture patterns appear frequently on the exam
3. **Do the lab** — deploy real resources to solidify understanding
4. **Take the knowledge check** — identify gaps before moving on
5. **Review exam tips** — know the keyword patterns that signal specific answers

### Key Principle

> The AZ-305 exam tests **design decision-making**, not memorization. Every question asks "what should you recommend?" — focus on understanding trade-offs between services.

---

## Prerequisites & Setup

### Required Knowledge
- Azure resource management (AZ-104 level)
- Basic networking (VNets, subnets, NSGs)
- Identity concepts (Entra ID, RBAC)

### Required Tools
- Azure subscription (free trial works for most labs)
- [Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli) 2.x
- [PowerShell 7](https://learn.microsoft.com/powershell/scripting/install/installing-powershell) with Az module
- [VS Code](https://code.visualstudio.com/) with [Bicep extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep)

### Lab Cost Estimate
Most labs can run within a free Azure trial. Estimated cost for all labs: **$30-$50** if completed within 2 weeks and resources are deleted promptly.

---

## Cross-Cutting Themes

These principles apply to EVERY module and EVERY exam question:

### Well-Architected Framework Pillars
- **Pillar**: **Reliability** | **Key Question to Ask**: What is the SLA? What happens when this fails?
- **Pillar**: **Security** | **Key Question to Ask**: Who can access this? How are secrets managed?
- **Pillar**: **Cost Optimization** | **Key Question to Ask**: What is the cost model? Can we right-size?
- **Pillar**: **Operational Excellence** | **Key Question to Ask**: How do we monitor? How do we deploy?
- **Pillar**: **Performance Efficiency** | **Key Question to Ask**: Can it scale? What are the limits?

### Zero Trust Architecture
- **Verify explicitly** — authenticate and authorize every request
- **Least privilege access** — scoped RBAC, just-in-time access
- **Assume breach** — network segmentation, encryption at rest and in transit

### Managed Identity Pattern
Use managed identity for ALL service-to-service authentication. If a question offers managed identity as an option, it is almost always correct.

---

## Official Microsoft Learn Paths

Complete these learning paths alongside each course module for the best results.

- **#**: 0 | **Learning Path**: [AZ-305 Prerequisites](https://learn.microsoft.com/training/paths/microsoft-azure-architect-design-prerequisites/) | **Duration**: 5 hr 26 min | **Maps to**: Pre-work
- **#**: 1 | **Learning Path**: [Design identity, governance, and monitor solutions](https://learn.microsoft.com/training/paths/design-identity-governance-monitor-solutions/) | **Duration**: 2 hr 25 min | **Maps to**: Module 1
- **#**: 2 | **Learning Path**: [Design data storage solutions](https://learn.microsoft.com/training/paths/design-data-storage-solutions/) | **Duration**: 2 hr 44 min | **Maps to**: Module 2
- **#**: 3 | **Learning Path**: [Design business continuity solutions](https://learn.microsoft.com/training/paths/design-business-continuity-solutions/) | **Duration**: 1 hr 46 min | **Maps to**: Module 3
- **#**: 4 | **Learning Path**: [Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/) | **Duration**: 3 hr 39 min | **Maps to**: Modules 4 & 5

---

## Microsoft Learning Case Studies

Scenario-based exercises from the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):

- **Case Study**: [Design a governance solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/01-Governance.html) | **Maps to**: Module 1
- **Case Study**: [Design authentication and authorization solutions](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/06-Authentication.html) | **Maps to**: Module 1
- **Case Study**: [Fabrikam Residences — Logging and monitoring](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/07-Access.html) | **Maps to**: Module 1
- **Case Study**: [Design a non-relational storage solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/04-Nonrelationalstorage.html) | **Maps to**: Module 2
- **Case Study**: [Design a relational storage solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/03-Relationalstorage.html) | **Maps to**: Module 2
- **Case Study**: [Design a compute solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/02-Compute.html) | **Maps to**: Module 4
- **Case Study**: [Design an app architecture solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/05-Apparchitecture.html) | **Maps to**: Module 4
- **Case Study**: [Design a network solution — BI enterprise application](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/08-Logging.html) | **Maps to**: Module 5

---

## External Resources

- **Resource**: AZ-305 Exam Page | **Link**: [Official Exam Page](https://learn.microsoft.com/credentials/certifications/exams/az-305/)
- **Resource**: AZ-305 Study Guide | **Link**: [aka.ms/AZ305-StudyGuide](https://aka.ms/AZ305-StudyGuide)
- **Resource**: Free Practice Assessment | **Link**: [Practice Assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Resource**: Exam Sandbox (try the format) | **Link**: [aka.ms/examdemo](https://aka.ms/examdemo)
- **Resource**: Exam Prep Videos | **Link**: [Exam Readiness Zone](https://learn.microsoft.com/shows/exam-readiness-zone/preparing-for-az-305-design-identity-governance-and-monitoring-solutions-1-of-4)
- **Resource**: Azure Architecture Center | **Link**: [learn.microsoft.com/azure/architecture](https://learn.microsoft.com/azure/architecture/)
- **Resource**: Well-Architected Framework | **Link**: [learn.microsoft.com/azure/well-architected](https://learn.microsoft.com/azure/well-architected/)
- **Resource**: Cloud Adoption Framework | **Link**: [learn.microsoft.com/azure/cloud-adoption-framework](https://learn.microsoft.com/azure/cloud-adoption-framework/)
- **Resource**: Microsoft Learning AZ-305 Labs | **Link**: [Lab Case Studies](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/)
- **Resource**: Microsoft Learning AZ-305 Source | **Link**: [GitHub Repository](https://github.com/MicrosoftLearning/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions)

---

## Progress Tracker

- **Module**: 1 - Identity, Governance & Monitoring | **Status**: Not Started | **Knowledge Check Score**: ___% | **Labs Completed**: ___ / 4
- **Module**: 2 - Data Storage Solutions | **Status**: Not Started | **Knowledge Check Score**: ___% | **Labs Completed**: ___ / 4
- **Module**: 3 - Business Continuity & HA | **Status**: Not Started | **Knowledge Check Score**: ___% | **Labs Completed**: ___ / 3
- **Module**: 4 - Infrastructure & Compute | **Status**: Not Started | **Knowledge Check Score**: ___% | **Labs Completed**: ___ / 3
- **Module**: 5 - Networking & Migrations | **Status**: Not Started | **Knowledge Check Score**: ___% | **Labs Completed**: ___ / 3
- **Module**: **Practice Assessment** | **Status**: Not Taken | **Knowledge Check Score**: ___%
- **Module**: **Practice Assessment** | **Status**: Not Taken | **Knowledge Check Score**: ___%
- **Module**: **Exam Date** | **Status**: _____________

> **Practice Assessment:** [Take the free Microsoft practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) after completing all modules.


---

<a id="module-1-overview"></a>

## Module 1: Overview

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

- **#**: 1 | **Lesson**: [Logging and Monitoring](lesson-1-logging-monitoring.md) | **Duration**: 60 min | **Focus**: Log Analytics, Azure Monitor, Application Insights, routing logs
- **#**: 2 | **Lesson**: [Authentication and Authorization](lesson-2-auth.md) | **Duration**: 75 min | **Focus**: Entra ID, B2B/B2C, RBAC, managed identity, Key Vault
- **#**: 3 | **Lesson**: [Governance](lesson-3-governance.md) | **Duration**: 60 min | **Focus**: Management groups, Azure Policy, PIM, compliance

---

## Hands-On Labs

- **#**: 1 | **Lab**: Deploy Log Analytics workspace with data collection rules | **Bicep Template**: [log-analytics-workspace.bicep](../../infra/log-analytics-workspace.bicep) | **Estimated Time**: 20 min
- **#**: 2 | **Lab**: Create custom RBAC role and assign to managed identity | **Bicep Template**: [custom-rbac-role.bicep](../../infra/custom-rbac-role.bicep) | **Estimated Time**: 15 min
- **#**: 3 | **Lab**: Deploy Key Vault with Private Link and managed identity access | **Bicep Template**: [keyvault-with-private-link.bicep](../../infra/keyvault-with-private-link.bicep) | **Estimated Time**: 20 min
- **#**: 4 | **Lab**: Deploy Azure Policy initiative for compliance | **Bicep Template**: [azure-policy-initiative.bicep](../../infra/azure-policy-initiative.bicep) | **Estimated Time**: 15 min

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
[Diagram removed for audio]

### Zero Trust Identity
[Diagram removed for audio]

### Governance Hierarchy
[Diagram removed for audio]

---

## Exam Tips

- **Keyword in Question**: "Multiple subscriptions" + "logging" | **Answer Points To**: Single centralized Log Analytics workspace
- **Keyword in Question**: "7+ years retention" | **Answer Points To**: Storage Account (Log Analytics max = 730 days interactive)
- **Keyword in Question**: "Real-time SIEM" | **Answer Points To**: Event Hub streaming
- **Keyword in Question**: "External partners" | **Answer Points To**: Entra B2B with access packages
- **Keyword in Question**: "Consumer-facing app" | **Answer Points To**: Entra External ID (B2C replacement)
- **Keyword in Question**: "Zero secrets in code" | **Answer Points To**: Managed identity
- **Keyword in Question**: "FIPS 140-2 Level 3" | **Answer Points To**: Key Vault Premium
- **Keyword in Question**: "Compliance framework" | **Answer Points To**: Policy initiative (not individual policy)
- **Keyword in Question**: "Just-in-time access" | **Answer Points To**: PIM
- **Keyword in Question**: "Periodic review of access" | **Answer Points To**: Access Reviews

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


---

<a id="module-1-lesson-1---logging-and-monitoring"></a>

## Module 1: Lesson 1 - Logging and Monitoring

# Lesson 1: Logging and Monitoring

**Duration:** 60 minutes | **Domain Weight:** Part of 25-30%

---

## Learning Objectives

- Recommend a logging solution (Log Analytics workspace topology, retention tiers)
- Recommend a solution for routing logs (diagnostic settings, Azure Monitor Agent)
- Recommend a monitoring solution (Azure Monitor, Application Insights, alerts)

---

## 1. Azure Monitor Ecosystem

Azure Monitor is the unified monitoring platform for all Azure resources. Understanding its components is critical for AZ-305.

### Core Components

- **Component**: **Metrics** | **Purpose**: Numeric time-series data (CPU, memory, requests) | **When to Use**: Real-time performance monitoring, auto-scale rules
- **Component**: **Logs** | **Purpose**: Structured event data stored in Log Analytics | **When to Use**: Complex querying, long-term analysis, compliance
- **Component**: **Alerts** | **Purpose**: Automated notifications and actions | **When to Use**: Incident response, auto-remediation
- **Component**: **Workbooks** | **Purpose**: Interactive visual reports | **When to Use**: Dashboards, capacity planning
- **Component**: **Application Insights** | **Purpose**: APM for application telemetry | **When to Use**: Distributed tracing, performance profiling

### Architecture Decision: Where Does Data Go?

[Diagram removed for audio]

**Key Insight:** A single resource can have multiple diagnostic settings pointing to different destinations simultaneously. This is the "fan-out" pattern.

---

## 2. Log Analytics Workspace Design

### Topology Decision Tree

[Diagram removed for audio]

### Workspace Design Best Practices

- **Decision**: Number of workspaces | **Recommendation**: Start with **one** | **Rationale**: Simplifies management, enables cross-resource queries
- **Decision**: Access model | **Recommendation**: **Resource-context** RBAC | **Rationale**: Users see logs for resources they already have access to
- **Decision**: Region placement | **Recommendation**: Same region as resources | **Rationale**: Minimizes latency and egress costs
- **Decision**: Retention | **Recommendation**: 90 days interactive, archive for 7+ years | **Rationale**: Balance cost and compliance
- **Decision**: Pricing | **Recommendation**: Commitment tiers (100+ GB/day) | **Rationale**: Up to 30% savings over pay-as-you-go

### Retention Tiers

- **Tier**: **Interactive** | **Duration**: 30-730 days (default 30) | **Cost**: Standard ingestion + retention | **Query Performance**: Full KQL
- **Tier**: **Archive** | **Duration**: Up to 12 years | **Cost**: ~$0.02/GB/month | **Query Performance**: Restore or search jobs (slower)
- **Tier**: **Storage Account** | **Duration**: Unlimited | **Cost**: ~$0.01/GB/month (cool) | **Query Performance**: Not queryable (export/rehydrate)

**Exam Trap:** Log Analytics interactive retention max is 730 days (2 years), NOT 7 years. For 7+ year compliance, use Storage Account or archive tier.

---

## 3. Routing Logs

### Diagnostic Settings Configuration

Every Azure resource can emit three types of telemetry via diagnostic settings:

- **Telemetry Type**: **Activity Logs** | **Examples**: Resource creation, role assignments, policy events | **Destination Options**: Log Analytics, Event Hub, Storage
- **Telemetry Type**: **Resource Logs** | **Examples**: SQL query performance, Key Vault access, App Service requests | **Destination Options**: Log Analytics, Event Hub, Storage
- **Telemetry Type**: **Platform Metrics** | **Examples**: CPU utilization, disk IOPS, network bytes | **Destination Options**: Log Analytics (for long-term trending)

### Azure Monitor Agent (AMA)

AMA replaced the legacy Log Analytics Agent (MMA, retired August 2024).

- **Feature**: Supported OS | **Azure Monitor Agent**: Windows, Linux
- **Feature**: Configuration | **Azure Monitor Agent**: Data Collection Rules (DCRs)
- **Feature**: Multi-homing | **Azure Monitor Agent**: Yes (multiple workspaces)
- **Feature**: Auth model | **Azure Monitor Agent**: Managed identity
- **Feature**: Deployment | **Azure Monitor Agent**: Azure Policy (recommended), ARM/Bicep, manual

### Data Collection Rules (DCRs)

DCRs define:
- **What** data to collect (Windows events, Syslog, performance counters, custom logs)
- **Where** to send it (Log Analytics workspace)
- **How** to transform it (KQL transforms for filtering/enrichment at ingestion)

[Diagram removed for audio]

---

## 4. Monitoring Solutions

### Azure Monitor Alerts

- **Alert Type**: **Metric alerts** | **Signal Source**: Platform metrics | **Example**: CPU > 90% for 5 minutes
- **Alert Type**: **Log alerts** | **Signal Source**: Log Analytics queries | **Example**: Error count > 100 in 1 hour
- **Alert Type**: **Activity log alerts** | **Signal Source**: Activity log events | **Example**: Resource deleted, role assigned
- **Alert Type**: **Service Health alerts** | **Signal Source**: Azure service issues | **Example**: Planned maintenance, outages
- **Alert Type**: **Resource Health alerts** | **Signal Source**: Individual resource status | **Example**: VM unhealthy

**Action Groups** define what happens when an alert fires:
- Email/SMS/Voice
- Azure Function / Logic App / Webhook
- ITSM connector (ServiceNow, etc.)
- Automation Runbook

### Application Insights

- **Feature**: **Workspace-based mode** | **Design Impact**: Required for new deployments (classic deprecated)
- **Feature**: **Sampling** | **Design Impact**: Reduces cost; adaptive sampling for high-traffic apps
- **Feature**: **Distributed tracing** | **Design Impact**: Tracks requests across microservices
- **Feature**: **Availability tests** | **Design Impact**: URL ping or multi-step web tests from global locations
- **Feature**: **Live Metrics** | **Design Impact**: Real-time performance stream (no storage cost)
- **Feature**: **Smart Detection** | **Design Impact**: AI-powered anomaly alerts

**Cost Control Pattern:**
[Diagram removed for audio]

### Microsoft Sentinel (SIEM + SOAR)

When the exam mentions "security monitoring" or "threat detection," Sentinel is the answer:
- Built on Log Analytics workspace
- 200+ data connectors
- Built-in AI/ML for threat detection
- Automated response with playbooks (Logic Apps)

---

## 5. Decision Summary

### "Which monitoring service?" Quick Reference

- **Scenario**: Infrastructure metrics and alerts | **Service**: Azure Monitor
- **Scenario**: Log querying and analysis | **Service**: Log Analytics
- **Scenario**: Application performance | **Service**: Application Insights
- **Scenario**: Security analytics and SIEM | **Service**: Microsoft Sentinel
- **Scenario**: Network diagnostics | **Service**: Network Watcher
- **Scenario**: Service availability | **Service**: Service Health
- **Scenario**: Individual resource status | **Service**: Resource Health

---

## Key Terms Glossary

- **Term**: **DCR** | **Definition**: Data Collection Rule — defines data sources and destinations for Azure Monitor Agent
- **Term**: **AMA** | **Definition**: Azure Monitor Agent — the current agent for collecting VM/on-premises telemetry
- **Term**: **KQL** | **Definition**: Kusto Query Language — query language for Log Analytics and related services
- **Term**: **Resource-context RBAC** | **Definition**: Access to log data based on Azure resource permissions, not workspace permissions
- **Term**: **Diagnostic settings** | **Definition**: Configuration that routes Azure resource logs/metrics to Log Analytics, Event Hub, or Storage
- **Term**: **Commitment tier** | **Definition**: Pre-purchased Log Analytics capacity at a discount (100, 200, 300, ... GB/day)

---

## Next Steps

- **Lab:** Deploy [log-analytics-workspace.bicep](../../infra/log-analytics-workspace.bicep) and configure diagnostic settings
- **Practice:** Run KQL queries from [security-audit.kql](../../scripts/kql/security-audit.kql)
- **Continue:** [Lesson 2 — Authentication and Authorization](lesson-2-auth.md)

---

## References

- [Azure Monitor Overview](https://learn.microsoft.com/azure/azure-monitor/overview)
- [Log Analytics Workspace Design](https://learn.microsoft.com/azure/azure-monitor/logs/workspace-design)
- [Data Collection Rules](https://learn.microsoft.com/azure/azure-monitor/essentials/data-collection-rule-overview)
- [Application Insights Overview](https://learn.microsoft.com/azure/azure-monitor/app/app-insights-overview)


---

<a id="module-1-lesson-2---authentication-and-authorization"></a>

## Module 1: Lesson 2 - Authentication and Authorization

# Lesson 2: Authentication and Authorization

**Duration:** 75 minutes | **Domain Weight:** Part of 25-30%

---

## Learning Objectives

- Recommend an authentication solution (Entra ID, B2B, B2C, federation)
- Recommend an identity management solution (Entra ID vs. hybrid)
- Recommend a solution for authorizing access to Azure resources (RBAC, custom roles)
- Recommend a solution for authorizing access to on-premises resources (Entra Connect, pass-through auth)
- Recommend a solution to manage secrets, certificates, and keys (Key Vault)

---

## 1. Microsoft Entra ID Authentication

### Identity Scenarios

- **Scenario**: Cloud-only users | **Solution**: Microsoft Entra ID | **Key Feature**: MFA, Conditional Access, passwordless
- **Scenario**: Hybrid with on-premises AD | **Solution**: Entra Connect Sync or Cloud Sync | **Key Feature**: Password hash sync, pass-through auth
- **Scenario**: External partners | **Solution**: Entra External ID (B2B) | **Key Feature**: Partners use own credentials
- **Scenario**: Consumer-facing apps | **Solution**: Entra External ID | **Key Feature**: Social logins, custom branding (replaces B2C for new projects since May 2025)

### Authentication Methods (Strongest to Weakest)

- **Method**: FIDO2 security keys | **Security Level**: Highest | **User Experience**: Phishing-resistant, hardware key
- **Method**: Windows Hello for Business | **Security Level**: Highest | **User Experience**: Biometric or PIN, device-bound
- **Method**: Microsoft Authenticator (passwordless) | **Security Level**: High | **User Experience**: Phone-based, number matching
- **Method**: Certificate-based auth | **Security Level**: High | **User Experience**: Smart card / certificate
- **Method**: MFA (phone + password) | **Security Level**: Medium | **User Experience**: Two-step verification
- **Method**: Password only | **Security Level**: Low | **User Experience**: **Never acceptable for production**

### Conditional Access Policies

Conditional Access is the Zero Trust policy engine. It evaluates signals and enforces access decisions.

[Diagram removed for audio]

**Conditional Access Policy Matrix (Exam Pattern)**

- **User Type**: Admins | **MFA Required**: Always | **Device Compliance**: Required | **Location**: Named locations only | **Session Limit**: 1 hour
- **User Type**: Employees | **MFA Required**: Risk-based | **Device Compliance**: Required | **Location**: Any | **Session Limit**: 8 hours
- **User Type**: B2B Guests | **MFA Required**: Always | **Device Compliance**: Not enforced | **Location**: Named locations only | **Session Limit**: 4 hours
- **User Type**: Service accounts | **MFA Required**: N/A | **Device Compliance**: N/A | **Location**: N/A | **Session Limit**: Managed identity preferred

---

## 2. Hybrid Identity

### Entra Cloud Sync vs. Connect Sync

- **Feature**: **Management** | **Cloud Sync**: Cloud-based portal | **Connect Sync v2**: On-premises server
- **Feature**: **Agent** | **Cloud Sync**: Lightweight provisioning agent | **Connect Sync v2**: Full application install
- **Feature**: **Multi-forest disconnected** | **Cloud Sync**: Yes | **Connect Sync v2**: Limited
- **Feature**: **Device sync** | **Cloud Sync**: No | **Connect Sync v2**: Yes
- **Feature**: **Pass-through auth** | **Cloud Sync**: No | **Connect Sync v2**: Yes
- **Feature**: **Group writeback** | **Cloud Sync**: Limited | **Connect Sync v2**: Yes
- **Feature**: **AD FS federation** | **Cloud Sync**: No | **Connect Sync v2**: Yes
- **Feature**: **Large groups (50K+)** | **Cloud Sync**: Yes | **Connect Sync v2**: Yes
- **Feature**: **Recommended for** | **Cloud Sync**: New deployments (simple) | **Connect Sync v2**: Complex scenarios

### Decision Tree

[Diagram removed for audio]

### Password Sync Options

- **Method**: Password Hash Sync (PHS) | **Passwords in Cloud?**: Hash of hash | **On-Premises Dependency**: None after sync | **Best For**: Most scenarios (recommended)
- **Method**: Pass-Through Auth (PTA) | **Passwords in Cloud?**: No | **On-Premises Dependency**: Auth agent on-premises | **Best For**: Compliance: passwords never leave on-prem
- **Method**: Federation (AD FS) | **Passwords in Cloud?**: No | **On-Premises Dependency**: AD FS farm | **Best For**: Legacy apps, smart cards, third-party MFA

**Exam Tip:** PHS is Microsoft's recommended default. PTA only when compliance mandates passwords never leave on-premises. Federation only for legacy requirements.

---

## 3. External Identity (B2B and External ID)

### B2B vs. External ID (formerly B2C)

- **Feature**: **Target users** | **B2B Collaboration**: Partners, vendors, consultants | **External ID (Consumer)**: Customers, consumers
- **Feature**: **Credential source** | **B2B Collaboration**: Partner's own identity provider | **External ID (Consumer)**: Social accounts, email, local
- **Feature**: **Directory** | **B2B Collaboration**: Guest objects in your tenant | **External ID (Consumer)**: Separate external tenant
- **Feature**: **Access management** | **B2B Collaboration**: Access packages, access reviews | **External ID (Consumer)**: Custom user flows
- **Feature**: **Branding** | **B2B Collaboration**: Your tenant branding | **External ID (Consumer)**: Fully customizable
- **Feature**: **Licensing** | **B2B Collaboration**: Free (up to 50K MAU) | **External ID (Consumer)**: Per-authentication pricing

### Entitlement Management (Access Packages)

For B2B scenarios, access packages automate the lifecycle:

[Diagram removed for audio]

**Exam Keywords:**
- "External partners access Azure resources" → B2B + access packages
- "Quarterly review of guest access" → Access reviews
- "Consumer sign-up with social accounts" → External ID

---

## 4. Azure RBAC (Role-Based Access Control)

### RBAC Fundamentals

[Diagram removed for audio]

### Scope Hierarchy

[Diagram removed for audio]

Role assignments at a higher scope are inherited by all child scopes.

### Built-in vs. Custom Roles

- **Role Type**: **Built-in** | **When to Use**: Standard permissions exist | **Example**: Reader, Contributor, Owner
- **Role Type**: **Custom** | **When to Use**: Need specific combination | **Example**: "VM Restart Operator" (only restart, no delete)

### Key Built-in Roles (Exam Favorites)

- **Role**: **Owner** | **Permissions**: Full access + assign roles | **Exam Scenario**: Subscription administrators
- **Role**: **Contributor** | **Permissions**: Full access, cannot assign roles | **Exam Scenario**: DevOps teams
- **Role**: **Reader** | **Permissions**: View only | **Exam Scenario**: Auditors, monitoring teams
- **Role**: **User Access Administrator** | **Permissions**: Manage role assignments only | **Exam Scenario**: Security team
- **Role**: **Key Vault Secrets Officer** | **Permissions**: Manage secrets | **Exam Scenario**: Application teams (Key Vault RBAC)
- **Role**: **Storage Blob Data Contributor** | **Permissions**: Read/write blob data | **Exam Scenario**: Applications via managed identity

### Deny Assignments

- Override role assignments (explicit deny)
- Currently only created by Azure Blueprints/Deployment Stacks (not manually)
- Different from NotActions (which exclude actions from a role, not deny them)

**Critical Distinction:**
- `NotActions` = actions excluded from the role (others can grant them)
- `Deny assignment` = actions blocked regardless of other role assignments

---

## 5. Managed Identities

### System-Assigned vs. User-Assigned

- **Feature**: **Lifecycle** | **System-Assigned**: Tied to resource (deleted with it) | **User-Assigned**: Independent (you manage lifecycle)
- **Feature**: **Sharing** | **System-Assigned**: One identity per resource | **User-Assigned**: One identity across many resources
- **Feature**: **Pre-provisioning** | **System-Assigned**: Created with resource | **User-Assigned**: Created before resource
- **Feature**: **Use case** | **System-Assigned**: Simple, single-resource access | **User-Assigned**: Shared access, deployment slots
- **Feature**: **RBAC management** | **System-Assigned**: More role assignments needed | **User-Assigned**: Fewer assignments (shared)

### Decision Flow

[Diagram removed for audio]

### Common Managed Identity Scenarios

- **Source**: App Service | **Target**: Azure SQL | **Role Assignment**: No role needed — use Entra auth directly
- **Source**: App Service | **Target**: Key Vault | **Role Assignment**: Key Vault Secrets User
- **Source**: App Service | **Target**: Storage | **Role Assignment**: Storage Blob Data Contributor
- **Source**: App Service | **Target**: Service Bus | **Role Assignment**: Azure Service Bus Data Sender/Receiver
- **Source**: Container Apps | **Target**: Cosmos DB | **Role Assignment**: Cosmos DB Built-in Data Contributor
- **Source**: Functions | **Target**: Event Hub | **Role Assignment**: Azure Event Hubs Data Receiver

**Non-Negotiable Rule:** If managed identity is available, use it. Never store secrets in code, config files, or environment variables.

---

## 6. Azure Key Vault

### Key Vault Tiers

- **Feature**: Secrets, keys, certificates | **Standard**: Yes | **Premium**: Yes
- **Feature**: HSM-backed keys | **Standard**: Software-protected | **Premium**: **FIPS 140-2 Level 3**
- **Feature**: Price | **Standard**: Lower | **Premium**: Higher
- **Feature**: Use case | **Standard**: Most scenarios | **Premium**: Financial, government, compliance

### Access Model Decision

- **Model**: **Azure RBAC** (recommended) | **When to Use**: New deployments, unified management with other Azure resources
- **Model**: **Vault access policy** | **When to Use**: Legacy, per-vault granularity

### Key Vault Design Patterns

- **Pattern**: **Soft delete** | **Implementation**: Always enabled (prevents accidental deletion, 7-90 day recovery)
- **Pattern**: **Purge protection** | **Implementation**: Enable for compliance (prevents permanent deletion during retention)
- **Pattern**: **Private Link** | **Implementation**: Private endpoint for network isolation
- **Pattern**: **Secret rotation** | **Implementation**: Event Grid trigger on secret near-expiry → Function rotates → updates Key Vault
- **Pattern**: **Backup** | **Implementation**: Key Vault backup for individual keys/secrets (same geo only)

### Secret Rotation Architecture

[Diagram removed for audio]

**Exam Keywords:**
- "FIPS 140-2 Level 3" → Key Vault Premium
- "No secrets in code" → Managed identity
- "Secret rotation" → Event Grid + Function
- "Purge protection" → Compliance requirement
- "Private network only" → Private Link endpoint

---

## Summary: Authentication & Authorization Decision Matrix

- **Question Type**: "External partners need access" | **Answer Pattern**: B2B + access packages + access reviews
- **Question Type**: "Consumer-facing application" | **Answer Pattern**: Entra External ID
- **Question Type**: "Hybrid identity, simple setup" | **Answer Pattern**: Entra Cloud Sync
- **Question Type**: "Hybrid, need device sync" | **Answer Pattern**: Entra Connect Sync v2
- **Question Type**: "No secrets in application code" | **Answer Pattern**: Managed identity (user-assigned)
- **Question Type**: "FIPS 140-2 Level 3" | **Answer Pattern**: Key Vault Premium
- **Question Type**: "Least privilege custom permissions" | **Answer Pattern**: Custom RBAC role
- **Question Type**: "Multiple subscriptions, same access" | **Answer Pattern**: Role assignment at management group scope

---

## Next Steps

- **Lab:** Deploy [custom-rbac-role.bicep](../../infra/custom-rbac-role.bicep) and test assignments
- **Lab:** Deploy [keyvault-with-private-link.bicep](../../infra/keyvault-with-private-link.bicep) with managed identity
- **Practice:** Run [create-rbac-assignments.sh](../../scripts/az-cli/create-rbac-assignments.sh)
- **Continue:** [Lesson 3 — Governance](lesson-3-governance.md)

---

## References

- [Entra ID Overview](https://learn.microsoft.com/entra/fundamentals/whatis)
- [Conditional Access](https://learn.microsoft.com/entra/identity/conditional-access/overview)
- [B2B Collaboration](https://learn.microsoft.com/entra/external-id/what-is-b2b)
- [Azure RBAC](https://learn.microsoft.com/azure/role-based-access-control/overview)
- [Managed Identities](https://learn.microsoft.com/entra/identity/managed-identities-azure-resources/overview)
- [Key Vault Best Practices](https://learn.microsoft.com/azure/key-vault/general/best-practices)


---

<a id="module-1-lesson-3---governance"></a>

## Module 1: Lesson 3 - Governance

# Lesson 3: Governance

**Duration:** 60 minutes | **Domain Weight:** Part of 25-30%

---

## Learning Objectives

- Recommend a structure for management groups, subscriptions, and resource groups
- Recommend a strategy for resource tagging
- Recommend a solution for managing compliance (Azure Policy, Deployment Stacks)
- Recommend a solution for identity governance (PIM, access reviews, entitlement management)

---

## 1. Management Hierarchy Design

### The Four Levels

[Diagram removed for audio]

### Management Group Design Pattern (Azure Landing Zones)

[Diagram removed for audio]

### When to Split Subscriptions

- **Reason**: **Billing boundary** | **Example**: Separate cost centers for departments
- **Reason**: **Access boundary** | **Example**: Dev team cannot touch production
- **Reason**: **Scale limits** | **Example**: Approaching subscription resource limits
- **Reason**: **Compliance** | **Example**: Regulated workloads require isolation
- **Reason**: **Environment isolation** | **Example**: Dev / Test / Prod separation

### Resource Group Design

- **Pattern**: **Lifecycle** | **Group By**: Resources deployed/deleted together | **When**: Most common, recommended
- **Pattern**: **Application** | **Group By**: All resources for one app | **When**: Microservices teams
- **Pattern**: **Resource type** | **Group By**: All VMs, all databases | **When**: Shared platform teams
- **Pattern**: **Environment** | **Group By**: Dev, test, prod | **When**: Small organizations

**Key Rule:** A resource can only belong to one resource group. Resource groups are a logical container, NOT a security boundary (use RBAC for security).

---

## 2. Resource Tagging

### Tagging Strategy

- **Tag Category**: **Business** | **Example Tags**: `CostCenter`, `BusinessUnit`, `Owner` | **Purpose**: Chargeback, accountability
- **Tag Category**: **Technical** | **Example Tags**: `Environment`, `Application`, `Tier` | **Purpose**: Automation, filtering
- **Tag Category**: **Compliance** | **Example Tags**: `DataClassification`, `Compliance` | **Purpose**: Regulatory requirements
- **Tag Category**: **Operations** | **Example Tags**: `SLA`, `MaintenanceWindow`, `DR-Priority` | **Purpose**: Operations and DR planning

### Tag Enforcement Methods

- **Method**: Azure Policy: `require` | **Effect**: Deny creation without tag | **Use Case**: Mandatory tags (CostCenter, Owner)
- **Method**: Azure Policy: `inherit` | **Effect**: Copy tag from resource group using Modify effect | **Use Case**: Consistent tagging without user burden
- **Method**: Azure Policy: `audit` | **Effect**: Flag non-compliant resources | **Use Case**: Soft enforcement during rollout
- **Method**: ARM/Bicep template defaults | **Effect**: Apply in template | **Use Case**: IaC-deployed resources

### Tag Inheritance

Tags do NOT automatically inherit from subscription → resource group → resource. You must use **Azure Policy with Modify effect** to copy tags from parent scopes.

[Diagram removed for audio]

---

## 3. Azure Policy

### Policy Fundamentals

- **Concept**: **Policy definition** | **Description**: Single rule (e.g., "require HTTPS on storage")
- **Concept**: **Initiative (policy set)** | **Description**: Group of related policies (e.g., CIS Benchmark)
- **Concept**: **Assignment** | **Description**: Apply a policy/initiative to a scope
- **Concept**: **Exemption** | **Description**: Exclude a specific resource/scope from a policy
- **Concept**: **Remediation** | **Description**: Fix existing non-compliant resources

### Policy Effects (Order of Evaluation)

- **Effect**: **Disabled** | **Behavior**: Policy not evaluated | **When to Use**: Testing, temporary bypass
- **Effect**: **Append** | **Behavior**: Add fields to request | **When to Use**: Add required properties
- **Effect**: **Modify** | **Behavior**: Change properties on existing resources | **When to Use**: Tag inheritance, enable features
- **Effect**: **Deny** | **Behavior**: Block the request | **When to Use**: Hard guardrails (no public IPs, required encryption)
- **Effect**: **Audit** | **Behavior**: Log non-compliance, allow creation | **When to Use**: Soft enforcement, awareness
- **Effect**: **AuditIfNotExists** | **Behavior**: Audit if related resource missing | **When to Use**: Check for diagnostic settings
- **Effect**: **DeployIfNotExists (DINE)** | **Behavior**: Auto-deploy related resource | **When to Use**: Auto-enable monitoring, backups
- **Effect**: **Manual** | **Behavior**: Requires manual attestation | **When to Use**: Compliance processes

### Policy Assignment Strategy

- **Scope Level**: Root Management Group | **Policy Type**: Security baselines | **Effect**: **Deny** | **Example**: No public IPs, require encryption
- **Scope Level**: Platform MG | **Policy Type**: Platform operations | **Effect**: **DINE** | **Example**: Deploy diagnostic settings, enable Defender
- **Scope Level**: Landing Zone MG | **Policy Type**: Application governance | **Effect**: **Audit → Deny** | **Example**: Allowed SKUs, required tags
- **Scope Level**: Subscription | **Policy Type**: Environment-specific | **Effect**: **Deny** | **Example**: Allowed regions, resource types
- **Scope Level**: Sandbox MG | **Policy Type**: Relaxed | **Effect**: **Audit only** | **Example**: Security policies only (not cost)

### Initiatives vs. Individual Policies

- **Use**: Single specific requirement | **Type**: Policy definition
- **Use**: Compliance framework (CIS, NIST, PCI) | **Type**: Initiative
- **Use**: Custom organizational standards | **Type**: Custom initiative

**Exam Tip:** If the question mentions "compliance framework" or "regulatory standard," the answer is an initiative, not individual policies.

### Azure Blueprints → Deployment Stacks

Blueprints are **deprecated (July 2026)**. The replacement is **Deployment Stacks**:

- **Feature**: Scope | **Blueprints (deprecated)**: Subscription | **Deployment Stacks**: Management group, subscription, or resource group
- **Feature**: Deny settings | **Blueprints (deprecated)**: Blueprint lock | **Deployment Stacks**: Deny settings on stack
- **Feature**: Template support | **Blueprints (deprecated)**: ARM only | **Deployment Stacks**: Bicep and ARM
- **Feature**: Versioning | **Blueprints (deprecated)**: Built-in | **Deployment Stacks**: Git-based
- **Feature**: Status | **Blueprints (deprecated)**: Deprecated July 2026 | **Deployment Stacks**: GA, actively developed

---

## 4. Compliance Management

### Microsoft Defender for Cloud

- **Feature**: **Secure Score** | **Purpose**: Overall security posture (0-100%)
- **Feature**: **Regulatory compliance dashboard** | **Purpose**: Map controls to standards (CIS, NIST, PCI-DSS)
- **Feature**: **Recommendations** | **Purpose**: Prioritized security improvements
- **Feature**: **Cloud Security Posture Management (CSPM)** | **Purpose**: Free tier for basic posture
- **Feature**: **Cloud Workload Protection (CWP)** | **Purpose**: Paid plans for specific resource types

### Compliance Dashboard Flow

[Diagram removed for audio]

---

## 5. Identity Governance

### Privileged Identity Management (PIM)

PIM provides just-in-time (JIT) privileged access:

- **Feature**: **Eligible assignments** | **Purpose**: User CAN activate the role (not active by default)
- **Feature**: **Time-bound activation** | **Purpose**: Role active for 1-8 hours only
- **Feature**: **Approval workflow** | **Purpose**: Require approval before activation
- **Feature**: **MFA on activation** | **Purpose**: Force re-authentication
- **Feature**: **Justification** | **Purpose**: Require reason for activation
- **Feature**: **Audit trail** | **Purpose**: Full log of who activated what, when, and why

### PIM Configuration Pattern

[Diagram removed for audio]

### Access Reviews

- **Setting**: **Frequency** | **Recommendation**: Quarterly for guests, semi-annual for employees
- **Setting**: **Reviewers** | **Recommendation**: Resource owners or managers
- **Setting**: **Auto-apply** | **Recommendation**: Remove access if not reviewed
- **Setting**: **Scope** | **Recommendation**: Groups, application assignments, Azure roles

### Entitlement Management

For lifecycle management of access packages:

[Diagram removed for audio]

### Identity Governance Decision Matrix

- **Scenario**: Admins need temporary elevated access | **Solution**: PIM (eligible assignments)
- **Scenario**: Review if guests still need access | **Solution**: Access reviews
- **Scenario**: External partners need scoped, time-limited access | **Solution**: Entitlement management (access packages)
- **Scenario**: Prevent permanent Owner assignments | **Solution**: PIM with time-bound activation
- **Scenario**: Automate user onboarding/offboarding | **Solution**: Lifecycle workflows

---

## 6. Summary Decision Matrix

- **Exam Keyword**: "Management group" + "multiple subscriptions" | **Answer**: Policy at management group scope
- **Exam Keyword**: "Tag enforcement" | **Answer**: Azure Policy with Deny effect
- **Exam Keyword**: "Tag inheritance" | **Answer**: Azure Policy with Modify effect
- **Exam Keyword**: "CIS Benchmark" / "compliance framework" | **Answer**: Policy initiative + Defender for Cloud
- **Exam Keyword**: "Just-in-time admin access" | **Answer**: PIM with eligible assignments
- **Exam Keyword**: "Quarterly guest review" | **Answer**: Access reviews
- **Exam Keyword**: "Time-limited partner access" | **Answer**: Entitlement management (access packages)
- **Exam Keyword**: "Prevent accidental deletion" | **Answer**: Resource locks (not governance, but often tested)
- **Exam Keyword**: "Blueprints replacement" | **Answer**: Deployment Stacks
- **Exam Keyword**: "Environment standardization" | **Answer**: Deployment Stacks + Policy

---

## Next Steps

- **Lab:** Deploy [azure-policy-initiative.bicep](../../infra/azure-policy-initiative.bicep)
- **Practice:** Run [Configure-PolicyInitiative.ps1](../../scripts/powershell/Configure-PolicyInitiative.ps1)
- **Practice:** Run [Enable-EntraPIM.ps1](../../scripts/powershell/Enable-EntraPIM.ps1)
- **Knowledge Check:** [Module 1 Knowledge Check](knowledge-check.md)

---

## References

- [Management Groups](https://learn.microsoft.com/azure/governance/management-groups/overview)
- [Azure Policy Overview](https://learn.microsoft.com/azure/governance/policy/overview)
- [Deployment Stacks](https://learn.microsoft.com/azure/azure-resource-manager/bicep/deployment-stacks)
- [PIM Overview](https://learn.microsoft.com/entra/id-governance/privileged-identity-management/pim-configure)
- [Access Reviews](https://learn.microsoft.com/entra/id-governance/access-reviews-overview)
- [Azure Landing Zones](https://learn.microsoft.com/azure/cloud-adoption-framework/ready/landing-zone/)


---

<a id="module-1-knowledge-check"></a>

## Module 1: Knowledge Check

# Module 1 Knowledge Check: Identity, Governance & Monitoring

**Target Score:** 80%+ before moving to Module 2

---

## Instructions

Choose the BEST answer for each scenario. Focus on understanding WHY each answer is correct — the exam tests design decision-making.

---

### Q1. Logging Architecture

Contoso Ltd. operates 50+ Azure subscriptions across multiple business units. They need centralized log collection with 90-day retention for compliance, cost-efficient storage for older logs, and the ability to query across all subscriptions. What should you recommend?

- A. One Log Analytics workspace per subscription with cross-workspace queries
- B. A single centralized Log Analytics workspace with resource-context RBAC
- C. Azure Monitor Logs with dedicated cluster and customer-managed keys
- D. Multiple Log Analytics workspaces federated with Azure Data Explorer

**Show Answer**

**Correct: B**

A single centralized workspace with resource-context RBAC provides unified querying, cost efficiency (bulk ingestion pricing via commitment tiers), and granular access control based on Azure resource permissions. This is the recommended pattern for multi-subscription enterprises.

- **A is wrong:** Multiple workspaces increase cost and complexity. Cross-workspace queries have limits and are slower.
- **C is wrong:** Dedicated clusters require 500GB+/day commitment — overkill unless you need CMK or higher performance.
- **D is wrong:** ADX federation adds complexity; only justified for petabyte-scale analytics.

---

### Q2. Log Routing

Wingtip Toys needs to route Azure Activity Logs to their SIEM system (Splunk), retain logs in Azure for 7 years for compliance, and enable near-real-time alerting. Which architecture should you recommend?

- A. Diagnostic settings to Event Hub (SIEM) + Storage Account (archive) + Log Analytics (alerting)
- B. Diagnostic settings to Log Analytics only with 7-year retention
- C. Azure Monitor Agent to Log Analytics with export rules to Storage
- D. Direct API integration from SIEM to Azure Activity Log

**Show Answer**

**Correct: A**

The fan-out pattern using diagnostic settings to multiple destinations: Event Hub for real-time SIEM streaming, Storage Account for cost-effective 7-year archive, Log Analytics for alerting and investigation.

- **B is wrong:** Log Analytics interactive retention max is 730 days (2 years). Archive tier extends to 12 years, but Storage Account is more cost-effective for 7-year retention.
- **C is wrong:** Azure Monitor Agent is for VMs, not Activity Logs. Export rules go to Storage, not Log Analytics.
- **D is wrong:** Polling APIs is inefficient and doesn't meet real-time requirements.

---

### Q3. Application Performance

Fabrikam runs microservices on AKS. They require distributed tracing, auto-scaling based on custom metrics, and cost control. What should you recommend?

- A. Application Insights with workspace-based mode, sampling enabled, and custom metrics for KEDA
- B. Application Insights with classic mode and Prometheus integration
- C. Azure Monitor for Containers with built-in Application Insights
- D. Third-party APM tool with OpenTelemetry export

**Show Answer**

**Correct: A**

Workspace-based Application Insights is the modern standard — unified querying, sampling reduces costs, and custom metrics can drive KEDA autoscaling.

- **B is wrong:** Classic mode is deprecated. Prometheus doesn't provide distributed tracing.
- **C is wrong:** Azure Monitor for Containers provides infrastructure metrics, not application-level traces.
- **D is wrong:** Third-party tools add cost and complexity when native options meet requirements.

---

### Q4. External Partner Access

Contoso needs to give 500 consultants (external users) access to specific Azure resources. Consultants should use their own corporate credentials, access must be reviewable quarterly, and least privilege is mandatory. What should you recommend?

- A. Microsoft Entra B2B with access packages and access reviews
- B. Microsoft Entra B2C with custom policies
- C. Sync external users to Microsoft Entra ID with Entra Connect
- D. Create cloud-only accounts for each consultant

**Show Answer**

**Correct: A**

B2B collaboration with Entitlement Management (access packages) and access reviews is the enterprise pattern for external partner access. Users keep their own credentials, access is time-bound and reviewable.

- **B is wrong:** B2C / External ID is for consumer-facing apps, not business partner collaboration.
- **C is wrong:** Syncing external users violates identity sovereignty and complicates management.
- **D is wrong:** Cloud-only accounts create credential sprawl and don't support quarterly reviews natively.

---

### Q5. Managed Identity

Wingtip Toys runs an e-commerce app on Azure App Service that needs to access Azure SQL Database, Azure Storage, and Azure Key Vault. The solution must have zero secrets in application code and support automatic credential rotation. What should you recommend?

- A. User-assigned managed identity for all services
- B. System-assigned managed identity for each App Service instance
- C. Service principal with certificate authentication stored in Key Vault
- D. Microsoft Entra application with client secret rotated monthly

**Show Answer**

**Correct: A**

User-assigned managed identity provides zero-secret authentication, automatic credential management, and can be shared across deployment slots and resources.

- **B is wrong:** System-assigned identities work but create access management overhead with multiple instances (each gets a unique identity).
- **C is wrong:** Service principals with certificates still require certificate management — managed identity eliminates this.
- **D is wrong:** Client secrets require rotation management and risk exposure.

---

### Q6. Key Vault Design

Fabrikam's financial services application must store database connection strings, API keys, and SSL certificates. They require FIPS 140-2 Level 3 compliance, automatic secret rotation, and private network access only. What should you recommend?

- A. Key Vault Premium with Private Link, Event Grid for rotation, purge protection enabled
- B. Key Vault Standard with VNet service endpoints and manual rotation
- C. Azure App Configuration with Key Vault references
- D. Key Vault Premium with access policies and public endpoint

**Show Answer**

**Correct: A**

Key Vault Premium provides HSM-backed keys (FIPS 140-2 Level 3). Private Link ensures private network access. Event Grid triggers automatic rotation. Purge protection is required for financial compliance.

- **B is wrong:** Standard tier doesn't provide FIPS 140-2 Level 3 (software-protected only). Service endpoints don't provide private IPs. Manual rotation doesn't meet requirements.
- **C is wrong:** App Configuration stores configuration, not secrets. Key Vault references are good practice but don't address the core requirements.
- **D is wrong:** Public endpoint violates "private network access only."

---

### Q7. RBAC Design

A company has three Azure subscriptions: Dev, Test, and Prod. The security team must be able to manage role assignments across all subscriptions but should have no other permissions. What should you recommend?

- A. Assign User Access Administrator role at the management group scope containing all three subscriptions
- B. Assign Owner role at each subscription scope
- C. Assign Contributor role at the management group scope
- D. Create a custom role with all permissions at each subscription

**Show Answer**

**Correct: A**

User Access Administrator grants only the ability to manage role assignments. Assigning at management group scope covers all subscriptions with a single assignment. This follows least privilege.

- **B is wrong:** Owner has full permissions — violates least privilege.
- **C is wrong:** Contributor cannot manage role assignments.
- **D is wrong:** Unnecessary complexity; a built-in role meets the requirement.

---

### Q8. Policy Design

An organization must ensure that all new Azure resources are created only in East US and West US regions, and all resources must have a `CostCenter` tag. Non-compliant existing resources should be flagged but not deleted. What should you recommend?

- A. Two Azure policies: `Deny` effect for allowed regions, `Audit` effect for the tag requirement on existing resources with `Deny` for new resources
- B. A single Azure Policy initiative with `Deny` effect for both policies
- C. Azure Blueprints with region and tag constraints
- D. Management group with subscription-level region restrictions

**Show Answer**

**Correct: A**

Two separate policies address different requirements: Deny for regions (block new resources in wrong regions), and a combination approach for tags (Audit existing, Deny new). This enforces going forward while giving time to remediate existing resources.

- **B is wrong:** Deny on existing resources without tags would block updates to those resources.
- **C is wrong:** Blueprints are deprecated (July 2026).
- **D is wrong:** Management groups don't inherently restrict regions.

---

### Q9. PIM Configuration

A company's database administrators need occasional Contributor access to the production subscription. Access should require approval, be time-limited, and create an audit trail. What should you recommend?

- A. PIM with eligible assignment, 4-hour maximum activation, approval required, justification required
- B. Permanent Contributor role with conditional access policy
- C. Just-in-time VM access through Defender for Cloud
- D. Custom RBAC role with time-based conditions

**Show Answer**

**Correct: A**

PIM with eligible assignments provides just-in-time access with all required controls: approval workflow, time-bound activation, justification, and full audit trail.

- **B is wrong:** Permanent role doesn't meet "occasional" or "time-limited" requirements. Conditional access controls authentication, not role activation.
- **C is wrong:** JIT VM access is for network ports (NSG), not RBAC.
- **D is wrong:** Custom RBAC roles don't support time-based activation natively.

---

### Q10. Hybrid Identity

A company is migrating to Azure. They have three disconnected AD forests, cannot allow password hashes in the cloud, and need seamless SSO. What should you recommend?

- A. Entra Connect Sync v2 with pass-through authentication and seamless SSO
- B. Entra Cloud Sync with password hash sync
- C. AD FS federation with each forest
- D. Entra Cloud Sync with pass-through authentication

**Show Answer**

**Correct: A**

Entra Connect Sync v2 supports pass-through authentication (passwords never leave on-premises) and seamless SSO. It can be configured for multiple forests.

- **B is wrong:** Cloud Sync doesn't support pass-through authentication. PHS puts password hashes in the cloud.
- **C is wrong:** AD FS adds significant infrastructure complexity. Only use for legacy requirements.
- **D is wrong:** Cloud Sync does not support pass-through authentication.

---

## Scoring

- **Score**: 9-10 / 10 (90-100%) | **Next Step**: Excellent! Move to Module 2
- **Score**: 8 / 10 (80%) | **Next Step**: Good. Review missed questions, then move to Module 2
- **Score**: 6-7 / 10 (60-70%) | **Next Step**: Review the relevant lessons before proceeding
- **Score**: Below 6 / 10 (<60%) | **Next Step**: Re-study the full module before retaking

---

## Continue Learning

- **MS Learn Path:** [Design identity, governance, and monitor solutions](https://learn.microsoft.com/training/paths/design-identity-governance-monitor-solutions/)
- **Case Studies:** [Governance](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/01-Governance.html) | [Authentication](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/06-Authentication.html) | [Logging](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/07-Access.html)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Next:** [Module 2 — Data Storage Solutions](../module-2-data-storage/overview.md)


---

<a id="module-2-overview"></a>

## Module 2: Overview

# Module 2: Data Storage Solutions (20-25%)

**Theme: "Right Data, Right Service, Right Tier"**

---

## Why This Module Comes Second

With identity and governance established, we now tackle data — the heart of most Azure solutions. Understanding storage patterns is prerequisite to business continuity (Module 3) and application architecture (Module 4).

---

## Learning Objectives

After completing this module, you will be able to:

- Recommend relational data solutions (SQL Database, SQL MI, PostgreSQL, MySQL)
- Select database service and compute tiers (DTU vs. vCore, serverless vs. provisioned)
- Design for database scalability (elastic pools, read replicas, sharding)
- Recommend semi-structured data solutions (Cosmos DB, Table Storage)
- Design storage account architectures (tiers, lifecycle, redundancy)
- Recommend data integration and analysis solutions (Data Factory, Synapse)

---

## Lessons

- **#**: 1 | **Lesson**: [Relational Data](lesson-1-relational-data.md) | **Duration**: 60 min | **Focus**: SQL Database, SQL MI, tiers, scalability, protection
- **#**: 2 | **Lesson**: [Non-Relational Data](lesson-2-non-relational-data.md) | **Duration**: 60 min | **Focus**: Cosmos DB, Blob Storage, Data Lake, Files
- **#**: 3 | **Lesson**: [Data Integration](lesson-3-data-integration.md) | **Duration**: 45 min | **Focus**: Data Factory, Synapse Analytics, data pipelines

---

## Hands-On Labs

- **#**: 1 | **Lab**: Deploy SQL elastic pool with vCore model | **Bicep Template**: [sql-database-elastic-pool.bicep](../../infra/sql-database-elastic-pool.bicep) | **Estimated Time**: 20 min
- **#**: 2 | **Lab**: Deploy Cosmos DB with multi-region writes | **Bicep Template**: [cosmosdb-multi-region.bicep](../../infra/cosmosdb-multi-region.bicep) | **Estimated Time**: 25 min
- **#**: 3 | **Lab**: Deploy storage account with lifecycle policies | **Bicep Template**: [storage-account-tiered.bicep](../../infra/storage-account-tiered.bicep) | **Estimated Time**: 15 min
- **#**: 4 | **Lab**: Deploy SQL failover group across regions | **Bicep Template**: [sql-failover-group.bicep](../../infra/sql-failover-group.bicep) | **Estimated Time**: 20 min

### Supporting Scripts
- [Data storage examples](../../scripts/examples/03-data-storage.ps1) (PowerShell)
- [New Cosmos DB account](../../scripts/powershell/New-CosmosDBAccount.ps1) (PowerShell)
- [Set storage lifecycle](../../scripts/powershell/Set-StorageLifecycle.ps1) (PowerShell)
- [Cost analysis queries](../../scripts/kql/cost-analysis.kql) (KQL)

---

## Knowledge Check

Complete the [Module 2 Knowledge Check](knowledge-check.md) after finishing all lessons. Target score: **80%+** before moving to Module 3.

---

## Key Architecture Patterns

### Relational Database Decision Tree
[Diagram removed for audio]

### Cosmos DB Global Distribution
[Diagram removed for audio]

### Storage Tiers Lifecycle
[Diagram removed for audio]

---

## Exam Tips

- **Keyword in Question**: "Full SQL Server compatibility" | **Answer Points To**: SQL Managed Instance
- **Keyword in Question**: "Multi-tenant, shared resources" | **Answer Points To**: Elastic pools
- **Keyword in Question**: "Variable workload, cost sensitive" | **Answer Points To**: Serverless compute tier
- **Keyword in Question**: "Global distribution, <10ms writes" | **Answer Points To**: Cosmos DB multi-region writes
- **Keyword in Question**: "Partition key" | **Answer Points To**: High cardinality, included in most queries
- **Keyword in Question**: "7-year archive" | **Answer Points To**: Storage Account (Archive tier or cool)
- **Keyword in Question**: "Immutable storage" | **Answer Points To**: Legal hold or time-based retention
- **Keyword in Question**: "Regional outage protection" | **Answer Points To**: GRS / GZRS redundancy
- **Keyword in Question**: "ETL / data orchestration" | **Answer Points To**: Azure Data Factory
- **Keyword in Question**: "Unified analytics" | **Answer Points To**: Azure Synapse Analytics

---

## Official Microsoft Resources

### MS Learn Path
[AZ-305: Design data storage solutions](https://learn.microsoft.com/training/paths/design-data-storage-solutions/) (2 hr 44 min, 3 modules)
- [Design a data storage solution for non-relational data](https://learn.microsoft.com/training/modules/design-data-storage-solution-for-non-relational-data/)
- [Design a data storage solution for relational data](https://learn.microsoft.com/training/modules/design-data-storage-solution-for-relational-data/)
- [Design data integration](https://learn.microsoft.com/training/modules/design-data-integration/)

### Case Studies
Complete these scenario-based exercises from the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):
- [Design a non-relational storage solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/04-Nonrelationalstorage.html)
- [Design a relational storage solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/03-Relationalstorage.html)

### Practice Assessment
[Take the free AZ-305 practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) — data storage questions make up 20-25% of the exam.


---

<a id="module-2-lesson-1---relational-data"></a>

## Module 2: Lesson 1 - Relational Data

# Lesson 1: Relational Data Storage

**Duration:** 60 minutes | **Domain Weight:** Part of 20-25%

---

## Learning Objectives

- Recommend a solution for storing relational data
- Recommend a database service tier and compute tier
- Recommend a solution for database scalability
- Recommend a solution for data protection

---

## 1. Azure Relational Database Services

### Service Comparison

- **Service**: **Azure SQL Database** | **SQL Compatibility**: T-SQL subset | **Key Differentiator**: Fully managed PaaS, elastic pools | **Exam Use Case**: New cloud-native apps
- **Service**: **Azure SQL Managed Instance** | **SQL Compatibility**: ~100% SQL Server | **Key Differentiator**: VNet integration, Agent jobs, CLR | **Exam Use Case**: Lift-and-shift SQL Server
- **Service**: **SQL Server on Azure VM** | **SQL Compatibility**: 100% SQL Server | **Key Differentiator**: Full OS control | **Exam Use Case**: Legacy apps, custom configs
- **Service**: **Azure Database for PostgreSQL** | **SQL Compatibility**: PostgreSQL | **Key Differentiator**: Open source, Citus for scale-out | **Exam Use Case**: PostgreSQL workloads
- **Service**: **Azure Database for MySQL** | **SQL Compatibility**: MySQL | **Key Differentiator**: Open source | **Exam Use Case**: LAMP stack, WordPress

### Decision Tree

[Diagram removed for audio]

### SQL MI vs. SQL Database — When It Matters

- **Feature**: SQL Agent jobs | **SQL Database**: No (use Elastic Jobs) | **SQL Managed Instance**: Yes
- **Feature**: CLR integration | **SQL Database**: No | **SQL Managed Instance**: Yes
- **Feature**: Service Broker | **SQL Database**: No | **SQL Managed Instance**: Yes (within instance)
- **Feature**: Cross-database queries | **SQL Database**: No (elastic query limited) | **SQL Managed Instance**: Yes
- **Feature**: VNet integration | **SQL Database**: Private endpoint | **SQL Managed Instance**: Native VNet deployment
- **Feature**: Linked servers | **SQL Database**: No | **SQL Managed Instance**: Yes
- **Feature**: SSIS | **SQL Database**: No (use Data Factory) | **SQL Managed Instance**: No (use Data Factory)
- **Feature**: Migration from on-prem | **SQL Database**: Partial compatibility | **SQL Managed Instance**: Near-seamless

---

## 2. Service Tiers and Compute Models

### Purchasing Models

- **Model**: **DTU** (Database Transaction Unit) | **Best For**: Simple, predictable workloads | **How It Works**: Bundled CPU + memory + IO
- **Model**: **vCore** | **Best For**: Fine-grained control, hybrid benefit | **How It Works**: Choose CPU cores and storage independently

**Exam Rule:** vCore is recommended for most production scenarios. DTU is simpler but inflexible.

### vCore Service Tiers

- **Tier**: **General Purpose** | **Use Case**: Most workloads | **Key Features**: Remote storage, zone redundant option | **SLA**: 99.99%
- **Tier**: **Business Critical** | **Use Case**: Low latency, HA | **Key Features**: Local SSD, built-in read replica, zone redundant | **SLA**: 99.99%
- **Tier**: **Hyperscale** | **Use Case**: Very large databases (up to 100 TB) | **Key Features**: Rapid scale-out, instant backups, up to 4 read replicas | **SLA**: 99.99%

### Compute Tiers (SQL Database)

- **Tier**: **Provisioned** | **Best For**: Predictable workloads | **Key Feature**: Reserved compute, Azure Hybrid Benefit eligible
- **Tier**: **Serverless** | **Best For**: Variable/intermittent workloads | **Key Feature**: Auto-pause (no cost when idle), auto-scale

### Serverless Auto-Pause Decision

[Diagram removed for audio]

**Exam Trap:** Serverless has a warm-up delay when resuming from pause. Do NOT recommend for latency-sensitive production apps.

---

## 3. Database Scalability

### Vertical Scaling (Scale Up)

- **Approach**: Change service tier | **When**: Need more IO or features | **Impact**: Brief connectivity interruption
- **Approach**: Add vCores | **When**: CPU-bound workload | **Impact**: Usually online
- **Approach**: Increase max storage | **When**: Running out of space | **Impact**: Online, no downtime

### Horizontal Scaling Options

- **Pattern**: **Elastic pools** | **Service**: SQL Database | **Use Case**: Multi-tenant SaaS (shared resources across databases)
- **Pattern**: **Read replicas** | **Service**: SQL Database (Business Critical/Hyperscale) | **Use Case**: Offload read-heavy reporting
- **Pattern**: **Sharding** | **Service**: SQL Database (Elastic Database tools) | **Use Case**: Very large datasets split across databases
- **Pattern**: **Hyperscale** | **Service**: SQL Database Hyperscale | **Use Case**: Large databases needing instant scale
- **Pattern**: **Geo-replication** | **Service**: SQL Database | **Use Case**: Cross-region read offload

### Elastic Pools Deep Dive

[Diagram removed for audio]

**When to use elastic pools:**
- Multiple databases with variable, non-overlapping peak usage
- Multi-tenant applications (one DB per tenant)
- Cost savings when per-database provisioned cost would be higher

**When NOT to use elastic pools:**
- Single database with consistent, high utilization
- Databases that always peak simultaneously
- Databases needing different service tiers

---

## 4. Data Protection

### Encryption

- **Layer**: **At rest** | **Feature**: Transparent Data Encryption (TDE) | **Default?**: Yes (service-managed key)
- **Layer**: **At rest (custom)** | **Feature**: TDE with customer-managed key (BYOK) | **Default?**: Optional (Key Vault)
- **Layer**: **In transit** | **Feature**: TLS 1.2+ | **Default?**: Yes, enforced
- **Layer**: **In use** | **Feature**: Always Encrypted | **Default?**: Optional (client-side encryption)

### Always Encrypted vs. Dynamic Data Masking

- **Feature**: **Protection level** | **Always Encrypted**: Data encrypted in DB, only client decrypts | **Dynamic Data Masking**: Data visible to privileged users, masked for others
- **Feature**: **Use case** | **Always Encrypted**: DBA should NOT see sensitive data (SSN, credit cards) | **Dynamic Data Masking**: Non-privileged users see masked data
- **Feature**: **Performance** | **Always Encrypted**: Client-side crypto overhead | **Dynamic Data Masking**: No performance impact
- **Feature**: **Exam keyword** | **Always Encrypted**: "Even DBAs cannot see data" | **Dynamic Data Masking**: "Hide data from non-privileged users"

### Row-Level Security

Controls which rows a user can access in a table:
[Diagram removed for audio]

**Exam Keyword:** "Users should only see their own data" → Row-Level Security

### Backup and Recovery

- **Feature**: Automated backups | **SQL Database**: Yes (full weekly, diff 12-24hr, log 5-10min) | **SQL MI**: Yes
- **Feature**: Point-in-time restore (PITR) | **SQL Database**: 1-35 days (default 7) | **SQL MI**: 1-35 days
- **Feature**: Long-term retention (LTR) | **SQL Database**: Up to 10 years | **SQL MI**: Up to 10 years
- **Feature**: Geo-restore | **SQL Database**: Yes (from GRS backup) | **SQL MI**: Yes
- **Feature**: Backup redundancy | **SQL Database**: LRS, ZRS, GRS | **SQL MI**: LRS, ZRS, GRS

---

## 5. Summary Decision Matrix

- **Exam Scenario**: Cloud-native app, no legacy SQL features | **Recommended Service / Feature**: Azure SQL Database
- **Exam Scenario**: Lift-and-shift SQL Server with Agent jobs | **Recommended Service / Feature**: SQL Managed Instance
- **Exam Scenario**: Full OS control, third-party tools | **Recommended Service / Feature**: SQL Server on Azure VM
- **Exam Scenario**: Multi-tenant SaaS, variable workloads | **Recommended Service / Feature**: Elastic pools
- **Exam Scenario**: Intermittent, dev/test database | **Recommended Service / Feature**: Serverless compute
- **Exam Scenario**: Read-heavy reporting offload | **Recommended Service / Feature**: Read replicas (Business Critical)
- **Exam Scenario**: DBAs cannot see sensitive data | **Recommended Service / Feature**: Always Encrypted
- **Exam Scenario**: Non-privileged users see masked data | **Recommended Service / Feature**: Dynamic Data Masking
- **Exam Scenario**: Users see only their own rows | **Recommended Service / Feature**: Row-Level Security
- **Exam Scenario**: 7-year backup retention | **Recommended Service / Feature**: Long-term retention (LTR) policy

---

## Next Steps

- **Lab:** Deploy [sql-database-elastic-pool.bicep](../../infra/sql-database-elastic-pool.bicep)
- **Lab:** Deploy [sql-failover-group.bicep](../../infra/sql-failover-group.bicep)
- **Continue:** [Lesson 2 — Non-Relational Data](lesson-2-non-relational-data.md)

---

## References

- [Azure SQL Database Overview](https://learn.microsoft.com/azure/azure-sql/database/sql-database-paas-overview)
- [SQL Managed Instance Overview](https://learn.microsoft.com/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview)
- [vCore vs. DTU](https://learn.microsoft.com/azure/azure-sql/database/purchasing-models)
- [Elastic Pools](https://learn.microsoft.com/azure/azure-sql/database/elastic-pool-overview)
- [Always Encrypted](https://learn.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)


---

<a id="module-2-lesson-2---non-relational-data"></a>

## Module 2: Lesson 2 - Non-Relational Data

# Lesson 2: Non-Relational Data Storage

**Duration:** 60 minutes | **Domain Weight:** Part of 20-25%

---

## Learning Objectives

- Recommend a solution for storing semi-structured data (Cosmos DB, Table Storage)
- Recommend a solution for storing unstructured data (Blob Storage, Data Lake, Files)
- Balance features, performance, and costs across storage solutions
- Recommend a data solution for protection and durability

---

## 1. Azure Cosmos DB

### API Selection

- **API**: **NoSQL (Core)** | **Use Case**: New applications, most flexible | **Data Model**: JSON documents | **Exam Keyword**: Default recommendation
- **API**: **MongoDB** | **Use Case**: Existing MongoDB apps | **Data Model**: BSON documents | **Exam Keyword**: "Migrate MongoDB"
- **API**: **Cassandra** | **Use Case**: Wide-column, write-heavy | **Data Model**: Column families | **Exam Keyword**: "Migrate Cassandra"
- **API**: **Gremlin** | **Use Case**: Graph relationships | **Data Model**: Graph (vertices/edges) | **Exam Keyword**: "Social network, recommendations"
- **API**: **Table** | **Use Case**: Key-value, simple | **Data Model**: Key-value pairs | **Exam Keyword**: "Migrate from Table Storage"

**Exam Rule:** For new projects, always recommend the **NoSQL (Core) API** unless the question explicitly mentions an existing MongoDB/Cassandra/Graph workload.

### Partition Key Selection

The most critical Cosmos DB design decision. **Cannot be changed after creation.**

- **Criteria**: Cardinality | **Good Partition Key**: High (tenantId, userId) | **Bad Partition Key**: Low (status, country)
- **Criteria**: Distribution | **Good Partition Key**: Even across partitions | **Bad Partition Key**: Hot partitions (all writes to one)
- **Criteria**: Query scope | **Good Partition Key**: Included in most queries | **Bad Partition Key**: Rarely in WHERE clause
- **Criteria**: Size | **Good Partition Key**: Each logical partition < 20 GB | **Bad Partition Key**: Single partition > 20 GB

**Example Decisions:**
- **Scenario**: Multi-tenant SaaS | **Good Key**: `/tenantId` | **Bad Key**: `/status` | **Why**: Even distribution, tenant-scoped queries
- **Scenario**: E-commerce orders | **Good Key**: `/customerId` | **Bad Key**: `/orderDate` | **Why**: Customer queries are common
- **Scenario**: IoT telemetry | **Good Key**: `/deviceId` | **Bad Key**: `/sensorType` | **Why**: Per-device queries, even distribution

### Consistency Levels

- **Level**: **Strong** | **Guarantee**: Linearizable reads | **Latency**: Highest | **Cost**: Highest | **Exam Use Case**: Financial transactions
- **Level**: **Bounded Staleness** | **Guarantee**: Reads lag by K versions or T time | **Latency**: High | **Cost**: High | **Exam Use Case**: Leaderboards, counters
- **Level**: **Session** | **Guarantee**: Read-your-writes within session | **Latency**: Medium | **Cost**: Medium | **Exam Use Case**: **Default — recommended for most**
- **Level**: **Consistent Prefix** | **Guarantee**: Reads never see out-of-order writes | **Latency**: Low | **Cost**: Low | **Exam Use Case**: Social media feeds
- **Level**: **Eventual** | **Guarantee**: No ordering guarantee | **Latency**: Lowest | **Cost**: Lowest | **Exam Use Case**: Analytics, non-critical reads

### Provisioned vs. Serverless

- **Model**: **Provisioned** | **Best For**: Production, predictable throughput | **RU Billing**: Per-second RU/s (reserved)
- **Model**: **Autoscale** | **Best For**: Variable but somewhat predictable | **RU Billing**: Auto-scales 10%-100% of max RU/s
- **Model**: **Serverless** | **Best For**: Dev/test, low/intermittent traffic | **RU Billing**: Per-request RU consumption

### Global Distribution

[Diagram removed for audio]

- **Configuration**: Single region | **Latency**: Lowest cost | **Cost**: $ | **Use Case**: Regional apps
- **Configuration**: Multi-region read | **Latency**: Low reads globally | **Cost**: $$ | **Use Case**: Global apps, read-heavy
- **Configuration**: Multi-region write | **Latency**: <10ms writes globally | **Cost**: $$$ | **Use Case**: Global apps, write-heavy

**Conflict Resolution (multi-region writes):**
- Last-Writer-Wins (LWW): Default, simple, uses `_ts` timestamp
- Custom: Stored procedure for merge logic

---

## 2. Azure Blob Storage

### Storage Account Types

- **Type**: **General-purpose v2** | **Performance**: Standard (HDD) | **Redundancy**: LRS/ZRS/GRS/GZRS | **Use Case**: Most workloads
- **Type**: **Premium Block Blob** | **Performance**: Premium (SSD) | **Redundancy**: LRS/ZRS | **Use Case**: Low-latency, high transaction
- **Type**: **Premium File Shares** | **Performance**: Premium (SSD) | **Redundancy**: LRS/ZRS | **Use Case**: Enterprise file shares
- **Type**: **Premium Page Blobs** | **Performance**: Premium (SSD) | **Redundancy**: LRS | **Use Case**: VM disks (unmanaged)

### Access Tiers

- **Tier**: **Hot** | **Min Retention**: None | **Access Cost**: Lowest | **Storage Cost**: Highest | **Use Case**: Frequently accessed data
- **Tier**: **Cool** | **Min Retention**: 30 days | **Access Cost**: Medium | **Storage Cost**: Medium | **Use Case**: Infrequent access (monthly)
- **Tier**: **Cold** | **Min Retention**: 90 days | **Access Cost**: Higher | **Storage Cost**: Lower | **Use Case**: Rare access (quarterly)
- **Tier**: **Archive** | **Min Retention**: 180 days | **Access Cost**: Highest (rehydrate first) | **Storage Cost**: Lowest | **Use Case**: Compliance, long-term backup

### Lifecycle Management

Automate tier transitions with policies:

[Diagram removed for audio]

### Redundancy Options

- **Option**: **LRS** | **Copies**: 3 | **Scope**: Single datacenter | **SLA**: 99.9% | **Exam Keyword**: "Cost sensitive"
- **Option**: **ZRS** | **Copies**: 3 | **Scope**: 3 availability zones | **SLA**: 99.9% | **Exam Keyword**: "Zone failure"
- **Option**: **GRS** | **Copies**: 6 | **Scope**: 2 regions | **SLA**: 99.9% | **Exam Keyword**: "Regional outage"
- **Option**: **GZRS** | **Copies**: 6 | **Scope**: 3 zones + paired region | **SLA**: 99.9% | **Exam Keyword**: "Zone + regional failure"
- **Option**: **RA-GRS** | **Copies**: 6 | **Scope**: 2 regions, read in secondary | **SLA**: 99.99% | **Exam Keyword**: "Read during outage"
- **Option**: **RA-GZRS** | **Copies**: 6 | **Scope**: 3 zones + paired region, read | **SLA**: 99.99% | **Exam Keyword**: "Highest durability"

### Data Protection Features

- **Feature**: **Soft delete** | **Purpose**: Recover deleted blobs (1-365 days) | **Exam Keyword**: "Accidental deletion"
- **Feature**: **Versioning** | **Purpose**: Keep previous versions of blobs | **Exam Keyword**: "Track changes"
- **Feature**: **Point-in-time restore** | **Purpose**: Restore container to a previous state | **Exam Keyword**: "Ransomware recovery"
- **Feature**: **Immutable storage** | **Purpose**: Prevent modification/deletion | **Exam Keyword**: "Regulatory compliance"
- **Feature**: **Legal hold** | **Purpose**: Immutable until hold removed | **Exam Keyword**: "Litigation hold"
- **Feature**: **Time-based retention** | **Purpose**: Immutable for set period | **Exam Keyword**: "WORM compliance"

---

## 3. Azure Data Lake Storage Gen2

Data Lake Storage Gen2 = Blob Storage + Hierarchical Namespace (HNS)

- **Feature**: Namespace | **Blob Storage**: Flat | **Data Lake Gen2**: Hierarchical (true directories)
- **Feature**: Rename/move operations | **Blob Storage**: Expensive (copy+delete) | **Data Lake Gen2**: Atomic (instant)
- **Feature**: ACLs | **Blob Storage**: Container-level | **Data Lake Gen2**: File/directory-level (POSIX)
- **Feature**: Analytics integration | **Blob Storage**: Good | **Data Lake Gen2**: Optimized (Spark, Synapse)
- **Feature**: Lifecycle management | **Blob Storage**: Yes | **Data Lake Gen2**: Yes
- **Feature**: Cost | **Blob Storage**: Standard | **Data Lake Gen2**: Standard (same pricing)

### Data Lake Design Pattern (Medallion Architecture)

[Diagram removed for audio]

---

## 4. Azure Files

- **Feature**: Protocol | **Standard**: SMB 3.x, NFS 4.1 | **Premium**: SMB 3.x, NFS 4.1
- **Feature**: Performance | **Standard**: HDD-backed | **Premium**: SSD-backed
- **Feature**: Max share size | **Standard**: 100 TiB | **Premium**: 100 TiB
- **Feature**: IOPS | **Standard**: Up to 20,000 | **Premium**: Up to 100,000
- **Feature**: Use case | **Standard**: File shares, lift-and-shift | **Premium**: Low-latency file workloads

### Azure Files vs. Azure NetApp Files

- **Factor**: Performance | **Azure Files**: Standard/Premium | **Azure NetApp Files**: Ultra-low latency
- **Factor**: Protocol | **Azure Files**: SMB, NFS 4.1 | **Azure NetApp Files**: SMB, NFS 3/4.1
- **Factor**: Use case | **Azure Files**: General file shares | **Azure NetApp Files**: SAP, HPC, databases
- **Factor**: Cost | **Azure Files**: Lower | **Azure NetApp Files**: Higher
- **Factor**: Management | **Azure Files**: Standard storage account | **Azure NetApp Files**: Dedicated NetApp service

### Azure File Sync

Extends Azure Files to on-premises Windows Servers:
- **Cloud tiering:** Frequently accessed files local, cold files in cloud
- **Multi-site sync:** Sync same share across multiple Windows Servers
- **Rapid DR:** Provision new server, install agent, instant access to files

---

## 5. Summary Decision Matrix

- **Data Type**: JSON documents, globally distributed | **Service**: Cosmos DB (NoSQL API) | **Key Decision Factor**: Partition key, consistency level
- **Data Type**: Key-value, simple queries | **Service**: Cosmos DB (Table API) or Table Storage | **Key Decision Factor**: Cost vs. features
- **Data Type**: Graph relationships | **Service**: Cosmos DB (Gremlin API) | **Key Decision Factor**: Social, recommendation engines
- **Data Type**: Binary files, media, backups | **Service**: Blob Storage | **Key Decision Factor**: Access tier, redundancy
- **Data Type**: Big data analytics | **Service**: Data Lake Storage Gen2 | **Key Decision Factor**: Hierarchical namespace
- **Data Type**: File shares (SMB/NFS) | **Service**: Azure Files | **Key Decision Factor**: Standard vs. Premium
- **Data Type**: Ultra-low latency files | **Service**: Azure NetApp Files | **Key Decision Factor**: SAP, HPC

---

## Next Steps

- **Lab:** Deploy [cosmosdb-multi-region.bicep](../../infra/cosmosdb-multi-region.bicep)
- **Lab:** Deploy [storage-account-tiered.bicep](../../infra/storage-account-tiered.bicep)
- **Continue:** [Lesson 3 — Data Integration](lesson-3-data-integration.md)

---

## References

- [Cosmos DB Overview](https://learn.microsoft.com/azure/cosmos-db/introduction)
- [Cosmos DB Partitioning](https://learn.microsoft.com/azure/cosmos-db/partitioning-overview)
- [Blob Storage Access Tiers](https://learn.microsoft.com/azure/storage/blobs/access-tiers-overview)
- [Data Lake Storage Gen2](https://learn.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)
- [Storage Redundancy](https://learn.microsoft.com/azure/storage/common/storage-redundancy)


---

<a id="module-2-lesson-3---data-integration"></a>

## Module 2: Lesson 3 - Data Integration

# Lesson 3: Data Integration

**Duration:** 45 minutes | **Domain Weight:** Part of 20-25%

---

## Learning Objectives

- Recommend a solution for data integration (Data Factory, Synapse pipelines)
- Recommend a solution for data analysis (Synapse Analytics, Databricks, Power BI)

---

## 1. Azure Data Factory (ADF)

### What It Does

ADF is a cloud-based ETL/ELT orchestration service for data movement and transformation.

### Core Components

- **Component**: **Pipeline** | **Purpose**: Logical grouping of activities
- **Component**: **Activity** | **Purpose**: A processing step (copy, transform, control flow)
- **Component**: **Dataset** | **Purpose**: Named reference to data (source or destination)
- **Component**: **Linked Service** | **Purpose**: Connection string to data stores
- **Component**: **Trigger** | **Purpose**: Defines when a pipeline runs (schedule, event, tumbling window)
- **Component**: **Integration Runtime** | **Purpose**: Compute infrastructure for activities

### Integration Runtime Types

- **Type**: **Azure** | **Location**: Azure cloud | **Use Case**: Cloud-to-cloud data movement
- **Type**: **Self-Hosted** | **Location**: On-premises / VM | **Use Case**: On-premises data access, private networks
- **Type**: **Azure-SSIS** | **Location**: Azure cloud | **Use Case**: Run existing SSIS packages

### Key Patterns

- **Pattern**: **Full load** | **Implementation**: Copy all data each run | **Exam Keyword**: Simple, small datasets
- **Pattern**: **Incremental load** | **Implementation**: Copy only changed data (watermark column) | **Exam Keyword**: Large datasets, efficiency
- **Pattern**: **Event-driven** | **Implementation**: Trigger pipeline on blob creation | **Exam Keyword**: Real-time ingestion
- **Pattern**: **Parameterized** | **Implementation**: Dynamic datasets and linked services | **Exam Keyword**: Multi-tenant, reusable pipelines
- **Pattern**: **Metadata-driven** | **Implementation**: Configuration table drives pipeline behavior | **Exam Keyword**: Enterprise-scale ingestion

### Data Factory vs. Synapse Pipelines

- **Feature**: Engine | **Data Factory**: Same | **Synapse Pipelines**: Same
- **Feature**: Standalone service | **Data Factory**: Yes | **Synapse Pipelines**: Embedded in Synapse workspace
- **Feature**: Git integration | **Data Factory**: Yes | **Synapse Pipelines**: Yes
- **Feature**: Monitoring | **Data Factory**: ADF Monitor | **Synapse Pipelines**: Synapse Studio Monitor
- **Feature**: Best for | **Data Factory**: Pure ETL/ELT orchestration | **Synapse Pipelines**: Unified analytics (ETL + query + ML)
- **Feature**: Data flows | **Data Factory**: Yes | **Synapse Pipelines**: Yes
- **Feature**: Cost model | **Data Factory**: Per pipeline run | **Synapse Pipelines**: Per pipeline run

**Exam Decision:** If the scenario is pure data movement/transformation → Data Factory. If the scenario includes analytics, Spark, or warehousing → Synapse (which includes pipelines).

---

## 2. Azure Synapse Analytics

### Components

- **Component**: **Dedicated SQL pool** | **Purpose**: Data warehousing (MPP) | **Billing Model**: Reserved DWU (always running)
- **Component**: **Serverless SQL pool** | **Purpose**: Ad-hoc queries over data lake | **Billing Model**: Per-TB scanned
- **Component**: **Apache Spark pool** | **Purpose**: Big data processing, ML | **Billing Model**: Per-node-hour
- **Component**: **Pipelines** | **Purpose**: Data orchestration (same as ADF) | **Billing Model**: Per-run
- **Component**: **Data Explorer pool** | **Purpose**: Log and telemetry analytics (KQL) | **Billing Model**: Per-cluster

### When to Use Each Pool

- **Workload**: Enterprise data warehouse (star schema) | **Pool**: Dedicated SQL pool | **Why**: MPP, optimized for complex queries
- **Workload**: Ad-hoc queries over files in data lake | **Pool**: Serverless SQL pool | **Why**: No infrastructure, pay-per-query
- **Workload**: Data transformation, feature engineering | **Pool**: Spark pool | **Why**: Distributed compute, Python/Scala/R
- **Workload**: Real-time log analytics | **Pool**: Data Explorer pool | **Why**: KQL, time-series optimized

### Dedicated vs. Serverless Decision

[Diagram removed for audio]

---

## 3. Other Analytics Services

### Azure Databricks

- **Feature**: Based on | **Description**: Apache Spark (managed)
- **Feature**: Differentiator | **Description**: Collaborative notebooks, Delta Lake, MLflow
- **Feature**: Best for | **Description**: Advanced analytics, ML/AI, data engineering
- **Feature**: Integration | **Description**: Reads from ADLS Gen2, writes to SQL/Cosmos

### Databricks vs. Synapse Spark

- **Factor**: Ecosystem | **Databricks**: Rich partner ecosystem, Delta Lake | **Synapse Spark**: Integrated with Synapse workspace
- **Factor**: Notebooks | **Databricks**: Collaborative, multi-language | **Synapse Spark**: Integrated with SQL pools
- **Factor**: ML support | **Databricks**: MLflow, AutoML | **Synapse Spark**: SparkML, ONNX
- **Factor**: Best for | **Databricks**: Data science teams | **Synapse Spark**: Unified analytics teams

### Azure Stream Analytics

Real-time stream processing using SQL-like query language.

- **Pattern**: **IoT analytics** | **Input**: IoT Hub / Event Hub | **Processing**: Windowed aggregation | **Output**: Power BI, SQL, Cosmos
- **Pattern**: **Real-time dashboards** | **Input**: Event Hub | **Processing**: Tumbling/sliding windows | **Output**: Power BI
- **Pattern**: **Anomaly detection** | **Input**: Event Hub | **Processing**: Built-in ML functions | **Output**: Alert / Azure Function

### Power BI Integration Points

- **Data Source**: Azure SQL | **Connection Type**: DirectQuery or Import | **Refresh**: Real-time or scheduled
- **Data Source**: Synapse dedicated pool | **Connection Type**: DirectQuery | **Refresh**: Real-time
- **Data Source**: Synapse serverless | **Connection Type**: DirectQuery | **Refresh**: On-demand
- **Data Source**: Cosmos DB | **Connection Type**: Import | **Refresh**: Scheduled
- **Data Source**: ADLS Gen2 | **Connection Type**: Dataflow | **Refresh**: Scheduled

---

## 4. Enterprise Data Platform Architecture

[Diagram removed for audio]

### Key Design Principles

1. **Data Factory for orchestration**, Synapse/Spark for transformation
2. **ADLS Gen2 as the central data lake** (medallion architecture)
3. **Private endpoints for all data services**
4. **Managed identity for all pipeline authentication** (no connection strings in factories)
5. **Incremental loads** wherever possible (watermark pattern)

---

## 5. Summary Decision Matrix

- **Scenario**: Cloud-to-cloud data movement | **Service**: Data Factory
- **Scenario**: On-premises data access | **Service**: Data Factory + Self-Hosted IR
- **Scenario**: Enterprise data warehouse | **Service**: Synapse dedicated SQL pool
- **Scenario**: Ad-hoc queries on data lake files | **Service**: Synapse serverless SQL pool
- **Scenario**: Big data / ML workloads | **Service**: Databricks or Synapse Spark
- **Scenario**: Real-time stream processing | **Service**: Stream Analytics
- **Scenario**: Business intelligence | **Service**: Power BI
- **Scenario**: Unified analytics platform | **Service**: Synapse Analytics workspace

---

## Next Steps

- **Lab:** Explore [Data Factory pipeline patterns](../../scripts/examples/03-data-storage.ps1)
- **Knowledge Check:** [Module 2 Knowledge Check](knowledge-check.md)

---

## References

- [Azure Data Factory Overview](https://learn.microsoft.com/azure/data-factory/introduction)
- [Synapse Analytics Overview](https://learn.microsoft.com/azure/synapse-analytics/overview-what-is)
- [Data Factory vs. Synapse Pipelines](https://learn.microsoft.com/azure/synapse-analytics/data-integration/concepts-data-factory-differences)
- [Stream Analytics Overview](https://learn.microsoft.com/azure/stream-analytics/stream-analytics-introduction)


---

<a id="module-2-knowledge-check"></a>

## Module 2: Knowledge Check

# Module 2 Knowledge Check: Data Storage Solutions

**Target Score:** 80%+ before moving to Module 3

---

## Instructions

Choose the BEST answer for each scenario. Focus on trade-offs between services, tiers, and features.

---

### Q1. Relational Database Selection

A company is migrating a SQL Server database to Azure. The application uses SQL Agent jobs, CLR assemblies, and cross-database queries. They want a fully managed solution with minimal code changes. What should you recommend?

- A. Azure SQL Database with elastic jobs
- B. Azure SQL Managed Instance
- C. SQL Server on Azure VM
- D. Azure Database for PostgreSQL

**Show Answer**

**Correct: B**

SQL Managed Instance provides ~100% SQL Server compatibility including SQL Agent, CLR, and cross-database queries in a fully managed PaaS service — minimal code changes needed.

- **A is wrong:** SQL Database doesn't support SQL Agent jobs natively, CLR, or cross-database queries.
- **C is wrong:** SQL on VM works but isn't "fully managed" — you manage patching, HA, backups.
- **D is wrong:** PostgreSQL is a different database engine entirely.

---

### Q2. Compute Tier Selection

A startup has a database that is heavily used during business hours (8 AM - 6 PM) but nearly idle at night and on weekends. They want to minimize costs. What should you recommend?

- A. Azure SQL Database — Serverless compute tier
- B. Azure SQL Database — General Purpose provisioned
- C. Azure SQL Database — Hyperscale tier
- D. Azure SQL Managed Instance

**Show Answer**

**Correct: A**

Serverless auto-pauses when idle (no compute charges) and auto-scales during active periods. Ideal for intermittent workloads with significant idle time.

- **B is wrong:** Provisioned compute charges continuously, even during idle hours.
- **C is wrong:** Hyperscale is for very large databases, not cost optimization for variable workloads.
- **D is wrong:** SQL MI is always running — no auto-pause capability.

---

### Q3. Elastic Pools

A SaaS company has 50 tenant databases. Each averages 5 DTUs but can spike to 50 DTUs. Spikes don't happen simultaneously. What should you recommend?

- A. 50 individual S3 databases (100 DTUs each)
- B. An elastic pool with 500 eDTUs shared across all databases
- C. 50 individual serverless databases
- D. A single database with row-level security for multi-tenancy

**Show Answer**

**Correct: B**

Elastic pools are designed for this exact scenario — multiple databases with variable, non-overlapping peak usage sharing a common resource pool. 500 eDTUs handles peaks while averaging much lower usage.

- **A is wrong:** Over-provisioning each database at peak capacity wastes resources and budget.
- **C is wrong:** 50 individual serverless databases don't share resources and each has minimum billing.
- **D is wrong:** Single database with RLS is a different architecture — operational complexity and doesn't scale the same way.

---

### Q4. Cosmos DB Partition Key

An e-commerce application stores orders in Cosmos DB. Queries are typically by customer (get all orders for a customer) and by order ID. The company has millions of customers worldwide. What partition key should you recommend?

- A. `/customerId`
- B. `/orderDate`
- C. `/status`
- D. `/region`

**Show Answer**

**Correct: A**

`/customerId` has high cardinality (millions of unique values), enables even distribution, and aligns with the most common query pattern (get orders by customer). Point reads by orderId within a customer partition are efficient.

- **B is wrong:** Date-based keys create hot partitions (all writes go to "today's" partition).
- **C is wrong:** Status has low cardinality (e.g., "pending," "shipped," "delivered") — creates very uneven distribution.
- **D is wrong:** Region has low cardinality and doesn't align with the primary query pattern.

---

### Q5. Cosmos DB Consistency

A financial application processes bank transfers between accounts. The application must guarantee that after a transfer, both the debit and credit are immediately visible to all readers. What Cosmos DB consistency level should you recommend?

- A. Strong
- B. Session
- C. Bounded Staleness
- D. Eventual

**Show Answer**

**Correct: A**

Strong consistency guarantees linearizable reads — after a write completes, all subsequent reads return the updated value. Required for financial transactions where read-after-write consistency across all clients is mandatory.

- **B is wrong:** Session consistency only guarantees read-your-writes within a single session, not across all readers.
- **C is wrong:** Bounded Staleness allows a configurable lag — not appropriate for immediate financial visibility.
- **D is wrong:** Eventual consistency offers no ordering guarantees — unacceptable for financial data.

---

### Q6. Storage Redundancy

A healthcare company stores medical images in Azure Blob Storage. Regulatory requirements mandate that data must survive a regional outage, and the application must be able to read data even during a regional failover. What redundancy option should you recommend?

- A. RA-GRS (Read-Access Geo-Redundant Storage)
- B. GRS (Geo-Redundant Storage)
- C. ZRS (Zone-Redundant Storage)
- D. LRS (Locally Redundant Storage)

**Show Answer**

**Correct: A**

RA-GRS provides 6 copies across two regions (like GRS) PLUS read access to the secondary region during normal operations. The application can read from the secondary if the primary region fails.

- **B is wrong:** GRS replicates to a secondary region but data is NOT readable until Microsoft initiates a failover.
- **C is wrong:** ZRS protects against zone failures within a single region, not regional outages.
- **D is wrong:** LRS has 3 copies in a single datacenter — no protection against zone or regional failure.

---

### Q7. Immutable Storage

A law firm must store legal documents that cannot be modified or deleted for 7 years to comply with SEC Rule 17a-4. What should you recommend?

- A. Blob Storage with time-based immutable retention policy (7 years)
- B. Blob Storage with soft delete enabled (7-year retention)
- C. Blob Storage with versioning enabled
- D. Data Lake Storage Gen2 with ACLs

**Show Answer**

**Correct: A**

Time-based immutable retention policy implements true WORM (Write Once, Read Many) storage. Blobs cannot be modified or deleted until the retention period expires. This meets SEC 17a-4 compliance.

- **B is wrong:** Soft delete allows recovery of deleted data but doesn't prevent deletion in the first place.
- **C is wrong:** Versioning keeps copies but doesn't prevent deletion of all versions.
- **D is wrong:** ACLs control access permissions but don't enforce immutability.

---

### Q8. Data Lake Design

A retail company needs a data lake for analytics. They ingest data from 20 sources, need to perform transformations, and serve curated data to Power BI. They need file-level access control and atomic directory operations. What should you recommend?

- A. Azure Data Lake Storage Gen2 (Blob Storage with hierarchical namespace)
- B. Standard Azure Blob Storage
- C. Azure Files Premium
- D. Azure Cosmos DB with analytical store

**Show Answer**

**Correct: A**

ADLS Gen2 provides hierarchical namespace (true directories with atomic rename/move), file-level POSIX ACLs, and is optimized for analytics workloads (Synapse, Spark, Data Factory integration). Same cost as standard Blob Storage.

- **B is wrong:** Standard Blob Storage has a flat namespace — no atomic directory operations, no file-level ACLs.
- **C is wrong:** Azure Files is for file shares (SMB/NFS), not analytics data lakes.
- **D is wrong:** Cosmos DB analytical store is for operational analytics on Cosmos data, not a general-purpose data lake.

---

### Q9. Data Integration

A company needs to ingest data from on-premises SQL Server and Salesforce into Azure Data Lake Gen2, transform it, load it into a Synapse dedicated pool, and visualize in Power BI. Which service should orchestrate this pipeline?

- A. Azure Data Factory with self-hosted integration runtime
- B. Azure Stream Analytics
- C. Azure Logic Apps
- D. Azure Functions with timer trigger

**Show Answer**

**Correct: A**

Data Factory is the purpose-built ETL/ELT orchestration service. Self-hosted integration runtime enables secure access to on-premises SQL Server. Built-in connectors for Salesforce, ADLS Gen2, and Synapse.

- **B is wrong:** Stream Analytics is for real-time streaming, not batch ETL orchestration.
- **C is wrong:** Logic Apps is for workflow automation, not data integration pipelines.
- **D is wrong:** Azure Functions can process data but lacks built-in connectors, monitoring, and pipeline orchestration features.

---

### Q10. Analytics Service Selection

A data science team needs to run Apache Spark notebooks for machine learning model training. They require collaborative notebooks, Delta Lake for reliable data processing, and MLflow for experiment tracking. What should you recommend?

- A. Azure Databricks
- B. Azure Synapse Spark pool
- C. Azure HDInsight
- D. Azure Machine Learning compute

**Show Answer**

**Correct: A**

Databricks provides the richest Spark experience with collaborative notebooks, native Delta Lake support, and integrated MLflow for experiment tracking — exactly matching the requirements.

- **B is wrong:** Synapse Spark is good for unified analytics but has more limited notebook collaboration and no native MLflow.
- **C is wrong:** HDInsight is open-source Hadoop/Spark but requires more management and lacks Delta Lake integration.
- **D is wrong:** Azure ML compute is for ML training/inference, not general Spark data engineering with Delta Lake.

---

## Scoring

- **Score**: 9-10 / 10 (90-100%) | **Next Step**: Excellent! Move to Module 3
- **Score**: 8 / 10 (80%) | **Next Step**: Good. Review missed questions, then move to Module 3
- **Score**: 6-7 / 10 (60-70%) | **Next Step**: Review the relevant lessons before proceeding
- **Score**: Below 6 / 10 (<60%) | **Next Step**: Re-study the full module before retaking

---

## Continue Learning

- **MS Learn Path:** [Design data storage solutions](https://learn.microsoft.com/training/paths/design-data-storage-solutions/)
- **Case Studies:** [Non-relational storage](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/04-Nonrelationalstorage.html) | [Relational storage](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/03-Relationalstorage.html)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Next:** [Module 3 — Business Continuity](../module-3-business-continuity/overview.md)


---

<a id="module-3-overview"></a>

## Module 3: Overview

# Module 3: Business Continuity & Disaster Recovery

**Estimated Duration:** 3-4 hours | **Exam Weight:** 15-20%

---

## Module Overview

Design solutions for backup, disaster recovery, and high availability that meet defined Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO).

---

## Domain Objectives Covered

- **#**: 3.1 | **Objective**: Design a solution for backup and disaster recovery
- **#**: 3.2 | **Objective**: Design for high availability

---

## Lessons

- **#**: 1 | **Lesson**: [Backup & Disaster Recovery](lesson-1-backup-dr.md) | **Duration**: 60 min | **Focus**: Azure Backup, ASR, RTO/RPO, geo-redundancy
- **#**: 2 | **Lesson**: [High Availability](lesson-2-high-availability.md) | **Duration**: 60 min | **Focus**: Availability zones, database HA, storage redundancy, SLAs

---

## Key Concepts to Master

- **Concept**: **RTO** (Recovery Time Objective) | **Why It Matters**: Maximum acceptable downtime
- **Concept**: **RPO** (Recovery Point Objective) | **Why It Matters**: Maximum acceptable data loss
- **Concept**: **Composite SLA** | **Why It Matters**: Calculate multi-service SLA
- **Concept**: **Availability Zones** | **Why It Matters**: Physical datacenter isolation
- **Concept**: **Active-Active vs. Active-Passive** | **Why It Matters**: Architecture pattern trade-offs

---

## Hands-On Labs

- **Lab**: Recovery Services Vault | **Template**: [recovery-services-vault.bicep](../../infra/recovery-services-vault.bicep) | **Purpose**: Azure Backup vault with policies
- **Lab**: Site Recovery | **Template**: [site-recovery-config.bicep](../../infra/site-recovery-config.bicep) | **Purpose**: ASR replication configuration
- **Lab**: SQL Failover Group | **Template**: [sql-failover-group.bicep](../../infra/sql-failover-group.bicep) | **Purpose**: Auto-failover for Azure SQL

---

## Architecture Diagrams

- [High Availability Patterns](../../images/high-availability-patterns.mmd)
- [Site Recovery DR](../../images/site-recovery-dr.mmd)
- [SQL HA/DR](../../images/sql-ha-dr.mmd)
- [Backup Architecture](../../images/backup-architecture.mmd)

---

## Exam Tips

- Questions often give you RTO/RPO numbers and ask you to select the cheapest/simplest solution that meets them
- Know the difference between Azure Backup and Azure Site Recovery
- Composite SLA calculation appears frequently — multiply individual SLAs
- Availability Zones provide 99.99% SLA vs. Availability Sets at 99.95%
- Database HA options vary by service (SQL auto-failover groups, Cosmos DB multi-region)

---

## Knowledge Check

Complete the [Module 3 Knowledge Check](knowledge-check.md) before moving on.

**Target:** 80%+ (8/10 correct)

---

## Official Microsoft Resources

### MS Learn Path
[AZ-305: Design business continuity solutions](https://learn.microsoft.com/training/paths/design-business-continuity-solutions/) (1 hr 46 min, 2 modules)
- [Describe high availability and disaster recovery strategies](https://learn.microsoft.com/training/modules/describe-high-availability-disaster-recovery-strategies/) (59 min)
- [Design a solution for backup and disaster recovery](https://learn.microsoft.com/training/modules/design-solution-for-backup-disaster-recovery/) (47 min)

### Case Studies
There is no formal case study for business continuity in the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/). Use the Bicep labs above and practice assessment to reinforce this domain.

### Practice Assessment
[Take the free AZ-305 practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) — business continuity questions make up 15-20% of the exam.


---

<a id="module-3-lesson-1---backup-and-disaster-recovery"></a>

## Module 3: Lesson 1 - Backup and Disaster Recovery

# Lesson 1: Backup & Disaster Recovery

**Duration:** 60 minutes | **Domain Weight:** Part of 15-20%

---

## Learning Objectives

- Recommend a recovery solution for Azure (hybrid and multi-cloud) workloads
- Design an Azure Site Recovery solution
- Design a solution for recovery in different regions
- Design an Azure backup solution
- Design for data protection (retention, encryption, immutability)

---

## 1. RTO and RPO Fundamentals

### Definitions

- **Metric**: **RTO** (Recovery Time Objective) | **Definition**: Maximum acceptable downtime | **Question It Answers**: "How long can you be down?"
- **Metric**: **RPO** (Recovery Point Objective) | **Definition**: Maximum acceptable data loss | **Question It Answers**: "How much data can you lose?"

### Mapping Requirements to Solutions

- **RTO / RPO**: RTO: hours, RPO: 24h | **Solution Tier**: Basic | **Example Services**: Azure Backup, geo-restore
- **RTO / RPO**: RTO: minutes, RPO: hours | **Solution Tier**: Standard | **Example Services**: Azure Site Recovery, SQL PITR
- **RTO / RPO**: RTO: seconds, RPO: ~0 | **Solution Tier**: Premium | **Example Services**: Active-active, synchronous replication

[Diagram removed for audio]

---

## 2. Azure Backup

### What Can Azure Backup Protect?

- **Workload**: **Azure VMs** | **Agent / Method**: VM backup extension | **Backup Frequency**: Daily
- **Workload**: **SQL Server in VM** | **Agent / Method**: SQL backup extension | **Backup Frequency**: Full: daily; Log: every 15 min
- **Workload**: **Azure Files** | **Agent / Method**: Share snapshot | **Backup Frequency**: Daily
- **Workload**: **Azure Blobs** | **Agent / Method**: Operational/vaulted backup | **Backup Frequency**: Continuous / daily
- **Workload**: **Azure Database for PostgreSQL** | **Agent / Method**: Vaulted backup | **Backup Frequency**: Daily with log backup
- **Workload**: **SAP HANA in VM** | **Agent / Method**: HANA backup extension | **Backup Frequency**: Full: daily; Log: every 15 min
- **Workload**: **Azure Managed Disks** | **Agent / Method**: Disk backup | **Backup Frequency**: Hourly/daily

### Recovery Services Vault vs. Backup Vault

- **Feature**: Supports | **Recovery Services Vault**: VMs, SQL in VM, SAP HANA, Files, MARS | **Backup Vault**: Blobs, Disks, PostgreSQL
- **Feature**: Soft delete | **Recovery Services Vault**: 14 days (extendable) | **Backup Vault**: 14 days (extendable)
- **Feature**: Cross-region restore | **Recovery Services Vault**: Yes (GRS vaults) | **Backup Vault**: Some workloads
- **Feature**: Immutable vaults | **Recovery Services Vault**: Yes | **Backup Vault**: Yes

### Backup Redundancy

- **Option**: **LRS** | **Protection**: 3 copies, single location | **Exam Use Case**: Cost-sensitive, low criticality
- **Option**: **ZRS** | **Protection**: 3 copies across zones | **Exam Use Case**: Zone resilience
- **Option**: **GRS** | **Protection**: 6 copies, paired region | **Exam Use Case**: Regional disaster recovery

### Immutable Vaults

Prevents backup deletion or shortening retention — critical for ransomware protection:
- **Soft delete:** Always-on, 14+ days recovery window
- **Immutable vault:** Cannot disable backup or reduce retention once locked
- **Multi-user authorization:** Requires Resource Guard approval for destructive operations

---

## 3. Azure Site Recovery (ASR)

### What It Does

ASR provides disaster recovery by replicating VMs and physical servers to a secondary Azure region (or from on-premises to Azure).

### Supported Scenarios

- **Source**: Azure VM (Region A) | **Destination**: Azure VM (Region B) | **Use Case**: Azure-to-Azure DR
- **Source**: On-premises VMware | **Destination**: Azure | **Use Case**: Cloud migration / DR
- **Source**: On-premises Hyper-V | **Destination**: Azure | **Use Case**: Cloud migration / DR
- **Source**: Physical servers | **Destination**: Azure | **Use Case**: Legacy server DR

### Key Components

- **Component**: **Replication policy** | **Purpose**: Defines RPO, recovery point retention, app-consistent snapshots
- **Component**: **Recovery plan** | **Purpose**: Orchestrates failover sequence, groups VMs, includes scripts
- **Component**: **Test failover** | **Purpose**: Non-disruptive DR drill in isolated network
- **Component**: **Failover** | **Purpose**: Actual cutover to secondary region
- **Component**: **Failback** | **Purpose**: Return to primary after outage resolved

### RPO and Recovery Points

- **Type**: **Crash-consistent** | **Frequency**: Every 5 minutes (default RPO) | **Use Case**: VM state at point in time
- **Type**: **App-consistent** | **Frequency**: Configurable (1-12 hours) | **Use Case**: Consistent application state (VSS)

### Recovery Plans

[Diagram removed for audio]

---

## 4. Service-Specific DR Options

### Azure SQL Database DR

- **Feature**: **Point-in-time restore** | **Description**: Restore to any second within retention | **RTO**: Minutes-hours | **RPO**: Seconds
- **Feature**: **Geo-restore** | **Description**: Restore from GRS backup to any region | **RTO**: Hours | **RPO**: Up to 1 hour
- **Feature**: **Active geo-replication** | **Description**: Async replica in any region (up to 4) | **RTO**: Seconds | **RPO**: <5 seconds
- **Feature**: **Auto-failover groups** | **Description**: Automatic failover with DNS endpoint | **RTO**: 30 seconds | **RPO**: <5 seconds

### Decision Matrix

[Diagram removed for audio]

### Cosmos DB DR

- **Configuration**: Multi-region writes | **RPO**: ~0 | **How**: Synchronous within region, auto-failover
- **Configuration**: Single-region write + multi-region read | **RPO**: Seconds | **How**: Automatic regional failover
- **Configuration**: Service-managed failover | **RPO**: Minutes | **How**: Azure handles failover

### Storage Account DR

- **Feature**: **GRS/GZRS** | **Description**: Async replication to paired region
- **Feature**: **RA-GRS/RA-GZRS** | **Description**: Read access during outage
- **Feature**: **Customer-managed failover** | **Description**: Initiate storage failover manually
- **Feature**: **Object replication** | **Description**: Async copy to another storage account (any region)

---

## 5. Multi-Region Architecture Patterns

### Active-Passive

[Diagram removed for audio]

### Active-Active

[Diagram removed for audio]

- **Pattern**: Active-Passive (cold) | **RTO**: Hours | **Cost**: $ | **Complexity**: Low | **Exam Keyword**: "Minimize cost"
- **Pattern**: Active-Passive (warm) | **RTO**: Minutes | **Cost**: $$ | **Complexity**: Medium | **Exam Keyword**: "Balance cost and RTO"
- **Pattern**: Active-Active | **RTO**: Seconds | **Cost**: $$$ | **Complexity**: High | **Exam Keyword**: "Minimize downtime"

---

## Summary Decision Matrix

- **Scenario**: VM disaster recovery | **Solution**: Azure Site Recovery
- **Scenario**: SQL Database auto-failover | **Solution**: Auto-failover groups
- **Scenario**: Protect against ransomware | **Solution**: Immutable vault + soft delete
- **Scenario**: VM/file backup | **Solution**: Recovery Services Vault
- **Scenario**: Blob backup | **Solution**: Backup Vault
- **Scenario**: On-prem to Azure DR | **Solution**: ASR with VMware/Hyper-V
- **Scenario**: Multi-region, zero downtime | **Solution**: Active-active with Cosmos DB
- **Scenario**: RTO: hours, RPO: daily | **Solution**: Azure Backup + geo-restore

---

## Next Steps

- **Lab:** Deploy [recovery-services-vault.bicep](../../infra/recovery-services-vault.bicep)
- **Lab:** Deploy [site-recovery-config.bicep](../../infra/site-recovery-config.bicep)
- **Continue:** [Lesson 2 — High Availability](lesson-2-high-availability.md)

---

## References

- [Azure Backup Overview](https://learn.microsoft.com/azure/backup/backup-overview)
- [Azure Site Recovery Overview](https://learn.microsoft.com/azure/site-recovery/site-recovery-overview)
- [SQL Auto-Failover Groups](https://learn.microsoft.com/azure/azure-sql/database/auto-failover-group-overview)
- [Business Continuity Overview](https://learn.microsoft.com/azure/architecture/framework/resiliency/business-metrics)


---

<a id="module-3-lesson-2---high-availability"></a>

## Module 3: Lesson 2 - High Availability

# Lesson 2: High Availability

**Duration:** 60 minutes | **Domain Weight:** Part of 15-20%

---

## Learning Objectives

- Identify the SLA requirements for a solution
- Recommend a solution for compute, storage, and database high availability
- Recommend a solution for Azure availability zones and multi-region deployments
- Calculate composite SLAs

---

## 1. SLA Fundamentals

### Azure SLA Tiers

- **SLA**: 99% | **Monthly Downtime**: 7.31 hours | **Annual Downtime**: 3.65 days | **Achievable With**: Basic single instance
- **SLA**: 99.9% | **Monthly Downtime**: 43.8 minutes | **Annual Downtime**: 8.76 hours | **Achievable With**: Single instance with SSD
- **SLA**: 99.95% | **Monthly Downtime**: 21.9 minutes | **Annual Downtime**: 4.38 hours | **Achievable With**: Availability Set
- **SLA**: 99.99% | **Monthly Downtime**: 4.38 minutes | **Annual Downtime**: 52.6 minutes | **Achievable With**: Availability Zones
- **SLA**: 99.999% | **Monthly Downtime**: 26.3 seconds | **Annual Downtime**: 5.26 minutes | **Achievable With**: Multi-region active-active

### Composite SLA Calculation

When services are **chained** (all must work): **multiply** SLAs.

[Diagram removed for audio]

When services are **redundant** (either can work): use complement formula.

[Diagram removed for audio]

**Exam Trap:** Composite SLA is always **lower** than the lowest individual SLA for chained dependencies (unless you add redundancy).

---

## 2. Compute High Availability

### Availability Options

- **Feature**: **Single VM (Premium SSD)** | **What It Protects Against**: Hardware failure (limited) | **SLA**: 99.9% | **Best For**: Dev/test
- **Feature**: **Availability Set** | **What It Protects Against**: Rack-level failure (FD+UD) | **SLA**: 99.95% | **Best For**: Legacy apps
- **Feature**: **Availability Zones** | **What It Protects Against**: Datacenter failure | **SLA**: 99.99% | **Best For**: Production workloads
- **Feature**: **VMSS across zones** | **What It Protects Against**: Datacenter failure + scaling | **SLA**: 99.99% | **Best For**: Auto-scaling workloads
- **Feature**: **Multi-region** | **What It Protects Against**: Regional outage | **SLA**: ~99.99%+ | **Best For**: Mission-critical

### Availability Sets Explained

[Diagram removed for audio]

- **Component**: **Fault Domain (FD)** | **Purpose**: Separate power/network rack | **Max Count**: 3 (most regions)
- **Component**: **Update Domain (UD)** | **Purpose**: Rolling update groups | **Max Count**: 20

### Availability Zones Explained

[Diagram removed for audio]

**Exam Rule:** Availability Zones > Availability Sets for new deployments (99.99% vs. 99.95%).

### PaaS Compute HA

- **Service**: App Service | **Zone-Redundant Option**: Zone-redundant plan (Premium+ v3) | **Multi-Region Option**: Traffic Manager / Front Door
- **Service**: Container Apps | **Zone-Redundant Option**: Zone-redundant environment | **Multi-Region Option**: Traffic Manager / Front Door
- **Service**: AKS | **Zone-Redundant Option**: Zone-redundant node pools | **Multi-Region Option**: Multi-cluster with Front Door
- **Service**: Azure Functions | **Zone-Redundant Option**: Zone-redundant (Premium plan) | **Multi-Region Option**: Traffic Manager / Front Door

---

## 3. Database High Availability

### Azure SQL Database HA

- **Tier**: **General Purpose** | **HA Model**: Remote storage, zone-redundant option | **RPO**: ~10 sec failover | **Auto-Failover**: Within region
- **Tier**: **Business Critical** | **HA Model**: Always On AG (local replicas), zone-redundant | **RPO**: 0 (sync) | **Auto-Failover**: Within region
- **Tier**: **Hyperscale** | **HA Model**: Multi-replica, zone-redundant | **RPO**: 0 (sync) | **Auto-Failover**: Within region

For **cross-region HA:**

- **Feature**: Zone redundancy | **Same Region**: Built-in HA | **Cross Region**: N/A
- **Feature**: Active geo-replication | **Same Region**: N/A | **Cross Region**: Manual failover
- **Feature**: Auto-failover groups | **Same Region**: N/A | **Cross Region**: Automatic DNS failover

### Cosmos DB HA

- **Configuration**: Single region | **SLA**: 99.99% | **Writes**: Single region | **Reads**: Single region
- **Configuration**: Multi-region read | **SLA**: 99.99% write, 99.999% read | **Writes**: Single region | **Reads**: All regions
- **Configuration**: Multi-region write | **SLA**: 99.999% | **Writes**: All regions | **Reads**: All regions
- **Configuration**: + Availability Zones | **SLA**: Further protection | **Writes**: Zone-redundant | **Reads**: Zone-redundant

### Azure Cache for Redis HA

- **Tier**: Basic | **HA**: None | **Cross-Region**: No
- **Tier**: Standard | **HA**: 2 replicas | **Cross-Region**: No
- **Tier**: Premium | **HA**: Cluster + zonal | **Cross-Region**: Geo-replication (active-passive)
- **Tier**: Enterprise | **HA**: Active-active geo-replication | **Cross-Region**: Active-active across regions

---

## 4. Storage High Availability

### Redundancy Revisited (HA Perspective)

- **Scenario**: Survive disk failure | **Minimum Redundancy**: LRS | **Why**: 3 copies, same datacenter
- **Scenario**: Survive zone failure | **Minimum Redundancy**: ZRS | **Why**: 3 copies across 3 zones
- **Scenario**: Survive regional failure | **Minimum Redundancy**: GRS/GZRS | **Why**: Copies in paired region
- **Scenario**: Read during regional failure | **Minimum Redundancy**: RA-GRS/RA-GZRS | **Why**: Read from secondary

### Storage Failover

- **Type**: **Microsoft-managed** | **Initiated By**: Microsoft (major disaster) | **RPO**: Hours | **Considerations**: Rare, last resort
- **Type**: **Customer-managed** | **Initiated By**: Customer | **RPO**: Data since last sync | **Considerations**: Secondary becomes primary, may lose recent writes

**Exam Trap:** After customer-managed failover, storage becomes LRS in the new primary region. You must re-configure geo-replication.

---

## 5. Network High Availability

### Load Balancer Options for HA

- **Service**: **Azure Load Balancer** | **Scope**: Regional | **Layer**: L4 (TCP/UDP) | **Best For**: VM/VMSS within region
- **Service**: **Application Gateway** | **Scope**: Regional | **Layer**: L7 (HTTP/HTTPS) | **Best For**: Web apps, WAF, SSL offload
- **Service**: **Traffic Manager** | **Scope**: Global | **Layer**: DNS-based | **Best For**: Multi-region failover
- **Service**: **Azure Front Door** | **Scope**: Global | **Layer**: L7 (HTTP/HTTPS) | **Best For**: Global web apps, CDN, WAF
- **Service**: **Cross-region Load Balancer** | **Scope**: Global | **Layer**: L4 | **Best For**: Multi-region L4

### Multi-Region Load Balancing Decision

[Diagram removed for audio]

---

## 6. Designing for Target SLA

### Step-by-Step Process

1. **Define business RTO/RPO** — What's acceptable?
2. **Calculate composite SLA** — Multiply chained service SLAs
3. **Identify the weakest link** — Which service drags the SLA down?
4. **Add redundancy** — Zones, replicas, or multi-region to strengthen weak links
5. **Recalculate** — Verify composite SLA meets requirement
6. **Test regularly** — DR drills, chaos engineering

### Example: Web App with SQL Backend

- **Configuration**: App Service (99.95%) × SQL (99.99%) | **Composite SLA**: 99.94%
- **Configuration**: + Zone-redundant App Service (99.99%) | **Composite SLA**: 99.98%
- **Configuration**: + Multi-region with Front Door (99.99%) + failover | **Composite SLA**: ~99.9999%

---

## Summary Decision Matrix

- **Requirement**: Protect against rack failure | **Solution**: Availability Set (99.95%)
- **Requirement**: Protect against datacenter failure | **Solution**: Availability Zones (99.99%)
- **Requirement**: Protect against regional outage | **Solution**: Multi-region deployment
- **Requirement**: SQL cross-region auto-failover | **Solution**: Auto-failover groups
- **Requirement**: Global HTTP load balancing + CDN | **Solution**: Azure Front Door
- **Requirement**: Global any-protocol failover | **Solution**: Traffic Manager
- **Requirement**: Storage read during regional outage | **Solution**: RA-GRS or RA-GZRS
- **Requirement**: Cosmos DB highest SLA | **Solution**: Multi-region writes + zones
- **Requirement**: Calculate composite SLA | **Solution**: Multiply chained, complement for redundant

---

## Next Steps

- **Lab:** Deploy [sql-failover-group.bicep](../../infra/sql-failover-group.bicep)
- **Lab:** Review [high-availability-patterns.mmd](../../images/high-availability-patterns.mmd)
- **Knowledge Check:** [Module 3 Knowledge Check](knowledge-check.md)

---

## References

- [Azure SLA Summary](https://azure.microsoft.com/support/legal/sla/summary/)
- [Availability Zones](https://learn.microsoft.com/azure/reliability/availability-zones-overview)
- [Composite SLA](https://learn.microsoft.com/azure/architecture/framework/resiliency/business-metrics)
- [Front Door Overview](https://learn.microsoft.com/azure/frontdoor/front-door-overview)


---

<a id="module-3-knowledge-check"></a>

## Module 3: Knowledge Check

# Module 3 Knowledge Check: Business Continuity & Disaster Recovery

**Target Score:** 80%+ before moving to Module 4

---

## Instructions

Choose the BEST answer for each scenario. Pay close attention to RTO, RPO, and cost requirements.

---

### Q1. RTO/RPO Requirements

A financial services company requires an RTO of 30 seconds and RPO of near zero for their web application and database. What architecture should you recommend?

- A. Azure Backup with geo-restore
- B. Azure Site Recovery with 5-minute RPO
- C. Active-active deployment across two regions with Cosmos DB multi-region writes
- D. Active-passive with SQL auto-failover groups

**Show Answer**

**Correct: C**

Active-active deployment with Cosmos DB multi-region writes provides near-zero RPO (synchronous within region) and near-instant failover (RTO ~seconds). Both regions serve traffic simultaneously.

- **A is wrong:** Backup + geo-restore has RTO of hours and RPO of up to 24 hours.
- **B is wrong:** ASR provides 5-minute RPO and RTO of minutes — doesn't meet 30-second RTO.
- **D is wrong:** Auto-failover groups have ~30-second RTO but this is active-passive, not the lowest RTO option. However, the 30-second RTO requirement combined with near-zero RPO points to active-active as the best solution.

---

### Q2. Azure Backup

A company needs to back up Azure VMs and SQL Server databases running on Azure VMs. They need 7-year retention for compliance and the ability to restore in a different region if the primary region fails. What should you configure?

- A. Recovery Services Vault with GRS and long-term retention policy
- B. Backup Vault with LRS
- C. Azure Site Recovery with 7-year retention
- D. Storage account with blob versioning

**Show Answer**

**Correct: A**

Recovery Services Vault supports both Azure VMs and SQL in VMs. GRS provides cross-region restore capability. Long-term retention policies support up to 10 years.

- **B is wrong:** Backup Vault supports blobs and disks, not VMs or SQL. LRS doesn't enable cross-region restore.
- **C is wrong:** ASR is for disaster recovery (replication), not long-term backup retention.
- **D is wrong:** Blob versioning is for blob data, not VM or SQL backups, and doesn't provide structured backup management.

---

### Q3. Azure Site Recovery

A company runs a 3-tier application on Azure VMs. They need to ensure the VMs start in the correct order during DR failover: database first, then application servers, then web servers. What ASR feature should you use?

- A. Replication policy with app-consistent snapshots
- B. Recovery plan with groups and sequenced actions
- C. Automation runbook triggered by Azure Monitor
- D. Availability set with fault domains

**Show Answer**

**Correct: B**

Recovery plans allow you to group VMs and define startup order. Group 1 (database), Group 2 (app tier), Group 3 (web tier) with pre/post scripts between groups.

- **A is wrong:** Replication policy controls RPO and snapshot frequency, not failover sequencing.
- **C is wrong:** Runbooks can be part of a recovery plan but don't define VM startup order by themselves.
- **D is wrong:** Availability sets provide rack-level redundancy, not DR failover sequencing.

---

### Q4. Composite SLA

An application uses App Service (99.95% SLA), Azure SQL (99.99% SLA), and Azure Cache for Redis Standard (99.9% SLA) in a chain. What is the composite SLA?

- A. 99.99%
- B. 99.95%
- C. 99.84%
- D. 99.9%

**Show Answer**

**Correct: C**

Composite SLA = 0.9995 × 0.9999 × 0.999 = 0.99840 = **99.84%**

For chained services, multiply individual SLAs. The result is always lower than the lowest individual SLA.

- **A is wrong:** You can't exceed the lowest individual SLA (99.9%) without redundancy.
- **B is wrong:** That's just the App Service SLA — you must account for all dependencies.
- **D is wrong:** That's just the Redis SLA.

---

### Q5. Availability Zones

A company is deploying a new production application and needs the highest availability within a single region. The application uses VMs and requires a 99.99% SLA. What deployment model should you recommend?

- A. Single VM with Premium SSD
- B. VMs in an Availability Set
- C. VMs across Availability Zones
- D. VMs in a Virtual Machine Scale Set (single zone)

**Show Answer**

**Correct: C**

Availability Zones provide 99.99% SLA by distributing VMs across physically separate datacenters within a region.

- **A is wrong:** Single VM with Premium SSD provides only 99.9% SLA.
- **B is wrong:** Availability Sets provide 99.95% SLA (rack-level, not datacenter-level).
- **D is wrong:** VMSS in a single zone doesn't protect against datacenter failure.

---

### Q6. SQL Database DR

A company has an Azure SQL Database that serves users in East US and West Europe. They need automatic failover if East US goes down, with a single connection endpoint that doesn't change after failover. What should you recommend?

- A. Active geo-replication
- B. Auto-failover groups
- C. Point-in-time restore
- D. Geo-restore from GRS backup

**Show Answer**

**Correct: B**

Auto-failover groups provide automatic failover with a stable DNS endpoint (e.g., `myserver-group.database.windows.net`) that doesn't change after failover. Applications don't need connection string changes.

- **A is wrong:** Active geo-replication provides readable replicas but requires manual failover and connection string changes.
- **C is wrong:** PITR restores to a point in time, doesn't provide automatic cross-region failover.
- **D is wrong:** Geo-restore creates a new database from GRS backup — slow (hours) and requires connection string changes.

---

### Q7. Storage Redundancy for HA

An application reads blobs from Azure Storage. During a regional outage, the application must continue reading blobs without waiting for Microsoft to initiate a failover. What redundancy should you recommend?

- A. GRS
- B. ZRS
- C. RA-GRS
- D. LRS

**Show Answer**

**Correct: C**

RA-GRS (Read-Access Geo-Redundant Storage) provides a secondary read endpoint that is accessible even during a primary region outage. The application can read from `*.secondary.blob.core.windows.net` immediately.

- **A is wrong:** GRS replicates to a paired region, but data is not accessible until Microsoft or customer initiates failover.
- **B is wrong:** ZRS protects against zone failure, not regional failure.
- **D is wrong:** LRS provides no cross-region protection.

---

### Q8. Ransomware Protection

A company experienced a ransomware attack that encrypted their files and attempted to delete their Azure Backups. What features should you enable to protect backup data from deletion? (Choose the best combination)

- A. Soft delete + Immutable vault + Multi-user authorization
- B. Geo-redundant storage only
- C. Azure Site Recovery with daily snapshots
- D. Storage account firewall rules

**Show Answer**

**Correct: A**

This combination provides defense-in-depth for backup data:
- **Soft delete:** Retains deleted backup data for 14+ days
- **Immutable vault:** Prevents disabling backup or reducing retention periods
- **Multi-user authorization (Resource Guard):** Requires additional approval for destructive operations

- **B is wrong:** GRS replicates backups across regions but doesn't prevent deletion.
- **C is wrong:** ASR is for VM replication, not backup protection.
- **D is wrong:** Firewall rules control network access but don't prevent authorized users from deleting backups.

---

### Q9. Multi-Region Architecture

A company wants to deploy their web application across two Azure regions. They want traffic routed to the closest region and must have WAF protection and built-in CDN capabilities. What should you use as the global load balancer?

- A. Azure Traffic Manager
- B. Azure Front Door
- C. Azure Load Balancer (Standard)
- D. Azure Application Gateway

**Show Answer**

**Correct: B**

Azure Front Door provides global HTTP/HTTPS load balancing with built-in CDN, WAF, and proximity-based routing. It operates at Layer 7 with edge POP locations worldwide.

- **A is wrong:** Traffic Manager does DNS-based routing but has no WAF or CDN capabilities.
- **C is wrong:** Load Balancer is regional (Layer 4), not global.
- **D is wrong:** Application Gateway is regional (Layer 7), not global.

---

### Q10. Cosmos DB HA

A global e-commerce platform needs the highest possible availability SLA from Cosmos DB while serving both reads and writes from multiple regions. What should you configure?

- A. Single-region Cosmos DB with automatic failover
- B. Multi-region read replicas (single-write region)
- C. Multi-region writes with availability zones enabled
- D. Serverless Cosmos DB with geo-replication

**Show Answer**

**Correct: C**

Multi-region writes with availability zones provides the highest Cosmos DB SLA (99.999% for both reads and writes). Each region can accept writes, and zones protect against datacenter failure.

- **A is wrong:** Single region provides 99.99% SLA, lower than multi-region write (99.999%).
- **B is wrong:** Multi-region read gives 99.999% read SLA but only 99.99% write SLA (single write region).
- **D is wrong:** Serverless mode doesn't support multi-region writes or geo-replication.

---

## Scoring

- **Score**: 9-10 / 10 (90-100%) | **Next Step**: Excellent! Move to Module 4
- **Score**: 8 / 10 (80%) | **Next Step**: Good. Review missed questions, then move to Module 4
- **Score**: 6-7 / 10 (60-70%) | **Next Step**: Review the relevant lessons before proceeding
- **Score**: Below 6 / 10 (<60%) | **Next Step**: Re-study the full module before retaking

---

## Continue Learning

- **MS Learn Path:** [Design business continuity solutions](https://learn.microsoft.com/training/paths/design-business-continuity-solutions/)
  - [Describe high availability and disaster recovery strategies](https://learn.microsoft.com/training/modules/describe-high-availability-disaster-recovery-strategies/)
  - [Design a solution for backup and disaster recovery](https://learn.microsoft.com/training/modules/design-solution-for-backup-disaster-recovery/)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Next:** [Module 4 — Infrastructure & Compute](../module-4-compute-apps/overview.md)


---

<a id="module-4-overview"></a>

## Module 4: Overview

# Module 4: Infrastructure & Compute Solutions

**Estimated Duration:** 4-5 hours | **Exam Weight:** 30-35%

---

## Module Overview

Design compute, application architecture, and migration solutions. This is the **heaviest-weighted domain** on the AZ-305 exam.

---

## Domain Objectives Covered

- **#**: 4.1 | **Objective**: Design a compute solution
- **#**: 4.2 | **Objective**: Design an application architecture
- **#**: 4.3 | **Objective**: Design migrations

---

## Lessons

- **#**: 1 | **Lesson**: [Compute Solutions](lesson-1-compute.md) | **Duration**: 60 min | **Focus**: VMs, Container Apps, AKS, Functions, App Service
- **#**: 2 | **Lesson**: [Application Architecture](lesson-2-app-architecture.md) | **Duration**: 60 min | **Focus**: Messaging, caching, APIM, App Config, microservices
- **#**: 3 | **Lesson**: [Migrations](lesson-3-migrations.md) | **Duration**: 45 min | **Focus**: Cloud Adoption Framework, migration tools, strategies

---

## Key Concepts to Master

- **Concept**: **Compute decision tree** | **Why It Matters**: Most common exam pattern — pick the right compute service
- **Concept**: **Messaging services** | **Why It Matters**: Service Bus vs. Event Grid vs. Event Hubs
- **Concept**: **API Management** | **Why It Matters**: Policies, tiers, security
- **Concept**: **Migration strategies** | **Why It Matters**: 5 Rs (Rehost, Refactor, Rearchitect, Rebuild, Replace)
- **Concept**: **Landing zones** | **Why It Matters**: CAF-aligned migration patterns

---

## Hands-On Labs

- **Lab**: Container Apps | **Template**: [container-apps-environment.bicep](../../infra/container-apps-environment.bicep) | **Purpose**: Serverless containers
- **Lab**: AKS | **Template**: [aks-cluster.bicep](../../infra/aks-cluster.bicep) | **Purpose**: Managed Kubernetes
- **Lab**: API Management | **Template**: [apim-with-backends.bicep](../../infra/apim-with-backends.bicep) | **Purpose**: API gateway with policies

---

## Architecture Diagrams

- [Container Apps Microservices](../../images/container-apps-microservices.mmd)
- [API Architecture](../../images/api-architecture.mmd)
- [Migration Landing Zone](../../images/migration-landing-zone.mmd)

---

## Exam Tips

- This domain is 30-35% of the exam — invest the most study time here
- Compute selection questions often hinge on requirements like OS-level access, event-driven triggers, or container orchestration
- Messaging service selection: know the difference between commands (Service Bus) and events (Event Grid/Event Hubs)
- Migration questions test CAF phases and the 5 Rs — know when to choose each strategy
- API Management tier selection is common — focus on VNet integration (Developer/Premium) and consumption pricing

---

## Knowledge Check

Complete the [Module 4 Knowledge Check](knowledge-check.md) before moving on.

**Target:** 80%+ (8/10 correct)

---

## Official Microsoft Resources

### MS Learn Path
[AZ-305: Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/) (3 hr 39 min, 4 modules)
- [Design an Azure compute solution](https://learn.microsoft.com/training/modules/design-compute-solution/) (1 hr 1 min)
- [Design an application architecture](https://learn.microsoft.com/training/modules/design-application-architecture/) (59 min)
- [Design network solutions](https://learn.microsoft.com/training/modules/design-network-solutions/) (53 min) — also covered in Module 5
- [Design migrations](https://learn.microsoft.com/training/modules/design-migrations/) (46 min)

### Case Studies
Complete these scenario-based exercises from the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):
- [Design a compute solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/02-Compute.html)
- [Design an app architecture solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/05-Apparchitecture.html)

### Practice Assessment
[Take the free AZ-305 practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) — infrastructure questions make up 30-35% of the exam (heaviest weighted).


---

<a id="module-4-lesson-1---compute-solutions"></a>

## Module 4: Lesson 1 - Compute Solutions

# Lesson 1: Compute Solutions

**Duration:** 60 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a solution for compute (VMs, App Service, Container Apps, AKS, Functions)
- Specify components of a compute solution based on requirements
- Recommend a solution for containers and serverless computing

---

## 1. Compute Service Decision Tree

This is the **most important decision framework** for AZ-305 exam questions.

[Diagram removed for audio]

### Compute Service Comparison

- **Service**: **Virtual Machines** | **Model**: IaaS | **Scaling**: Manual/VMSS | **OS Access**: Full | **Best For**: Legacy, custom software
- **Service**: **App Service** | **Model**: PaaS | **Scaling**: Auto-scale rules | **OS Access**: No | **Best For**: Web apps, REST APIs
- **Service**: **Container Apps** | **Model**: Serverless containers | **Scaling**: KEDA/HTTP auto-scale | **OS Access**: No | **Best For**: Microservices, event-driven containers
- **Service**: **AKS** | **Model**: Managed K8s | **Scaling**: Cluster/pod autoscaler | **OS Access**: Node-level | **Best For**: Complex orchestration, K8s expertise
- **Service**: **Azure Functions** | **Model**: FaaS | **Scaling**: Consumption (auto) | **OS Access**: No | **Best For**: Event-driven, glue logic
- **Service**: **Azure Container Instances** | **Model**: CaaS | **Scaling**: None (per-container) | **OS Access**: No | **Best For**: Burst, batch, sidecar
- **Service**: **Azure Batch** | **Model**: Managed HPC | **Scaling**: Pool auto-scale | **OS Access**: Node-level | **Best For**: Parallel/HPC workloads

---

## 2. Virtual Machines

### VM Size Categories

- **Category**: General purpose | **Prefix**: B, D | **Use Case**: Balanced CPU/memory, dev/test, web servers
- **Category**: Compute optimized | **Prefix**: F | **Use Case**: CPU-intensive (batch, gaming, analytics)
- **Category**: Memory optimized | **Prefix**: E, M | **Use Case**: Databases, in-memory analytics
- **Category**: Storage optimized | **Prefix**: L | **Use Case**: Big data, SQL/NoSQL databases
- **Category**: GPU | **Prefix**: N | **Use Case**: ML training, rendering, video
- **Category**: HPC | **Prefix**: H | **Use Case**: High-performance compute

### VM Scaling Options

- **Feature**: **Vertical scaling** | **What**: Change VM size | **When**: Need more CPU/RAM (requires restart)
- **Feature**: **VMSS (Uniform)** | **What**: Identical VM pool | **When**: Web tier, auto-scale by metrics
- **Feature**: **VMSS (Flexible)** | **What**: Mixed VM sizes | **When**: High availability, different SKUs

### Exam Keyword Mapping

- **Exam Phrase**: "Requires OS-level access" | **Service**: VM
- **Exam Phrase**: "Install custom device drivers" | **Service**: VM (GPU if needed)
- **Exam Phrase**: "Lift and shift without changes" | **Service**: VM
- **Exam Phrase**: "Run third-party licensed software" | **Service**: VM

---

## 3. Azure App Service

### Key Features

- **Feature**: Languages | **Details**: .NET, Java, Node.js, Python, PHP, Ruby
- **Feature**: Deployment | **Details**: Git, CI/CD, ZIP, Docker container
- **Feature**: Scaling | **Details**: Auto-scale (rule-based or automatic)
- **Feature**: SSL/Custom domain | **Details**: Built-in, App Service managed certificates (free)
- **Feature**: Deployment slots | **Details**: Staging with swap (Standard+ tiers)

### Plan Tiers

- **Tier**: **Free / Shared** | **Key Feature**: No SLA, shared infra | **Exam Use Case**: Dev/test only
- **Tier**: **Basic** | **Key Feature**: Dedicated compute, no auto-scale | **Exam Use Case**: Simple production
- **Tier**: **Standard** | **Key Feature**: Auto-scale, deployment slots | **Exam Use Case**: Standard production
- **Tier**: **Premium v3** | **Key Feature**: Enhanced compute, VNet integration, zone redundancy | **Exam Use Case**: High-performance, private networking
- **Tier**: **Isolated v2** | **Key Feature**: ASE (App Service Environment), dedicated VNet | **Exam Use Case**: Full network isolation, compliance

### Exam Decision Points

- **Requirement**: "VNet integration" | **Tier**: Premium v3 or Isolated
- **Requirement**: "Complete network isolation" | **Tier**: Isolated v2 (ASE)
- **Requirement**: "Zone-redundant" | **Tier**: Premium v3
- **Requirement**: "Deployment slots for blue-green" | **Tier**: Standard+

---

## 4. Azure Container Apps

### When to Use Container Apps

- Microservices without K8s management overhead
- HTTP APIs and background workers
- Event-driven processing (KEDA scalers)
- Jobs (scheduled or event-driven batch)

### Key Features

- **Feature**: Container runtime | **Details**: Any Linux container
- **Feature**: Scaling | **Details**: HTTP-based, KEDA event triggers, scheduled
- **Feature**: Scale to zero | **Details**: Yes (Consumption plan)
- **Feature**: Built-in | **Details**: Dapr, service discovery, traffic splitting
- **Feature**: Revisions | **Details**: Multiple versions with traffic control
- **Feature**: Networking | **Details**: Internal (VNet) or external

### Container Apps vs. AKS

- **Factor**: K8s knowledge required | **Container Apps**: No | **AKS**: Yes
- **Factor**: Scale to zero | **Container Apps**: Yes | **AKS**: No (minimum 1 node)
- **Factor**: Management overhead | **Container Apps**: Low | **AKS**: High
- **Factor**: Customization | **Container Apps**: Limited (opinionated) | **AKS**: Full K8s control
- **Factor**: Cost for variable workloads | **Container Apps**: Lower (consumption) | **AKS**: Higher (always running nodes)
- **Factor**: Exam keyword | **Container Apps**: "Serverless containers" | **AKS**: "Kubernetes orchestration"

---

## 5. Azure Kubernetes Service (AKS)

### When to Use AKS

- Team has Kubernetes expertise
- Need custom operators, CRDs, service mesh
- Complex multi-container orchestration
- Compliance requires specific K8s configurations

### Key AKS Concepts for Exam

- **Concept**: **Node pools** | **What**: Groups of VMs running pods | **Exam Relevance**: System pool (required) + user pools
- **Concept**: **Cluster autoscaler** | **What**: Adds/removes nodes | **Exam Relevance**: Based on pending pod demand
- **Concept**: **HPA** (Horizontal Pod Autoscaler) | **What**: Adds/removes pods | **Exam Relevance**: Based on CPU/memory metrics
- **Concept**: **KEDA** | **What**: Event-driven pod scaling | **Exam Relevance**: Based on queue length, etc.
- **Concept**: **Azure CNI** | **What**: Native VNet IP per pod | **Exam Relevance**: Enterprise networking
- **Concept**: **Kubenet** | **What**: Route-based, NAT | **Exam Relevance**: Simpler, fewer IPs needed

### AKS Security

- **Feature**: Microsoft Entra integration | **Purpose**: RBAC with Azure AD identities
- **Feature**: Workload identity | **Purpose**: Pods authenticate with managed identity
- **Feature**: Network policies | **Purpose**: Pod-to-pod traffic filtering
- **Feature**: Private cluster | **Purpose**: API server not publicly accessible
- **Feature**: Azure Policy for AKS | **Purpose**: Enforce container standards

---

## 6. Azure Functions

### Hosting Plans

- **Plan**: **Consumption** | **Scaling**: Auto (0→many) | **Timeout**: 5 min (default, max 10) | **VNet**: Limited | **Cold Start**: Yes
- **Plan**: **Flex Consumption** | **Scaling**: Auto (0→many) | **Timeout**: Unlimited | **VNet**: Yes | **Cold Start**: Reduced (always-ready)
- **Plan**: **Premium** | **Scaling**: Pre-warmed instances | **Timeout**: Unlimited | **VNet**: Yes | **Cold Start**: No (always warm)
- **Plan**: **Dedicated (App Service)** | **Scaling**: Manual / auto-scale | **Timeout**: Unlimited | **VNet**: Yes | **Cold Start**: No

### Trigger Types

- **Trigger**: HTTP | **Use Case**: REST API, webhooks
- **Trigger**: Timer | **Use Case**: Scheduled tasks (CRON)
- **Trigger**: Queue (Storage) | **Use Case**: Async message processing
- **Trigger**: Service Bus | **Use Case**: Reliable message processing
- **Trigger**: Event Grid | **Use Case**: React to Azure resource events
- **Trigger**: Cosmos DB change feed | **Use Case**: Process document changes
- **Trigger**: Blob | **Use Case**: Process uploaded files

### Exam Keyword Mapping

- **Exam Phrase**: "Minimize cost, sporadic usage" | **Plan**: Consumption
- **Exam Phrase**: "No cold start, VNet" | **Plan**: Premium
- **Exam Phrase**: "Long-running processing" | **Plan**: Premium or Dedicated
- **Exam Phrase**: "Scale to zero, event-driven" | **Plan**: Consumption or Flex Consumption

---

## 7. Compute Decision Summary

- **Exam Scenario**: Lift-and-shift legacy Windows app | **Service**: VM (or App Service if .NET web app)
- **Exam Scenario**: Web app with deployment slots | **Service**: App Service (Standard+)
- **Exam Scenario**: Microservices, no K8s expertise | **Service**: Container Apps
- **Exam Scenario**: Complex K8s with custom operators | **Service**: AKS
- **Exam Scenario**: Timer-triggered cleanup job | **Service**: Azure Functions (Consumption)
- **Exam Scenario**: Event-driven with VNet, no cold start | **Service**: Azure Functions (Premium)
- **Exam Scenario**: Parallel batch processing | **Service**: Azure Batch
- **Exam Scenario**: Quick container burst (CI/CD agent) | **Service**: Azure Container Instances
- **Exam Scenario**: Complete network isolation | **Service**: App Service Isolated (ASE) or Private AKS
- **Exam Scenario**: GPU workloads | **Service**: VM (N-series) or AKS with GPU node pool

---

## Next Steps

- **Lab:** Deploy [container-apps-environment.bicep](../../infra/container-apps-environment.bicep)
- **Lab:** Deploy [aks-cluster.bicep](../../infra/aks-cluster.bicep)
- **Continue:** [Lesson 2 — Application Architecture](lesson-2-app-architecture.md)

---

## References

- [Compute Decision Tree](https://learn.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree)
- [App Service Overview](https://learn.microsoft.com/azure/app-service/overview)
- [Container Apps Overview](https://learn.microsoft.com/azure/container-apps/overview)
- [AKS Overview](https://learn.microsoft.com/azure/aks/intro-kubernetes)
- [Azure Functions Overview](https://learn.microsoft.com/azure/azure-functions/functions-overview)


---

<a id="module-4-lesson-2---application-architecture"></a>

## Module 4: Lesson 2 - Application Architecture

# Lesson 2: Application Architecture

**Duration:** 60 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a messaging architecture
- Recommend a caching solution
- Recommend an API integration solution
- Recommend a configuration management solution

---

## 1. Messaging Services

### The Three Messaging Services

- **Service**: **Service Bus** | **Pattern**: Message broker (queue/topic) | **Delivery**: At-least-once, FIFO, sessions | **Best For**: Commands, transactions, workflows
- **Service**: **Event Grid** | **Pattern**: Event routing (pub/sub) | **Delivery**: At-least-once, push | **Best For**: React to resource events, webhooks
- **Service**: **Event Hubs** | **Pattern**: Event streaming | **Delivery**: Partitioned consumer | **Best For**: Telemetry, log ingestion, big data

### Decision Tree

[Diagram removed for audio]

### Service Bus Deep Dive

- **Feature**: Pattern | **Queue**: Point-to-point | **Topic**: Publish-subscribe
- **Feature**: Receivers | **Queue**: One consumer per message | **Topic**: Multiple subscriptions
- **Feature**: Use case | **Queue**: Task distribution, commands | **Topic**: Fan-out notifications
- **Feature**: Ordering | **Queue**: FIFO (sessions) | **Topic**: Per-subscription FIFO
- **Feature**: Dead-letter | **Queue**: Yes | **Topic**: Yes

- **Tier**: **Basic** | **Feature**: Queues only | **Exam Use Case**: Simple messaging
- **Tier**: **Standard** | **Feature**: Queues + Topics | **Exam Use Case**: Pub/sub patterns
- **Tier**: **Premium** | **Feature**: Dedicated capacity, VNet | **Exam Use Case**: Enterprise, predictable performance

**Key Features for Exam:**
- **Sessions:** Guarantee FIFO ordering and message grouping
- **Dead-letter queue:** Handle poison messages
- **Duplicate detection:** Prevent processing same message twice
- **Scheduled delivery:** Send messages for future processing
- **Transactions:** Atomic operations across messages

### Event Grid Deep Dive

- **Component**: **Event source** | **Description**: Azure service emitting events (Storage, Resource Group, etc.)
- **Component**: **Topic** | **Description**: Endpoint that receives events
- **Component**: **Event subscription** | **Description**: Route events to handler with optional filtering
- **Component**: **Event handler** | **Description**: Destination (Function, Logic App, webhook, queue)

**Common Event Sources:**
- Blob Storage (blob created, deleted)
- Resource Groups (resource created, deleted, updated)
- Azure subscriptions (policy changes)
- Container Registry (image pushed)
- IoT Hub (device telemetry)

### Event Hubs Deep Dive

- **Feature**: Throughput | **Description**: Millions of events per second
- **Feature**: Retention | **Description**: 1-90 days (or unlimited with capture)
- **Feature**: Partitions | **Description**: 1-32 (Standard), up to 2000 (Dedicated)
- **Feature**: Consumer groups | **Description**: Independent readers of the same stream
- **Feature**: Capture | **Description**: Auto-archive to Blob Storage / ADLS Gen2

- **Tier**: **Basic** | **Throughput**: 1 consumer group | **Exam Use Case**: Dev/test
- **Tier**: **Standard** | **Throughput**: 20 consumer groups | **Exam Use Case**: Production
- **Tier**: **Premium** | **Throughput**: Processing Units | **Exam Use Case**: Isolation, VNet
- **Tier**: **Dedicated** | **Throughput**: Capacity Units | **Exam Use Case**: Extreme scale

---

## 2. Azure Cache for Redis

### Use Cases

- **Pattern**: **Data cache** | **Description**: Cache database query results | **Exam Keyword**: "Reduce database load"
- **Pattern**: **Session store** | **Description**: Store user session state | **Exam Keyword**: "Stateless web tier"
- **Pattern**: **Content cache** | **Description**: Cache static content | **Exam Keyword**: "Reduce latency for repeated reads"
- **Pattern**: **Distributed lock** | **Description**: Coordinate across instances | **Exam Keyword**: "Resource contention"
- **Pattern**: **Message broker** | **Description**: Pub/sub messaging (lightweight) | **Exam Keyword**: "Simple pub/sub"

### Tier Selection

- **Tier**: **Basic** | **Clustering**: No | **Geo-Replication**: No | **VNet**: No | **Best For**: Dev/test
- **Tier**: **Standard** | **Clustering**: No | **Geo-Replication**: No | **VNet**: No | **Best For**: Simple caching
- **Tier**: **Premium** | **Clustering**: Yes | **Geo-Replication**: Passive | **VNet**: Yes | **Best For**: Enterprise, persistence
- **Tier**: **Enterprise** | **Clustering**: Yes | **Geo-Replication**: Active-active | **VNet**: Yes | **Best For**: Mission-critical, Redis modules

### Caching Patterns

- **Pattern**: **Cache-aside** | **How**: App reads cache; on miss, reads DB and populates cache | **When**: Most common, read-heavy
- **Pattern**: **Write-through** | **How**: Write to cache + DB simultaneously | **When**: Consistency critical
- **Pattern**: **Write-behind** | **How**: Write to cache, async flush to DB | **When**: Write-heavy, eventual consistency OK

---

## 3. Azure API Management (APIM)

### Core Capabilities

- **Feature**: **API gateway** | **Description**: Single entry point for all APIs
- **Feature**: **Developer portal** | **Description**: Self-service API documentation and testing
- **Feature**: **Policies** | **Description**: Transform requests/responses (rate limiting, caching, auth)
- **Feature**: **Products** | **Description**: Group APIs with access policies
- **Feature**: **Subscriptions** | **Description**: API keys for access control

### Tier Selection

- **Tier**: **Consumption** | **VNet**: No | **Multi-region**: No | **Self-hosted**: No | **Best For**: Serverless, pay-per-call
- **Tier**: **Developer** | **VNet**: Yes (external only) | **Multi-region**: No | **Self-hosted**: Yes | **Best For**: Dev/test
- **Tier**: **Basic** | **VNet**: No | **Multi-region**: No | **Self-hosted**: No | **Best For**: Entry production
- **Tier**: **Standard** | **VNet**: No | **Multi-region**: No | **Self-hosted**: Yes | **Best For**: Standard production
- **Tier**: **Premium** | **VNet**: Yes (internal + external) | **Multi-region**: Yes | **Self-hosted**: Yes | **Best For**: Enterprise, VNet integration

### Key Policies for Exam

- **Policy**: `rate-limit` | **Purpose**: Throttle calls per subscription | **Exam Keyword**: "Prevent abuse"
- **Policy**: `quota` | **Purpose**: Limit total calls per period | **Exam Keyword**: "Monthly usage cap"
- **Policy**: `validate-jwt` | **Purpose**: Validate OAuth 2.0 tokens | **Exam Keyword**: "Secure API with Azure AD"
- **Policy**: `cache-lookup/cache-store` | **Purpose**: Cache API responses | **Exam Keyword**: "Reduce backend load"
- **Policy**: `cors` | **Purpose**: Enable cross-origin requests | **Exam Keyword**: "SPA calling API"
- **Policy**: `ip-filter` | **Purpose**: Restrict by IP address | **Exam Keyword**: "Whitelist IPs"
- **Policy**: `set-backend-service` | **Purpose**: Route to different backends | **Exam Keyword**: "Versioning, blue-green"
- **Policy**: `rewrite-uri` | **Purpose**: Transform URL paths | **Exam Keyword**: "Backend URL mapping"

### APIM + Azure AD Integration

[Diagram removed for audio]

---

## 4. Azure App Configuration

### What It Does

Centralized configuration management separate from application code.

- **Feature**: Key-value store | **Description**: Hierarchical, labeled configuration
- **Feature**: Feature flags | **Description**: Enable/disable features without redeployment
- **Feature**: Key Vault references | **Description**: Pull secrets from Key Vault through App Configuration
- **Feature**: Snapshots | **Description**: Point-in-time configuration snapshots
- **Feature**: Events | **Description**: Event Grid integration for config changes

### App Configuration vs. Key Vault

- **Factor**: Data type | **App Configuration**: Non-sensitive configuration | **Key Vault**: Secrets, certificates, keys
- **Factor**: Access model | **App Configuration**: Read-heavy, fast | **Key Vault**: Cryptographic operations
- **Factor**: Versioning | **App Configuration**: Labels and snapshots | **Key Vault**: Secret versions
- **Factor**: Use together | **App Configuration**: Yes — reference Key Vault secrets from App Config

### Feature Flags Pattern

[Diagram removed for audio]

---

## 5. Microservices Architecture Patterns

### Key Patterns for AZ-305

- **Pattern**: **API Gateway** | **Implementation**: APIM | **Exam Keyword**: Single entry point, cross-cutting concerns
- **Pattern**: **Service discovery** | **Implementation**: Container Apps built-in | **Exam Keyword**: "Services find each other"
- **Pattern**: **Event-driven** | **Implementation**: Service Bus / Event Grid | **Exam Keyword**: Loosely coupled services
- **Pattern**: **CQRS** | **Implementation**: Separate read/write models | **Exam Keyword**: "Optimize reads and writes separately"
- **Pattern**: **Saga** | **Implementation**: Service Bus with orchestrator | **Exam Keyword**: "Distributed transactions"
- **Pattern**: **Sidecar** | **Implementation**: Dapr in Container Apps | **Exam Keyword**: "Cross-cutting concerns per service"
- **Pattern**: **Circuit breaker** | **Implementation**: APIM retry policy / app code | **Exam Keyword**: "Prevent cascade failures"

### Dapr Integration (Container Apps)

- **Building Block**: Service invocation | **Purpose**: Service-to-service calls with mTLS
- **Building Block**: State management | **Purpose**: Pluggable state stores
- **Building Block**: Pub/sub | **Purpose**: Event-driven messaging
- **Building Block**: Bindings | **Purpose**: Input/output connectors
- **Building Block**: Secrets | **Purpose**: Centralized secret management

---

## 6. Summary Decision Matrix

- **Scenario**: Reliable message delivery, FIFO | **Service**: Service Bus (with sessions)
- **Scenario**: React to Azure resource events | **Service**: Event Grid
- **Scenario**: High-volume telemetry ingestion | **Service**: Event Hubs
- **Scenario**: Reduce database read load | **Service**: Azure Cache for Redis
- **Scenario**: Stateless web tier (session store) | **Service**: Azure Cache for Redis
- **Scenario**: Centralize API access + rate limiting | **Service**: API Management
- **Scenario**: Complete API network isolation | **Service**: APIM Premium (internal VNet)
- **Scenario**: Feature flags without redeployment | **Service**: App Configuration
- **Scenario**: Centralized config + secrets | **Service**: App Configuration + Key Vault
- **Scenario**: Distributed transactions across services | **Service**: Saga pattern with Service Bus

---

## Next Steps

- **Lab:** Deploy [apim-with-backends.bicep](../../infra/apim-with-backends.bicep)
- **Explore:** [API Architecture diagram](../../images/api-architecture.mmd)
- **Continue:** [Lesson 3 — Migrations](lesson-3-migrations.md)

---

## References

- [Service Bus Overview](https://learn.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Event Grid Overview](https://learn.microsoft.com/azure/event-grid/overview)
- [Event Hubs Overview](https://learn.microsoft.com/azure/event-hubs/event-hubs-about)
- [Redis Cache Overview](https://learn.microsoft.com/azure/azure-cache-for-redis/cache-overview)
- [API Management Overview](https://learn.microsoft.com/azure/api-management/api-management-key-concepts)
- [App Configuration Overview](https://learn.microsoft.com/azure/azure-app-configuration/overview)


---

<a id="module-4-lesson-3---migrations"></a>

## Module 4: Lesson 3 - Migrations

# Lesson 3: Migrations

**Duration:** 45 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Evaluate a migration solution for application and data
- Recommend a solution for Azure migrations (Azure Migrate, Data Migration strategies)
- Apply the Cloud Adoption Framework migration model

---

## 1. Cloud Adoption Framework (CAF) — Migration

### CAF Phases

[Diagram removed for audio]

- **Phase**: **Strategy** | **Key Activity**: Define business justification | **Deliverable**: Business case, motivations
- **Phase**: **Plan** | **Key Activity**: Assess digital estate, rationalize workloads | **Deliverable**: Migration plan, 5 Rs classification
- **Phase**: **Ready** | **Key Activity**: Set up Azure landing zone | **Deliverable**: Subscriptions, networking, identity
- **Phase**: **Migrate** | **Key Activity**: Rehost/refactor workloads | **Deliverable**: Running workloads in Azure
- **Phase**: **Innovate** | **Key Activity**: Rearchitect/rebuild for cloud-native | **Deliverable**: Modernized applications
- **Phase**: **Govern** | **Key Activity**: Compliance, cost, security baselines | **Deliverable**: Policies, guardrails
- **Phase**: **Manage** | **Key Activity**: Operations baseline | **Deliverable**: Monitoring, patching, SLA management

### The 5 Rs of Rationalization

- **Strategy**: **Rehost** (lift-and-shift) | **Description**: Move to Azure VMs as-is | **Exam Scenario**: "No code changes," "urgent timeline"
- **Strategy**: **Refactor** | **Description**: Move to PaaS with minimal changes | **Exam Scenario**: "Use App Service instead of VM"
- **Strategy**: **Rearchitect** | **Description**: Redesign for cloud-native features | **Exam Scenario**: "Microservices," "event-driven"
- **Strategy**: **Rebuild** | **Description**: Rewrite from scratch | **Exam Scenario**: "Legacy, no source code"
- **Strategy**: **Replace** | **Description**: Switch to SaaS | **Exam Scenario**: "Use Dynamics 365 instead of custom CRM"

### Migration Decision Flow

[Diagram removed for audio]

---

## 2. Azure Migrate

### Components

- **Component**: **Azure Migrate Hub** | **Purpose**: Central orchestration portal
- **Component**: **Discovery and assessment** | **Purpose**: Discover on-prem VMs, assess readiness
- **Component**: **Server Migration** | **Purpose**: Agentless or agent-based VM replication
- **Component**: **Database Migration** | **Purpose**: Azure Database Migration Service (DMS)
- **Component**: **Web App Migration** | **Purpose**: App Service Migration Assistant
- **Component**: **Data Box** | **Purpose**: Offline bulk data transfer

### Assessment Outputs

- **Assessment**: **Azure readiness** | **What It Tells You**: Can the VM run on Azure?
- **Assessment**: **Right-sizing** | **What It Tells You**: Recommended VM size
- **Assessment**: **Cost estimate** | **What It Tells You**: Monthly Azure cost
- **Assessment**: **Dependency analysis** | **What It Tells You**: What connects to what (agent-based or agentless)
- **Assessment**: **SQL assessment** | **What It Tells You**: SQL Server readiness for SQL DB, SQL MI, or SQL on VM

### Migration Approaches

- **Approach**: **Agentless** | **Method**: Azure Migrate appliance, no agent on VMs | **When**: VMware VMs, simpler setup
- **Approach**: **Agent-based** | **Method**: Mobility agent on each VM | **When**: Physical servers, Hyper-V, complex scenarios
- **Approach**: **Azure Site Recovery** | **Method**: Built-in replication engine | **When**: Fallback, non-VMware

---

## 3. Database Migration

### Azure Database Migration Service (DMS)

- **Migration Path**: SQL Server → SQL Database | **Source**: On-prem SQL Server | **Target**: Azure SQL Database | **Mode**: Offline / Online
- **Migration Path**: SQL Server → SQL MI | **Source**: On-prem SQL Server | **Target**: SQL Managed Instance | **Mode**: Online (near-zero downtime)
- **Migration Path**: PostgreSQL → PostgreSQL | **Source**: On-prem PostgreSQL | **Target**: Azure Database for PostgreSQL | **Mode**: Online
- **Migration Path**: MySQL → MySQL | **Source**: On-prem MySQL | **Target**: Azure Database for MySQL | **Mode**: Online
- **Migration Path**: MongoDB → Cosmos DB | **Source**: On-prem MongoDB | **Target**: Cosmos DB API for MongoDB | **Mode**: Online

### Other Migration Tools

- **Tool**: **Data Migration Assistant (DMA)** | **Purpose**: Assess SQL Server for compatibility issues
- **Tool**: **Azure SQL Migration extension** | **Purpose**: VS Code extension for SQL assessment + migration
- **Tool**: **Azure Data Box** | **Purpose**: Ship physical devices for large offline data transfer
- **Tool**: **AzCopy** | **Purpose**: CLI tool for fast blob/file transfers
- **Tool**: **Storage Migration Service** | **Purpose**: Migrate Windows file servers to Azure Files

### Migration Mode: Online vs. Offline

- **Mode**: **Offline** | **How**: Full backup + restore | **Downtime**: Hours | **Use Case**: Acceptable maintenance window
- **Mode**: **Online** | **How**: Initial sync + continuous replication + cutover | **Downtime**: Minutes | **Use Case**: Business-critical, minimal downtime

---

## 4. Landing Zones

### What Is a Landing Zone?

A pre-configured Azure environment with:
- Subscription structure and management groups
- Networking (hub-spoke or Virtual WAN)
- Identity and access management
- Governance policies
- Monitoring and logging

### Landing Zone Architecture

[Diagram removed for audio]

### Landing Zone Implementation Options

- **Option**: **Start small** | **Scope**: Single subscription | **Time**: Days | **Best For**: POC, small org
- **Option**: **Enterprise-scale** | **Scope**: Full CAF, multi-subscription | **Time**: Weeks | **Best For**: Enterprise, regulated industries
- **Option**: **CAF Terraform module** | **Scope**: IaC-driven | **Time**: Days-weeks | **Best For**: Existing Terraform teams
- **Option**: **Azure Landing Zone Accelerator** | **Scope**: Portal-guided deployment | **Time**: Hours | **Best For**: Quick enterprise setup

---

## 5. Application Migration Patterns

### Web Application Migration

- **Source**: IIS on Windows Server | **Target**: App Service | **Tool**: App Service Migration Assistant | **Exam Keyword**: "Migrate .NET web app"
- **Source**: Tomcat on Linux | **Target**: App Service (Linux) | **Tool**: App Service Migration Assistant | **Exam Keyword**: "Migrate Java web app"
- **Source**: Containerized app | **Target**: Container Apps or AKS | **Tool**: Docker push + deploy | **Exam Keyword**: "Migrate containers"
- **Source**: Spring Boot | **Target**: Azure Spring Apps | **Tool**: Spring migration guide | **Exam Keyword**: "Migrate Spring app"

### Data Migration Strategies

- **Data Type**: SQL Server databases | **Strategy**: Online migration | **Service**: DMS
- **Data Type**: File shares | **Strategy**: Storage Migration Service | **Service**: Azure Files
- **Data Type**: Large datasets (>10 TB) | **Strategy**: Offline transfer | **Service**: Azure Data Box
- **Data Type**: Blob data | **Strategy**: AzCopy / Data Factory | **Service**: Storage Account
- **Data Type**: NoSQL (MongoDB) | **Strategy**: Online migration | **Service**: DMS to Cosmos DB

---

## 6. Summary Decision Matrix

- **Scenario**: Discover and assess on-prem VMs | **Solution**: Azure Migrate (discovery + assessment)
- **Scenario**: Migrate VMware VMs to Azure | **Solution**: Azure Migrate (agentless)
- **Scenario**: Migrate SQL Server to SQL MI (minimal downtime) | **Solution**: DMS online migration
- **Scenario**: Move 50 TB of data to Azure | **Solution**: Azure Data Box
- **Scenario**: Migrate .NET web app to PaaS | **Solution**: App Service Migration Assistant
- **Scenario**: Set up enterprise Azure environment | **Solution**: CAF Landing Zone Accelerator
- **Scenario**: "No code changes allowed" | **Solution**: Rehost (VMs)
- **Scenario**: "Minimize management overhead" | **Solution**: Refactor to PaaS
- **Scenario**: "Need microservices architecture" | **Solution**: Rearchitect (Container Apps/AKS)
- **Scenario**: "Replace custom CRM" | **Solution**: Replace with SaaS (Dynamics 365)

---

## Next Steps

- **Explore:** [Migration Landing Zone diagram](../../images/migration-landing-zone.mmd)
- **Review:** [Cloud Adoption Framework](../../azure-architect-library/cloud-adoption-framework.md)
- **Knowledge Check:** [Module 4 Knowledge Check](knowledge-check.md)

---

## References

- [Cloud Adoption Framework](https://learn.microsoft.com/azure/cloud-adoption-framework/)
- [Azure Migrate Overview](https://learn.microsoft.com/azure/migrate/migrate-services-overview)
- [Database Migration Service](https://learn.microsoft.com/azure/dms/dms-overview)
- [5 Rs of Rationalization](https://learn.microsoft.com/azure/cloud-adoption-framework/digital-estate/5-rs-of-rationalization)
- [Azure Landing Zones](https://learn.microsoft.com/azure/cloud-adoption-framework/ready/landing-zone/)


---

<a id="module-4-knowledge-check"></a>

## Module 4: Knowledge Check

# Module 4 Knowledge Check: Infrastructure & Compute Solutions

**Target Score:** 80%+ before moving to Module 5

---

## Instructions

Choose the BEST answer for each scenario. This is the heaviest exam domain — make sure you understand the trade-offs.

---

### Q1. Compute Selection

A company wants to deploy a web application that processes variable traffic. During peak hours, it handles 1000 requests/second; at night, it drops to near zero. The team has no container or Kubernetes experience. They want to minimize cost and management. What should you recommend?

- A. Azure Virtual Machines with VMSS
- B. Azure App Service (Standard plan)
- C. Azure Container Apps (Consumption plan)
- D. Azure App Service (Premium v3 plan)

**Show Answer**

**Correct: C**

Container Apps with Consumption plan scales to zero (no cost when idle), auto-scales on HTTP traffic, and requires no K8s expertise. Minimizes both cost and management for variable workloads.

- **A is wrong:** VMSS requires managing VMs and doesn't scale to zero.
- **B is wrong:** Standard App Service plan charges 24/7 even with no traffic.
- **D is wrong:** Premium v3 is even more expensive and doesn't scale to zero.

---

### Q2. Functions Hosting

A company has an Azure Function that processes messages from a Service Bus queue. The processing takes 15 minutes per message. The Function must access resources in a VNet. What hosting plan should you recommend?

- A. Consumption plan
- B. Flex Consumption plan
- C. Premium plan
- D. Free tier App Service plan

**Show Answer**

**Correct: C**

Premium plan supports unlimited execution time (no timeout), VNet integration, and pre-warmed instances. Required for long-running + VNet scenarios.

- **A is wrong:** Consumption plan has a maximum 10-minute timeout, which can't handle 15-minute processing.
- **B is wrong:** Flex Consumption supports VNet and long execution but Premium is the established recommendation for guaranteed VNet + long-running.
- **D is wrong:** Free tier doesn't support Functions Premium capabilities.

---

### Q3. Messaging Service Selection

An IoT platform ingests telemetry from 100,000 sensors sending data every second. The data needs to be processed in near-real-time and archived to Azure Data Lake. What messaging service should you use?

- A. Azure Service Bus
- B. Azure Event Grid
- C. Azure Event Hubs
- D. Azure Queue Storage

**Show Answer**

**Correct: C**

Event Hubs handles millions of events per second with partitioned consumers, Capture (auto-archive to ADLS), and Kafka compatibility. Purpose-built for high-volume telemetry ingestion.

- **A is wrong:** Service Bus is for commands and workflows, not high-volume telemetry. Lower throughput ceiling.
- **B is wrong:** Event Grid is for discrete events (resource changes), not continuous telemetry streams.
- **D is wrong:** Queue Storage has limited throughput and lacks streaming features like partitions and capture.

---

### Q4. Service Bus vs. Event Grid

An application needs to notify multiple downstream services when a new order is placed. Each service should receive the notification independently. Messages must support dead-lettering for failed deliveries. What should you recommend?

- A. Azure Service Bus Queue
- B. Azure Service Bus Topic with subscriptions
- C. Azure Event Grid
- D. Azure Event Hubs

**Show Answer**

**Correct: B**

Service Bus Topics support pub/sub with multiple subscriptions (each service gets its own copy), dead-letter queues for failed messages, and reliable delivery guarantees.

- **A is wrong:** Queues are point-to-point — only one consumer gets each message, not fan-out.
- **C is wrong:** Event Grid supports pub/sub but has limited dead-letter capabilities compared to Service Bus and is better for events, not commands.
- **D is wrong:** Event Hubs is for streaming, not pub/sub command patterns.

---

### Q5. API Management

A company is exposing internal APIs to external partners. They need rate limiting, OAuth 2.0 token validation, and the ability to publish API documentation for partners. The APIs are deployed in a VNet and must not be directly accessible from the internet. What should you recommend?

- A. APIM Consumption tier
- B. APIM Developer tier
- C. APIM Standard tier
- D. APIM Premium tier with internal VNet mode

**Show Answer**

**Correct: D**

Premium tier supports internal VNet deployment (APIs not directly internet-accessible), rate limiting, JWT validation policies, and a developer portal for partner documentation.

- **A is wrong:** Consumption tier doesn't support VNet integration.
- **B is wrong:** Developer tier supports external VNet only, not internal mode. Also no SLA.
- **C is wrong:** Standard tier doesn't support VNet integration.

---

### Q6. Caching Strategy

A web application reads product catalog data from Azure SQL Database. The same data is read millions of times but updated only hourly. Response latency must be under 5ms. What should you recommend?

- A. Increase SQL Database tier to Business Critical
- B. Azure Cache for Redis with cache-aside pattern
- C. Cosmos DB with session consistency
- D. Azure CDN

**Show Answer**

**Correct: B**

Redis provides sub-millisecond latency for cached data. Cache-aside pattern: check cache first → on miss, read from SQL → populate cache. Hourly updates can invalidate/refresh the cache.

- **A is wrong:** Upgrading SQL tier reduces query latency but can't match Redis sub-ms performance for repeated reads.
- **C is wrong:** Cosmos DB is a database, not a caching layer — adds complexity without solving the caching need.
- **D is wrong:** CDN caches static content at edge locations, not dynamic database query results.

---

### Q7. Migration Strategy

A company has a legacy .NET Framework 4.5 application running on IIS with a SQL Server 2016 backend. They have a 2-month deadline, no developer resources for code changes, and the database uses SQL Agent jobs and CLR assemblies. What migration strategy and target should you recommend?

- A. Rehost: VMs for app + SQL Server on Azure VM
- B. Refactor: App Service + Azure SQL Database
- C. Rehost: VMs for app + SQL Managed Instance
- D. Rearchitect: Container Apps + Cosmos DB

**Show Answer**

**Correct: C**

The app is lift-and-shifted to a VM (no code changes needed). SQL Server migrates to SQL Managed Instance because it supports SQL Agent jobs and CLR (Azure SQL Database does not). This is a PaaS upgrade for the database while keeping the app as-is.

- **A is wrong:** SQL Server on VM works but misses the opportunity to use managed PaaS for the database.
- **B is wrong:** Azure SQL Database doesn't support SQL Agent or CLR. .NET Framework 4.5 on App Service may have compatibility issues.
- **D is wrong:** Rearchitecting violates the "no code changes" and 2-month deadline constraints.

---

### Q8. Azure Migrate

A company wants to migrate 200 VMware VMs to Azure. They need to assess readiness, right-size VMs, estimate costs, and understand dependencies between servers before migrating. What tools should they use?

- A. Azure Site Recovery only
- B. Azure Migrate with discovery, assessment, and dependency analysis
- C. Azure Data Box
- D. Azure Resource Mover

**Show Answer**

**Correct: B**

Azure Migrate provides the complete discovery-assess-migrate workflow: automatic discovery of VMware VMs, readiness assessment, right-sizing recommendations, cost estimates, and dependency mapping (agent-based or agentless).

- **A is wrong:** ASR handles replication/failover but doesn't provide assessment, right-sizing, or dependency analysis.
- **C is wrong:** Data Box is for offline data transfer, not VM migration.
- **D is wrong:** Resource Mover moves existing Azure resources between regions, not on-premises to Azure.

---

### Q9. App Configuration

A development team deploys the same application to dev, staging, and production environments. They need to manage environment-specific configuration centrally, toggle features without redeployment, and keep secrets secure. What should you recommend?

- A. App Service application settings per environment
- B. Azure App Configuration with labels + feature flags + Key Vault references
- C. Environment variables in Docker containers
- D. Azure Key Vault only

**Show Answer**

**Correct: B**

App Configuration with labels (dev/staging/prod) provides centralized config per environment. Feature flags enable toggling without redeployment. Key Vault references securely pull secrets through App Configuration.

- **A is wrong:** App Service settings are per-instance, not centralized. No feature flag support.
- **C is wrong:** Docker environment variables are per-container, not centralized. No feature flags.
- **D is wrong:** Key Vault stores secrets but isn't designed for general configuration or feature flags.

---

### Q10. Container Orchestration

A company is deploying a microservices application with 15 services. The team has strong Kubernetes expertise and needs custom operators, a service mesh (Istio), and fine-grained control over pod networking with Azure CNI. What should you recommend?

- A. Azure Container Apps
- B. Azure Kubernetes Service (AKS)
- C. Azure Container Instances
- D. Azure App Service with containers

**Show Answer**

**Correct: B**

AKS provides full Kubernetes control: custom operators, CRDs, Istio service mesh, Azure CNI networking, and granular pod configuration. Required when teams need Kubernetes-level customization.

- **A is wrong:** Container Apps is opinionated and doesn't support custom operators, arbitrary service meshes, or Azure CNI.
- **C is wrong:** ACI runs individual containers, not orchestrated microservices with service mesh.
- **D is wrong:** App Service supports containers but not custom operators, Istio, or K8s-level networking.

---

## Scoring

- **Score**: 9-10 / 10 (90-100%) | **Next Step**: Excellent! Move to Module 5
- **Score**: 8 / 10 (80%) | **Next Step**: Good. Review missed questions, then move to Module 5
- **Score**: 6-7 / 10 (60-70%) | **Next Step**: Review the relevant lessons before proceeding
- **Score**: Below 6 / 10 (<60%) | **Next Step**: Re-study the full module before retaking

---

## Continue Learning

- **MS Learn Path:** [Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/)
- **Case Studies:** [Compute](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/02-Compute.html) | [App Architecture](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/05-Apparchitecture.html)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Next:** [Module 5 — Network Solutions](../module-5-networking/overview.md)


---

<a id="module-5-overview"></a>

## Module 5: Overview

# Module 5: Network Solutions

**Estimated Duration:** 3-4 hours | **Exam Weight:** Part of 30-35% (Infrastructure)

---

## Module Overview

Design network topologies, connectivity, security, and load balancing solutions for Azure infrastructure.

---

## Domain Objectives Covered

- **#**: 5.1 | **Objective**: Design a network architecture
- **#**: 5.2 | **Objective**: Design for network security and connectivity

---

## Lessons

- **#**: 1 | **Lesson**: [Network Topology & Connectivity](lesson-1-network-topology.md) | **Duration**: 60 min | **Focus**: VNet design, hub-spoke, Virtual WAN, hybrid connectivity
- **#**: 2 | **Lesson**: [Network Security](lesson-2-network-security.md) | **Duration**: 60 min | **Focus**: NSG, Firewall, WAF, Private Link, DDoS Protection
- **#**: 3 | **Lesson**: [Load Balancing](lesson-3-load-balancing.md) | **Duration**: 45 min | **Focus**: Load Balancer, App Gateway, Front Door, Traffic Manager

---

## Key Concepts to Master

- **Concept**: **Hub-spoke vs. Virtual WAN** | **Why It Matters**: Most common topology question
- **Concept**: **Private Link vs. Service Endpoints** | **Why It Matters**: Critical security decision
- **Concept**: **NSG vs. Azure Firewall** | **Why It Matters**: Different scopes of protection
- **Concept**: **Load balancer selection** | **Why It Matters**: L4 vs. L7, regional vs. global
- **Concept**: **ExpressRoute vs. VPN** | **Why It Matters**: Hybrid connectivity options

---

## Hands-On Labs

- **Lab**: Hub-Spoke Network | **Template**: [hub-spoke-network.bicep](../../infra/hub-spoke-network.bicep) | **Purpose**: VNet peering with hub topology
- **Lab**: Application Gateway WAF | **Template**: [application-gateway-waf.bicep](../../infra/application-gateway-waf.bicep) | **Purpose**: L7 load balancer with WAF
- **Lab**: Front Door | **Template**: [front-door-global.bicep](../../infra/front-door-global.bicep) | **Purpose**: Global load balancing with CDN
- **Lab**: Private Endpoints | **Template**: [private-endpoint-services.bicep](../../infra/private-endpoint-services.bicep) | **Purpose**: Private access to PaaS services

---

## Architecture Diagrams

- [Hub-Spoke Network](../../images/hub-spoke-network.mmd)
- [Private Link Topology](../../images/private-link-topology.mmd)

---

## Exam Tips

- Network questions often combine security + topology requirements
- Private Link is preferred over Service Endpoints for data exfiltration protection
- Azure Firewall is centralized (hub-level), NSG is per-subnet/NIC
- Know the 4 Azure load balancing services and when to use each
- ExpressRoute provides private connectivity (not internet), VPN uses encrypted internet tunnel

---

## Knowledge Check

Complete the [Module 5 Knowledge Check](knowledge-check.md) before the final review.

**Target:** 80%+ (8/10 correct)

---

## Official Microsoft Resources

### MS Learn Path
Networking is covered within [AZ-305: Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/) (3 hr 39 min)
- [Design network solutions](https://learn.microsoft.com/training/modules/design-network-solutions/) (53 min)

### Case Studies
Complete this scenario-based exercise from the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):
- [Design a network solution — BI enterprise application](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/08-Logging.html)

### Practice Assessment
[Take the free AZ-305 practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) after completing all 5 modules.


---

<a id="module-5-lesson-1---network-topology-and-connectivity"></a>

## Module 5: Lesson 1 - Network Topology and Connectivity

# Lesson 1: Network Topology & Connectivity

**Duration:** 60 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a network architecture (hub-spoke, Virtual WAN)
- Recommend a solution for network addressing and name resolution
- Recommend a solution for hybrid connectivity (VPN, ExpressRoute)

---

## 1. Virtual Network (VNet) Fundamentals

### Key Concepts

- **Concept**: **VNet** | **Description**: Isolated network in Azure, regional scope
- **Concept**: **Subnet** | **Description**: Segment within a VNet, can have NSGs and route tables
- **Concept**: **Address space** | **Description**: CIDR block (e.g., 10.0.0.0/16) — plan for no overlap
- **Concept**: **VNet peering** | **Description**: Connects VNets (same or different region), non-transitive
- **Concept**: **Service endpoints** | **Description**: Route traffic to PaaS via Azure backbone
- **Concept**: **Private endpoints** | **Description**: Private IP in your VNet for PaaS services

### Address Space Planning

[Diagram removed for audio]

**Key Rules:**
- No overlapping address spaces between peered VNets
- `/24` minimum for most subnets (251 usable IPs)
- `/27` minimum for GatewaySubnet
- `/26` minimum for AzureBastionSubnet
- `/26` minimum for AzureFirewallSubnet

---

## 2. Hub-Spoke Topology

### Architecture

[Diagram removed for audio]

### Components

- **Component**: Azure Firewall | **Location**: Hub | **Purpose**: Centralized traffic filtering
- **Component**: VPN/ER Gateway | **Location**: Hub | **Purpose**: Hybrid connectivity
- **Component**: Azure Bastion | **Location**: Hub | **Purpose**: Secure VM access (no public IPs)
- **Component**: DNS | **Location**: Hub | **Purpose**: Centralized name resolution
- **Component**: Workloads | **Location**: Spokes | **Purpose**: Application VMs, PaaS services

### Hub-Spoke Rules

- **Rule**: Peering is non-transitive | **Details**: Spoke-to-spoke traffic must route through hub (firewall/NVA)
- **Rule**: Use UDR for spoke-to-spoke | **Details**: User-Defined Routes force traffic via hub firewall
- **Rule**: Gateway transit | **Details**: Spokes can use the hub's VPN/ER gateway
- **Rule**: Spoke isolation | **Details**: Each spoke is a separate security boundary

---

## 3. Azure Virtual WAN

### When to Use Virtual WAN vs. Hub-Spoke

- **Factor**: Scale | **Hub-Spoke (DIY)**: Small-medium (< 30 VNets) | **Azure Virtual WAN**: Large (30+ VNets, many branches)
- **Factor**: Branch connectivity | **Hub-Spoke (DIY)**: Managed VPN/ER gateways | **Azure Virtual WAN**: Automated branch-to-branch
- **Factor**: Transitive routing | **Hub-Spoke (DIY)**: Requires UDR + NVA/Firewall | **Azure Virtual WAN**: Built-in transit
- **Factor**: Management | **Hub-Spoke (DIY)**: Customer managed | **Azure Virtual WAN**: Microsoft managed
- **Factor**: Cost | **Hub-Spoke (DIY)**: Lower (build your own) | **Azure Virtual WAN**: Higher (managed service)
- **Factor**: Exam keyword | **Hub-Spoke (DIY)**: "Small/medium enterprise" | **Azure Virtual WAN**: "Large enterprise, many branches"

### Virtual WAN Components

- **Component**: **Virtual WAN** | **Purpose**: Parent resource
- **Component**: **Virtual Hub** | **Purpose**: Managed hub VNet per region
- **Component**: **Connections** | **Purpose**: VNet, VPN site, ExpressRoute, or P2S
- **Component**: **Routing** | **Purpose**: Automatic route propagation between hubs

### Virtual WAN Tiers

- **Tier**: **Basic** | **Features**: S2S VPN only
- **Tier**: **Standard** | **Features**: S2S VPN, P2S VPN, ExpressRoute, inter-hub transit, Azure Firewall

---

## 4. Hybrid Connectivity

### VPN Gateway

- **Feature**: Protocol | **Details**: IPSec/IKEv2 over public internet
- **Feature**: Bandwidth | **Details**: Up to 10 Gbps (VpnGw5)
- **Feature**: Encryption | **Details**: AES-256
- **Feature**: Use case | **Details**: Branch offices, dev/test, backup connectivity

- **SKU**: VpnGw1 | **Max S2S**: 30 | **Max P2S**: 250 | **Max Bandwidth**: 650 Mbps
- **SKU**: VpnGw2 | **Max S2S**: 30 | **Max P2S**: 500 | **Max Bandwidth**: 1 Gbps
- **SKU**: VpnGw3 | **Max S2S**: 30 | **Max P2S**: 1000 | **Max Bandwidth**: 1.25 Gbps
- **SKU**: VpnGw5 | **Max S2S**: 100 | **Max P2S**: 10000 | **Max Bandwidth**: 10 Gbps

### ExpressRoute

- **Feature**: Protocol | **Details**: Private connectivity via partner/direct peering
- **Feature**: Bandwidth | **Details**: 50 Mbps to 100 Gbps
- **Feature**: Internet | **Details**: Does NOT travel over public internet
- **Feature**: Use case | **Details**: Production, compliance, high bandwidth

- **SKU**: **Local** | **Use Case**: Same metro as ER location, unlimited data
- **SKU**: **Standard** | **Use Case**: Same geopolitical region
- **SKU**: **Premium** | **Use Case**: Global reach (cross-region), Microsoft 365

### ExpressRoute vs. VPN Decision

[Diagram removed for audio]

### Coexistence Pattern

[Diagram removed for audio]

**Exam Tip:** ExpressRoute + VPN as backup is a common best-practice pattern.

---

## 5. DNS in Azure

### Azure DNS Options

- **Option**: **Azure DNS (public zones)** | **Use Case**: Host public domain DNS records
- **Option**: **Azure DNS (private zones)** | **Use Case**: Name resolution for VNet resources
- **Option**: **Azure DNS Private Resolver** | **Use Case**: Conditional forwarding between on-prem and Azure

### Private DNS Zones

- **Zone**: `privatelink.blob.core.windows.net` | **Purpose**: Private endpoints for Blob Storage
- **Zone**: `privatelink.database.windows.net` | **Purpose**: Private endpoints for Azure SQL
- **Zone**: `privatelink.vaultcore.azure.net` | **Purpose**: Private endpoints for Key Vault
- **Zone**: Custom zones (e.g., `contoso.internal`) | **Purpose**: Internal name resolution

### DNS Resolution Flow (Hybrid)

[Diagram removed for audio]

---

## 6. Summary Decision Matrix

- **Scenario**: Small-medium enterprise networking | **Solution**: Hub-spoke topology
- **Scenario**: Large enterprise, many branches | **Solution**: Azure Virtual WAN (Standard)
- **Scenario**: Private connectivity, not over internet | **Solution**: ExpressRoute
- **Scenario**: Encrypted tunnel over internet | **Solution**: VPN Gateway
- **Scenario**: Primary + backup connectivity | **Solution**: ExpressRoute + VPN coexistence
- **Scenario**: Cross-region ExpressRoute | **Solution**: ExpressRoute Premium + Global Reach
- **Scenario**: Resolve Azure private endpoints from on-prem | **Solution**: Azure DNS Private Resolver
- **Scenario**: Secure VM access without public IPs | **Solution**: Azure Bastion (in hub)

---

## Next Steps

- **Lab:** Deploy [hub-spoke-network.bicep](../../infra/hub-spoke-network.bicep)
- **Diagram:** Review [hub-spoke-network.mmd](../../images/hub-spoke-network.mmd)
- **Continue:** [Lesson 2 — Network Security](lesson-2-network-security.md)

---

## References

- [Hub-Spoke Topology](https://learn.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
- [Virtual WAN Overview](https://learn.microsoft.com/azure/virtual-wan/virtual-wan-about)
- [ExpressRoute Overview](https://learn.microsoft.com/azure/expressroute/expressroute-introduction)
- [VPN Gateway Overview](https://learn.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)
- [Azure DNS Private Resolver](https://learn.microsoft.com/azure/dns/dns-private-resolver-overview)


---

<a id="module-5-lesson-2---network-security"></a>

## Module 5: Lesson 2 - Network Security

# Lesson 2: Network Security

**Duration:** 60 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a solution for network security (NSG, Azure Firewall, WAF)
- Recommend a solution for private connectivity to Azure PaaS services
- Recommend a solution for securing internet-facing applications

---

## 1. Network Security Layers

### Defense-in-Depth

[Diagram removed for audio]

---

## 2. Network Security Groups (NSG)

### How NSGs Work

- **Scope**: **Subnet** | **Attachment**: Applied to all resources in subnet | **Effect**: Default for most scenarios
- **Scope**: **NIC** | **Attachment**: Applied to specific VM NIC | **Effect**: Fine-grained per-VM rules
- **Scope**: **Both** | **Attachment**: Subnet + NIC | **Effect**: Most restrictive combination wins

### Default Rules

- **Priority**: 65000 | **Direction**: Inbound | **Action**: Allow | **Traffic**: VNet-to-VNet
- **Priority**: 65001 | **Direction**: Inbound | **Action**: Allow | **Traffic**: Azure Load Balancer probes
- **Priority**: 65500 | **Direction**: Inbound | **Action**: Deny | **Traffic**: All other inbound
- **Priority**: 65000 | **Direction**: Outbound | **Action**: Allow | **Traffic**: VNet-to-VNet
- **Priority**: 65001 | **Direction**: Outbound | **Action**: Allow | **Traffic**: Internet outbound
- **Priority**: 65500 | **Direction**: Outbound | **Action**: Deny | **Traffic**: All other outbound

### NSG Best Practices for Exam

- **Practice**: Apply at subnet level (not NIC) | **Why**: Simpler management, consistent rules
- **Practice**: Use Application Security Groups (ASG) | **Why**: Group VMs by role (web, app, data)
- **Practice**: Deny internet inbound by default | **Why**: Only open what's needed
- **Practice**: Use service tags | **Why**: `AzureCloud`, `Storage`, `Sql` instead of IPs

### Application Security Groups (ASG)

[Diagram removed for audio]

No need to manage individual IP addresses — ASGs group VMs logically.

---

## 3. Azure Firewall

### NSG vs. Azure Firewall

- **Feature**: Scope | **NSG**: Subnet or NIC | **Azure Firewall**: VNet or cross-VNet (hub)
- **Feature**: Layer | **NSG**: L3/L4 (IP, port) | **Azure Firewall**: L3/L4/L7 (FQDN, URL, TLS)
- **Feature**: FQDN filtering | **NSG**: No | **Azure Firewall**: Yes (`*.microsoft.com`)
- **Feature**: Threat intelligence | **NSG**: No | **Azure Firewall**: Yes (block known malicious IPs)
- **Feature**: TLS inspection | **NSG**: No | **Azure Firewall**: Yes (Premium)
- **Feature**: Cost | **NSG**: Free | **Azure Firewall**: Significant (per hour + per GB)
- **Feature**: Exam keyword | **NSG**: "Subnet-level filtering" | **Azure Firewall**: "Centralized, FQDN, threat intelligence"

### Azure Firewall Tiers

- **Tier**: **Standard** | **Key Features**: L3/L4/L7 filtering, FQDN, threat intel, NAT rules
- **Tier**: **Premium** | **Key Features**: Standard + TLS inspection, IDPS, URL filtering, web categories
- **Tier**: **Basic** | **Key Features**: Limited features, lower cost, small environments

### Azure Firewall Policy

[Diagram removed for audio]

### Firewall Placement (Hub-Spoke)

[Diagram removed for audio]

---

## 4. Private Endpoints vs. Service Endpoints

### Comparison

- **Feature**: Network path | **Service Endpoint**: Azure backbone (optimized route) | **Private Endpoint**: Private IP in your VNet
- **Feature**: Source IP (PaaS sees) | **Service Endpoint**: VNet subnet IP | **Private Endpoint**: Private endpoint IP
- **Feature**: Data exfiltration risk | **Service Endpoint**: Can access any instance of the service | **Private Endpoint**: Only your specific resource
- **Feature**: DNS | **Service Endpoint**: Public DNS (no change) | **Private Endpoint**: Requires Private DNS zone
- **Feature**: Cost | **Service Endpoint**: Free | **Private Endpoint**: Per-hour + per-GB
- **Feature**: On-prem access | **Service Endpoint**: No (VNet only) | **Private Endpoint**: Yes (via VPN/ER + DNS)
- **Feature**: Exam preference | **Service Endpoint**: Budget-sensitive, simple | **Private Endpoint**: **Default recommendation**

### Private Endpoint Architecture

[Diagram removed for audio]

### When to Use Which

- **Scenario**: Block access from internet, PaaS in VNet | **Solution**: Private Endpoint
- **Scenario**: Access PaaS from on-premises via VPN/ER | **Solution**: Private Endpoint
- **Scenario**: Prevent data exfiltration to other storage accounts | **Solution**: Private Endpoint
- **Scenario**: Quick, free optimization of traffic path | **Solution**: Service Endpoint
- **Scenario**: Exam default recommendation | **Solution**: **Private Endpoint**

---

## 5. Web Application Firewall (WAF)

### Where WAF Can Run

- **Service**: **Application Gateway** | **WAF**: WAF v2 | **Use Case**: Regional web apps
- **Service**: **Azure Front Door** | **WAF**: WAF | **Use Case**: Global web apps
- **Service**: **Azure CDN (from Microsoft)** | **WAF**: WAF | **Use Case**: CDN edge protection

### WAF Features

- **Feature**: OWASP rule sets | **Description**: Protect against SQL injection, XSS, etc.
- **Feature**: Custom rules | **Description**: IP-based, geo-based, rate-limiting
- **Feature**: Bot protection | **Description**: Block/allow known bot categories
- **Feature**: Modes | **Description**: Detection (log only) or Prevention (block)
- **Feature**: Per-site policies | **Description**: Different WAF policies per listener/route

### WAF Decision

[Diagram removed for audio]

---

## 6. DDoS Protection

### Tiers

- **Feature**: Scope | **DDoS Network Protection**: VNet (all public IPs) | **DDoS IP Protection**: Per public IP
- **Feature**: Cost | **DDoS Network Protection**: ~$2,944/month + overage | **DDoS IP Protection**: ~$199/month per IP
- **Feature**: Added features | **DDoS Network Protection**: Cost protection, rapid response, diagnostics | **DDoS IP Protection**: Basic diagnostics
- **Feature**: Best for | **DDoS Network Protection**: Enterprise with many public IPs | **DDoS IP Protection**: Few public IPs

### Always-On Protection

Azure **DDoS Infrastructure Protection** (free, default) protects against common network-layer attacks. DDoS Protection plans add:
- Adaptive tuning for your traffic profiles
- Attack analytics and alerting
- Cost protection (credit for scale-out during attack)
- DDoS Rapid Response team access

---

## 7. Azure Bastion

Secure RDP/SSH access to VMs without public IP addresses.

- **Tier**: **Basic** | **Features**: RDP/SSH via portal
- **Tier**: **Standard** | **Features**: + Native client, IP-based, shareable link, scaling
- **Tier**: **Premium** | **Features**: + Session recording

### Bastion vs. Alternatives

- **Access Method**: Public IP + NSG | **Security**: Exposed to internet | **Exam Keyword**: "Legacy, not recommended"
- **Access Method**: JIT VM Access (Defender) | **Security**: Temporary NSG rule | **Exam Keyword**: "Time-limited access"
- **Access Method**: Azure Bastion | **Security**: No public IP needed | **Exam Keyword**: "Secure VM access"
- **Access Method**: VPN + private IP | **Security**: Requires VPN client | **Exam Keyword**: "Existing VPN infrastructure"

---

## 8. Summary Decision Matrix

- **Scenario**: Subnet/NIC traffic filtering | **Solution**: NSG
- **Scenario**: Group VMs by role for rules | **Solution**: Application Security Groups (ASG)
- **Scenario**: Centralized FQDN filtering, threat intel | **Solution**: Azure Firewall (Standard)
- **Scenario**: TLS inspection, IDPS | **Solution**: Azure Firewall (Premium)
- **Scenario**: PaaS private access, prevent exfiltration | **Solution**: Private Endpoint
- **Scenario**: Quick traffic optimization, budget | **Solution**: Service Endpoint
- **Scenario**: Protect web apps from OWASP attacks | **Solution**: WAF (App Gateway or Front Door)
- **Scenario**: Volumetric DDoS protection | **Solution**: DDoS Protection plan
- **Scenario**: Secure VM access, no public IPs | **Solution**: Azure Bastion

---

## Next Steps

- **Lab:** Deploy [private-endpoint-services.bicep](../../infra/private-endpoint-services.bicep)
- **Lab:** Deploy [application-gateway-waf.bicep](../../infra/application-gateway-waf.bicep)
- **Diagram:** Review [private-link-topology.mmd](../../images/private-link-topology.mmd)
- **Continue:** [Lesson 3 — Load Balancing](lesson-3-load-balancing.md)

---

## References

- [NSG Overview](https://learn.microsoft.com/azure/virtual-network/network-security-groups-overview)
- [Azure Firewall Overview](https://learn.microsoft.com/azure/firewall/overview)
- [Private Link / Private Endpoints](https://learn.microsoft.com/azure/private-link/private-link-overview)
- [WAF on Application Gateway](https://learn.microsoft.com/azure/web-application-firewall/ag/ag-overview)
- [DDoS Protection Overview](https://learn.microsoft.com/azure/ddos-protection/ddos-protection-overview)


---

<a id="module-5-lesson-3---load-balancing"></a>

## Module 5: Lesson 3 - Load Balancing

# Lesson 3: Load Balancing

**Duration:** 45 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a load balancing solution
- Choose between regional and global load balancers
- Choose between Layer 4 and Layer 7 load balancers

---

## 1. Azure Load Balancing Services

### The Four Load Balancers

- **Service**: **Azure Load Balancer** | **Scope**: Regional | **Layer**: L4 | **Protocol**: TCP/UDP | **Key Feature**: Ultra-low latency, HA ports
- **Service**: **Application Gateway** | **Scope**: Regional | **Layer**: L7 | **Protocol**: HTTP/HTTPS | **Key Feature**: URL routing, SSL offload, WAF
- **Service**: **Azure Front Door** | **Scope**: Global | **Layer**: L7 | **Protocol**: HTTP/HTTPS | **Key Feature**: CDN, WAF, global distribution
- **Service**: **Traffic Manager** | **Scope**: Global | **Layer**: DNS | **Protocol**: Any | **Key Feature**: DNS-based routing, any protocol

### Decision Tree

[Diagram removed for audio]

---

## 2. Azure Load Balancer (L4)

### SKUs

- **Feature**: SLA | **Basic**: None | **Standard**: 99.99%
- **Feature**: Backend pool | **Basic**: Availability Set only | **Standard**: Any VMs in VNet
- **Feature**: Health probes | **Basic**: TCP, HTTP | **Standard**: TCP, HTTP, HTTPS
- **Feature**: HA Ports | **Basic**: No | **Standard**: Yes
- **Feature**: Availability Zones | **Basic**: No | **Standard**: Zone-redundant
- **Feature**: Outbound rules | **Basic**: No | **Standard**: Yes
- **Feature**: **Exam:** | **Basic**: "Don't use for production" | **Standard**: **Default recommendation**

### Key Concepts

- **Concept**: **Frontend IP** | **Description**: Public or internal IP that receives traffic
- **Concept**: **Backend pool** | **Description**: VMs/VMSS that serve traffic
- **Concept**: **Health probes** | **Description**: TCP/HTTP checks to detect unhealthy instances
- **Concept**: **Load balancing rules** | **Description**: Map frontend port to backend port
- **Concept**: **HA Ports** | **Description**: Load balance ALL ports (useful for NVA/firewall)
- **Concept**: **Outbound rules** | **Description**: Control SNAT for outbound internet access

### Internal vs. Public

- **Type**: **Public** | **Use Case**: Internet-facing services
- **Type**: **Internal** | **Use Case**: Internal services (app tier behind web tier)

---

## 3. Application Gateway (L7)

### Key Features

- **Feature**: **URL-based routing** | **Description**: Route `/api/*` to one pool, `/web/*` to another
- **Feature**: **Multi-site hosting** | **Description**: Route by host header (`app1.contoso.com`, `app2.contoso.com`)
- **Feature**: **SSL termination** | **Description**: Decrypt at gateway, re-encrypt or HTTP to backend
- **Feature**: **SSL end-to-end** | **Description**: Decrypt, inspect, re-encrypt to backend
- **Feature**: **Cookie-based affinity** | **Description**: Session stickiness
- **Feature**: **Autoscaling** | **Description**: Scale instances based on traffic (v2)
- **Feature**: **WAF** | **Description**: Built-in OWASP protection (v2)
- **Feature**: **Zone redundancy** | **Description**: Deploy across availability zones

### Application Gateway SKUs

- **SKU**: **Standard v2** | **Key Feature**: Autoscale, zone redundancy | **Use Case**: Production web apps
- **SKU**: **WAF v2** | **Key Feature**: Standard v2 + WAF | **Use Case**: Web apps needing OWASP protection

### Components

[Diagram removed for audio]

---

## 4. Azure Front Door (Global L7)

### Key Features

- **Feature**: **Global anycast** | **Description**: Routes to nearest POP (250+ edge locations)
- **Feature**: **CDN integration** | **Description**: Built-in content caching at edge
- **Feature**: **WAF** | **Description**: Global WAF with custom rules and bot protection
- **Feature**: **SSL offload** | **Description**: Edge termination, managed certificates
- **Feature**: **URL routing** | **Description**: Path-based and host-based routing
- **Feature**: **Session affinity** | **Description**: Optional sticky sessions
- **Feature**: **Health probes** | **Description**: Active health monitoring of backends
- **Feature**: **Traffic splitting** | **Description**: Weighted routing for blue-green deployments
- **Feature**: **Private Link origin** | **Description**: Connect to private backends

### Front Door Tiers

- **Tier**: **Standard** | **Key Feature**: CDN, basic routing, basic WAF
- **Tier**: **Premium** | **Key Feature**: Standard + enhanced WAF, Private Link origins, bot protection

### Front Door vs. Traffic Manager

- **Factor**: Layer | **Front Door**: L7 (HTTP/HTTPS) | **Traffic Manager**: DNS (any protocol)
- **Factor**: Failover speed | **Front Door**: Fast (connection-level) | **Traffic Manager**: Slow (DNS TTL)
- **Factor**: CDN | **Front Door**: Built-in | **Traffic Manager**: No
- **Factor**: WAF | **Front Door**: Built-in | **Traffic Manager**: No
- **Factor**: Non-HTTP protocols | **Front Door**: No | **Traffic Manager**: Yes
- **Factor**: SSL offload | **Front Door**: Yes | **Traffic Manager**: No
- **Factor**: Path-based routing | **Front Door**: Yes | **Traffic Manager**: No
- **Factor**: **Exam default for HTTP** | **Front Door**: **Yes** | **Traffic Manager**: Non-HTTP only

---

## 5. Traffic Manager (Global DNS)

### Routing Methods

- **Method**: **Priority** | **How**: Always route to primary; failover if unhealthy | **Use Case**: Active-passive DR
- **Method**: **Weighted** | **How**: Distribute by percentage | **Use Case**: Blue-green, canary
- **Method**: **Performance** | **How**: Route to lowest-latency endpoint | **Use Case**: Global UX optimization
- **Method**: **Geographic** | **How**: Route by user's geographic location | **Use Case**: Data sovereignty
- **Method**: **Multivalue** | **How**: Return multiple healthy endpoints | **Use Case**: Client-side load balancing
- **Method**: **Subnet** | **How**: Route by client subnet | **Use Case**: Enterprise routing policies

### Traffic Manager Limitations

- DNS-based: failover depends on TTL (typically 30-60 seconds)
- No CDN, WAF, or SSL offload
- Works with any protocol (not just HTTP)

---

## 6. Combined Patterns

### Global + Regional

[Diagram removed for audio]

### Multi-Tier Internal

[Diagram removed for audio]

---

## 7. Summary Decision Matrix

- **Scenario**: Internal VM load balancing (TCP/UDP) | **Service**: Azure Load Balancer (Standard, internal)
- **Scenario**: Internet-facing VM load balancing | **Service**: Azure Load Balancer (Standard, public)
- **Scenario**: Web app with URL routing and WAF (single region) | **Service**: Application Gateway WAF v2
- **Scenario**: Global web app with CDN and WAF | **Service**: Azure Front Door (Premium)
- **Scenario**: Multi-region failover (any protocol) | **Service**: Traffic Manager
- **Scenario**: Multi-region HTTP with fast failover | **Service**: Azure Front Door
- **Scenario**: NVA/firewall load balancing (all ports) | **Service**: Load Balancer with HA Ports
- **Scenario**: Blue-green deployment (HTTP) | **Service**: Front Door (weighted) or App Gateway (traffic splitting)
- **Scenario**: DNS-based geographic routing | **Service**: Traffic Manager (geographic)
- **Scenario**: Global + regional combined | **Service**: Front Door → App Gateway → Load Balancer

---

## Next Steps

- **Lab:** Deploy [front-door-global.bicep](../../infra/front-door-global.bicep)
- **Lab:** Deploy [application-gateway-waf.bicep](../../infra/application-gateway-waf.bicep)
- **Knowledge Check:** [Module 5 Knowledge Check](knowledge-check.md)

---

## References

- [Load Balancing Decision Tree](https://learn.microsoft.com/azure/architecture/guide/technology-choices/load-balancing-overview)
- [Azure Load Balancer](https://learn.microsoft.com/azure/load-balancer/load-balancer-overview)
- [Application Gateway](https://learn.microsoft.com/azure/application-gateway/overview)
- [Azure Front Door](https://learn.microsoft.com/azure/frontdoor/front-door-overview)
- [Traffic Manager](https://learn.microsoft.com/azure/traffic-manager/traffic-manager-overview)


---

<a id="module-5-knowledge-check"></a>

## Module 5: Knowledge Check

# Module 5 Knowledge Check: Network Solutions

**Target Score:** 80%+ to complete the course

---

## Instructions

Choose the BEST answer for each scenario. Network questions often combine topology, security, and load balancing requirements.

---

### Q1. Network Topology

A mid-sized company (10 VNets, 2 branch offices) needs a hub-spoke topology with centralized firewall, VPN gateway, and spoke isolation. Spokes should not communicate directly. What should you recommend?

- A. Azure Virtual WAN (Standard)
- B. Customer-managed hub-spoke with Azure Firewall and UDRs
- C. Full mesh VNet peering
- D. Azure Virtual WAN (Basic)

**Show Answer**

**Correct: B**

For small to medium deployments (< 30 VNets), a customer-managed hub-spoke is cost-effective and provides full control. Azure Firewall in the hub handles centralized filtering, and UDRs enforce spoke-to-hub routing. Spoke isolation is achieved by not peering spokes directly.

- **A is wrong:** Virtual WAN Standard works but is more expensive and complex than needed for 10 VNets.
- **C is wrong:** Full mesh peering allows direct spoke-to-spoke communication (violates isolation requirement) and doesn't scale.
- **D is wrong:** Virtual WAN Basic supports only S2S VPN, not ExpressRoute or transit routing.

---

### Q2. Hybrid Connectivity

A healthcare organization needs private connectivity from their on-premises datacenter to Azure. Traffic must NOT traverse the public internet. They need 2 Gbps bandwidth and connections to Azure services in their region. What should you recommend?

- A. VPN Gateway (VpnGw3)
- B. ExpressRoute (Standard)
- C. VPN Gateway with Azure Virtual WAN
- D. Azure Peering Service

**Show Answer**

**Correct: B**

ExpressRoute provides private connectivity that does NOT traverse the public internet. Standard SKU covers same geopolitical region. 2 Gbps circuits are available.

- **A is wrong:** VPN Gateway uses encrypted tunnels over the public internet — the requirement explicitly states "must NOT traverse the public internet."
- **C is wrong:** VPN through Virtual WAN still uses the internet.
- **D is wrong:** Peering Service improves internet routing to Microsoft services but still uses the internet path.

---

### Q3. Private Endpoints

A company uses Azure SQL Database and Azure Storage. They need to ensure these services are only accessible from within their VNet and from on-premises via ExpressRoute. They also need to prevent data exfiltration to other Azure SQL instances. What should you recommend?

- A. Service Endpoints on both services
- B. Private Endpoints for both services
- C. Azure Firewall with application rules
- D. NSG rules blocking internet traffic

**Show Answer**

**Correct: B**

Private Endpoints assign private IPs in the VNet, accessible via ExpressRoute from on-premises. They prevent data exfiltration because the endpoint points to a specific resource instance (not any SQL server). Service Endpoints don't prevent exfiltration and aren't accessible from on-premises.

- **A is wrong:** Service Endpoints don't prevent data exfiltration (can access any storage account in the service), and aren't accessible from on-premises.
- **C is wrong:** Azure Firewall controls traffic flow but doesn't give PaaS services private IPs for VNet/on-prem access.
- **D is wrong:** NSGs can't restrict traffic to specific PaaS resource instances.

---

### Q4. NSG vs. Firewall

A company needs to filter traffic at the subnet level within a spoke VNet. They need to allow HTTP traffic from web VMs to app VMs using logical groupings, without managing individual IP addresses. What should you use?

- A. Azure Firewall with network rules
- B. NSG with Application Security Groups (ASGs)
- C. Azure Firewall with application rules
- D. NSG with IP-based rules

**Show Answer**

**Correct: B**

NSGs with ASGs allow you to define rules using logical groups (WebASG → AppASG on port 80/443) without managing individual IP addresses. This is the simplest and most cost-effective solution for subnet-level filtering.

- **A is wrong:** Azure Firewall is centralized (hub-level), more expensive, and overkill for simple subnet-level rules.
- **C is wrong:** Same as A — application rules filter by FQDN, unnecessary for VM-to-VM traffic.
- **D is wrong:** IP-based NSG rules work but require manual IP management, violating the "without managing individual IPs" requirement.

---

### Q5. WAF Placement

A company runs a global e-commerce website across East US and West Europe. They need OWASP protection, CDN caching for static assets, and fast failover between regions. What should you recommend?

- A. Application Gateway WAF v2 in each region
- B. Azure Front Door Premium with WAF
- C. Traffic Manager with Application Gateway WAF in each region
- D. Azure CDN (Standard) with NSG rules

**Show Answer**

**Correct: B**

Azure Front Door Premium provides global L7 load balancing, built-in CDN, WAF with OWASP protection, and fast connection-level failover. Single service covers all three requirements.

- **A is wrong:** Application Gateway is regional. Two separate WAF instances don't provide global load balancing or CDN.
- **C is wrong:** Traffic Manager + App Gateway works but has slower DNS-based failover, no built-in CDN, and more complexity.
- **D is wrong:** Azure CDN doesn't provide WAF or intelligent routing. NSGs don't protect against OWASP attacks.

---

### Q6. Load Balancing

An application has a web tier (HTTP), an application tier (TCP port 8080), and a database tier. The web tier needs URL-based routing and SSL offload. The app tier just needs TCP load balancing. What combination should you use?

- A. Azure Front Door for web tier, Load Balancer for app tier
- B. Application Gateway for web tier, Internal Load Balancer for app tier
- C. Load Balancer for both tiers
- D. Application Gateway for both tiers

**Show Answer**

**Correct: B**

Application Gateway provides L7 features (URL routing, SSL offload) for the web tier. Internal Load Balancer efficiently handles TCP load balancing for the app tier. Right tool for each tier.

- **A is wrong:** Front Door is global — overkill for a single-region internal architecture.
- **C is wrong:** Load Balancer is L4 only — can't do URL-based routing or SSL offload.
- **D is wrong:** Application Gateway handles L7 HTTP/HTTPS only. TCP 8080 is better served by Load Balancer (simpler, lower latency).

---

### Q7. DDoS Protection

A company has 3 public IP addresses in Azure. They want DDoS mitigation beyond the default infrastructure protection. They want the most cost-effective option. What should you recommend?

- A. DDoS Network Protection
- B. DDoS IP Protection
- C. Azure Firewall Premium
- D. NSG rules to block suspicious IPs

**Show Answer**

**Correct: B**

DDoS IP Protection costs ~$199/month per IP (3 × $199 = $597/month). DDoS Network Protection costs ~$2,944/month regardless of IP count. For 3 IPs, IP Protection is significantly cheaper.

- **A is wrong:** Network Protection at $2,944/month is much more expensive for only 3 IPs. It becomes cost-effective at ~15+ IPs.
- **C is wrong:** Azure Firewall provides network filtering, not DDoS protection specifically.
- **D is wrong:** NSG rules can block known IPs but can't handle volumetric DDoS attacks dynamically.

---

### Q8. DNS Resolution

A company has a hub-spoke network with Private Endpoints for Azure SQL and Storage. On-premises servers connected via ExpressRoute need to resolve the `privatelink.*` DNS zones. What should you deploy?

- A. Custom DNS server in hub VNet
- B. Azure DNS Private Resolver with inbound endpoint
- C. Conditional forwarders on on-premises DNS only
- D. Public DNS zone with A records

**Show Answer**

**Correct: B**

Azure DNS Private Resolver with an inbound endpoint allows on-premises DNS servers to forward `privatelink.*` queries to Azure, which resolves them using the Private DNS zones linked to the VNet.

- **A is wrong:** Custom DNS VMs work but require managing OS, patching, and HA — Private Resolver is a managed service.
- **C is wrong:** On-prem conditional forwarders need something in Azure to forward TO — the Private Resolver's inbound endpoint serves as that target.
- **D is wrong:** Public DNS would expose private IP addresses publicly and bypass the purpose of Private Endpoints.

---

### Q9. Azure Bastion

A company's security policy requires that no VMs have public IP addresses. Administrators need to RDP into Windows VMs and SSH into Linux VMs from their laptops using native RDP/SSH clients (not just the Azure portal). What Bastion tier do you need?

- A. Basic
- B. Standard
- C. Premium
- D. Bastion is not needed — use JIT VM access

**Show Answer**

**Correct: B**

Standard tier supports native client connectivity (az network bastion rdp/ssh commands) in addition to portal access. Basic tier only supports portal-based RDP/SSH.

- **A is wrong:** Basic tier only supports browser-based access via Azure portal, not native RDP/SSH clients.
- **C is wrong:** Premium adds session recording but Standard is sufficient for native client support.
- **D is wrong:** JIT VM access temporarily opens NSG rules but still requires a public IP on the VM, violating the security policy.

---

### Q10. Multi-Region Architecture

A company deploys a non-HTTP application (custom TCP protocol) across East US and West Europe. They need automatic failover to the healthy region with the lowest latency. What global load balancing solution should they use?

- A. Azure Front Door
- B. Azure Traffic Manager with Performance routing
- C. Azure Application Gateway
- D. Azure Load Balancer (Standard)

**Show Answer**

**Correct: B**

Traffic Manager supports any protocol (including custom TCP) with DNS-based routing. Performance routing directs users to the lowest-latency endpoint. Health probes detect failures for failover.

- **A is wrong:** Front Door only supports HTTP/HTTPS, not custom TCP protocols.
- **C is wrong:** Application Gateway is regional, not global.
- **D is wrong:** Standard Load Balancer is regional. Cross-region LB exists but is simpler than needed; Traffic Manager with Performance routing is the standard recommendation.

---

## Scoring

- **Score**: 9-10 / 10 (90-100%) | **Next Step**: Excellent! Proceed to final exam prep
- **Score**: 8 / 10 (80%) | **Next Step**: Good. Review missed areas, then do full practice exam
- **Score**: 6-7 / 10 (60-70%) | **Next Step**: Review the relevant lessons before the practice exam
- **Score**: Below 6 / 10 (<60%) | **Next Step**: Re-study the full module before retaking

---

## Continue Learning

- **MS Learn Path:** [Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/) (network module)
- **Case Study:** [Design a network solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/08-Logging.html)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Final Step:** Take the [full practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15), review [practice questions](../../docs/practice-questions.md), then [schedule your exam](https://learn.microsoft.com/credentials/certifications/exams/az-305/).


---

