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

| Component | Purpose | When to Use |
|-----------|---------|------------|
| **Metrics** | Numeric time-series data (CPU, memory, requests) | Real-time performance monitoring, auto-scale rules |
| **Logs** | Structured event data stored in Log Analytics | Complex querying, long-term analysis, compliance |
| **Alerts** | Automated notifications and actions | Incident response, auto-remediation |
| **Workbooks** | Interactive visual reports | Dashboards, capacity planning |
| **Application Insights** | APM for application telemetry | Distributed tracing, performance profiling |

### Architecture Decision: Where Does Data Go?

```
Azure Resource ──> Diagnostic Setting ──> ┬──> Log Analytics (query & alert)
                                          ├──> Event Hub (stream to SIEM)
                                          └──> Storage Account (archive)

VM/On-Premises ──> Azure Monitor Agent ──> Data Collection Rule ──> Log Analytics
```

**Key Insight:** A single resource can have multiple diagnostic settings pointing to different destinations simultaneously. This is the "fan-out" pattern.

---

## 2. Log Analytics Workspace Design

### Topology Decision Tree

```
How many teams/subscriptions?
  │
  ├── Small org (1-5 subs) ──> Single workspace
  │
  ├── Enterprise (5+ subs) ──> Single centralized workspace
  │     with resource-context RBAC
  │
  └── Regulatory/sovereignty ──> Separate workspace per
        requirements              compliance boundary
```

### Workspace Design Best Practices

| Decision | Recommendation | Rationale |
|----------|---------------|-----------|
| Number of workspaces | Start with **one** | Simplifies management, enables cross-resource queries |
| Access model | **Resource-context** RBAC | Users see logs for resources they already have access to |
| Region placement | Same region as resources | Minimizes latency and egress costs |
| Retention | 90 days interactive, archive for 7+ years | Balance cost and compliance |
| Pricing | Commitment tiers (100+ GB/day) | Up to 30% savings over pay-as-you-go |

### Retention Tiers

| Tier | Duration | Cost | Query Performance |
|------|----------|------|------------------|
| **Interactive** | 30-730 days (default 30) | Standard ingestion + retention | Full KQL |
| **Archive** | Up to 12 years | ~$0.02/GB/month | Restore or search jobs (slower) |
| **Storage Account** | Unlimited | ~$0.01/GB/month (cool) | Not queryable (export/rehydrate) |

**Exam Trap:** Log Analytics interactive retention max is 730 days (2 years), NOT 7 years. For 7+ year compliance, use Storage Account or archive tier.

---

## 3. Routing Logs

### Diagnostic Settings Configuration

Every Azure resource can emit three types of telemetry via diagnostic settings:

| Telemetry Type | Examples | Destination Options |
|---------------|----------|-------------------|
| **Activity Logs** | Resource creation, role assignments, policy events | Log Analytics, Event Hub, Storage |
| **Resource Logs** | SQL query performance, Key Vault access, App Service requests | Log Analytics, Event Hub, Storage |
| **Platform Metrics** | CPU utilization, disk IOPS, network bytes | Log Analytics (for long-term trending) |

### Azure Monitor Agent (AMA)

AMA replaced the legacy Log Analytics Agent (MMA, retired August 2024).

| Feature | Azure Monitor Agent |
|---------|-------------------|
| Supported OS | Windows, Linux |
| Configuration | Data Collection Rules (DCRs) |
| Multi-homing | Yes (multiple workspaces) |
| Auth model | Managed identity |
| Deployment | Azure Policy (recommended), ARM/Bicep, manual |

### Data Collection Rules (DCRs)

DCRs define:
- **What** data to collect (Windows events, Syslog, performance counters, custom logs)
- **Where** to send it (Log Analytics workspace)
- **How** to transform it (KQL transforms for filtering/enrichment at ingestion)

```
DCR Configuration:
  Data Sources:
    - Windows Event Logs (System, Application, Security)
    - Performance Counters (CPU, Memory, Disk, Network)
    - Syslog (Linux: auth, daemon, kern)
  Destinations:
    - Log Analytics Workspace (primary)
  Transformations:
    - Filter: SecurityEvent | where EventID in (4624, 4625, 4648)
    - Parse: Custom log format extraction
```

---

## 4. Monitoring Solutions

### Azure Monitor Alerts

| Alert Type | Signal Source | Example |
|-----------|-------------|---------|
| **Metric alerts** | Platform metrics | CPU > 90% for 5 minutes |
| **Log alerts** | Log Analytics queries | Error count > 100 in 1 hour |
| **Activity log alerts** | Activity log events | Resource deleted, role assigned |
| **Service Health alerts** | Azure service issues | Planned maintenance, outages |
| **Resource Health alerts** | Individual resource status | VM unhealthy |

**Action Groups** define what happens when an alert fires:
- Email/SMS/Voice
- Azure Function / Logic App / Webhook
- ITSM connector (ServiceNow, etc.)
- Automation Runbook

### Application Insights

| Feature | Design Impact |
|---------|--------------|
| **Workspace-based mode** | Required for new deployments (classic deprecated) |
| **Sampling** | Reduces cost; adaptive sampling for high-traffic apps |
| **Distributed tracing** | Tracks requests across microservices |
| **Availability tests** | URL ping or multi-step web tests from global locations |
| **Live Metrics** | Real-time performance stream (no storage cost) |
| **Smart Detection** | AI-powered anomaly alerts |

**Cost Control Pattern:**
```
High-traffic app? ──> Enable adaptive sampling (default: keep 5 events/sec)
Verbose logging? ──> Use "Basic" log plan (lower cost, limited queries)
Dev/test? ──> Set daily cap to prevent budget surprises
```

### Microsoft Sentinel (SIEM + SOAR)

When the exam mentions "security monitoring" or "threat detection," Sentinel is the answer:
- Built on Log Analytics workspace
- 200+ data connectors
- Built-in AI/ML for threat detection
- Automated response with playbooks (Logic Apps)

---

## 5. Decision Summary

### "Which monitoring service?" Quick Reference

| Scenario | Service |
|----------|---------|
| Infrastructure metrics and alerts | Azure Monitor |
| Log querying and analysis | Log Analytics |
| Application performance | Application Insights |
| Security analytics and SIEM | Microsoft Sentinel |
| Network diagnostics | Network Watcher |
| Service availability | Service Health |
| Individual resource status | Resource Health |

---

## Key Terms Glossary

| Term | Definition |
|------|-----------|
| **DCR** | Data Collection Rule — defines data sources and destinations for Azure Monitor Agent |
| **AMA** | Azure Monitor Agent — the current agent for collecting VM/on-premises telemetry |
| **KQL** | Kusto Query Language — query language for Log Analytics and related services |
| **Resource-context RBAC** | Access to log data based on Azure resource permissions, not workspace permissions |
| **Diagnostic settings** | Configuration that routes Azure resource logs/metrics to Log Analytics, Event Hub, or Storage |
| **Commitment tier** | Pre-purchased Log Analytics capacity at a discount (100, 200, 300, ... GB/day) |

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
