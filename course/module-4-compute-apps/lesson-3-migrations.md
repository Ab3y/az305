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

```
Strategy ──> Plan ──> Ready ──> Adopt ──> Govern ──> Manage
                        │         │
                        │         ├── Migrate
                        │         └── Innovate
                        │
                        └── Landing Zone
```

| Phase | Key Activity | Deliverable |
|-------|-------------|-------------|
| **Strategy** | Define business justification | Business case, motivations |
| **Plan** | Assess digital estate, rationalize workloads | Migration plan, 5 Rs classification |
| **Ready** | Set up Azure landing zone | Subscriptions, networking, identity |
| **Migrate** | Rehost/refactor workloads | Running workloads in Azure |
| **Innovate** | Rearchitect/rebuild for cloud-native | Modernized applications |
| **Govern** | Compliance, cost, security baselines | Policies, guardrails |
| **Manage** | Operations baseline | Monitoring, patching, SLA management |

### The 5 Rs of Rationalization

| Strategy | Description | Exam Scenario |
|----------|-------------|--------------|
| **Rehost** (lift-and-shift) | Move to Azure VMs as-is | "No code changes," "urgent timeline" |
| **Refactor** | Move to PaaS with minimal changes | "Use App Service instead of VM" |
| **Rearchitect** | Redesign for cloud-native features | "Microservices," "event-driven" |
| **Rebuild** | Rewrite from scratch | "Legacy, no source code" |
| **Replace** | Switch to SaaS | "Use Dynamics 365 instead of custom CRM" |

### Migration Decision Flow

```
Can the application run on Azure as-is?
  ├── YES ──> Rehost (VMs)
  │            └── Later: Refactor to PaaS?
  └── NO
        Can it be moved to PaaS with minor changes?
          ├── YES ──> Refactor (App Service, SQL MI)
          └── NO
                Is the code maintainable?
                  ├── YES ──> Rearchitect (modernize)
                  └── NO
                        Is there a SaaS equivalent?
                          ├── YES ──> Replace
                          └── NO  ──> Rebuild
```

---

## 2. Azure Migrate

### Components

| Component | Purpose |
|-----------|---------|
| **Azure Migrate Hub** | Central orchestration portal |
| **Discovery and assessment** | Discover on-prem VMs, assess readiness |
| **Server Migration** | Agentless or agent-based VM replication |
| **Database Migration** | Azure Database Migration Service (DMS) |
| **Web App Migration** | App Service Migration Assistant |
| **Data Box** | Offline bulk data transfer |

### Assessment Outputs

| Assessment | What It Tells You |
|-----------|------------------|
| **Azure readiness** | Can the VM run on Azure? |
| **Right-sizing** | Recommended VM size |
| **Cost estimate** | Monthly Azure cost |
| **Dependency analysis** | What connects to what (agent-based or agentless) |
| **SQL assessment** | SQL Server readiness for SQL DB, SQL MI, or SQL on VM |

### Migration Approaches

| Approach | Method | When |
|----------|--------|------|
| **Agentless** | Azure Migrate appliance, no agent on VMs | VMware VMs, simpler setup |
| **Agent-based** | Mobility agent on each VM | Physical servers, Hyper-V, complex scenarios |
| **Azure Site Recovery** | Built-in replication engine | Fallback, non-VMware |

---

## 3. Database Migration

### Azure Database Migration Service (DMS)

| Migration Path | Source | Target | Mode |
|---------------|--------|--------|------|
| SQL Server → SQL Database | On-prem SQL Server | Azure SQL Database | Offline / Online |
| SQL Server → SQL MI | On-prem SQL Server | SQL Managed Instance | Online (near-zero downtime) |
| PostgreSQL → PostgreSQL | On-prem PostgreSQL | Azure Database for PostgreSQL | Online |
| MySQL → MySQL | On-prem MySQL | Azure Database for MySQL | Online |
| MongoDB → Cosmos DB | On-prem MongoDB | Cosmos DB API for MongoDB | Online |

### Other Migration Tools

| Tool | Purpose |
|------|---------|
| **Data Migration Assistant (DMA)** | Assess SQL Server for compatibility issues |
| **Azure SQL Migration extension** | VS Code extension for SQL assessment + migration |
| **Azure Data Box** | Ship physical devices for large offline data transfer |
| **AzCopy** | CLI tool for fast blob/file transfers |
| **Storage Migration Service** | Migrate Windows file servers to Azure Files |

### Migration Mode: Online vs. Offline

| Mode | How | Downtime | Use Case |
|------|-----|----------|----------|
| **Offline** | Full backup + restore | Hours | Acceptable maintenance window |
| **Online** | Initial sync + continuous replication + cutover | Minutes | Business-critical, minimal downtime |

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

```
Root Management Group
  ├── Platform
  │     ├── Identity (domain controllers, Azure AD Connect)
  │     ├── Management (Log Analytics, Automation, Defender)
  │     └── Connectivity (hub VNet, VPN/ExpressRoute, Firewall)
  └── Landing Zones
        ├── Production
        │     ├── Subscription: App A
        │     └── Subscription: App B
        └── Non-Production
              ├── Subscription: Dev
              └── Subscription: Test
```

### Landing Zone Implementation Options

| Option | Scope | Time | Best For |
|--------|-------|------|----------|
| **Start small** | Single subscription | Days | POC, small org |
| **Enterprise-scale** | Full CAF, multi-subscription | Weeks | Enterprise, regulated industries |
| **CAF Terraform module** | IaC-driven | Days-weeks | Existing Terraform teams |
| **Azure Landing Zone Accelerator** | Portal-guided deployment | Hours | Quick enterprise setup |

---

## 5. Application Migration Patterns

### Web Application Migration

| Source | Target | Tool | Exam Keyword |
|--------|--------|------|-------------|
| IIS on Windows Server | App Service | App Service Migration Assistant | "Migrate .NET web app" |
| Tomcat on Linux | App Service (Linux) | App Service Migration Assistant | "Migrate Java web app" |
| Containerized app | Container Apps or AKS | Docker push + deploy | "Migrate containers" |
| Spring Boot | Azure Spring Apps | Spring migration guide | "Migrate Spring app" |

### Data Migration Strategies

| Data Type | Strategy | Service |
|-----------|----------|---------|
| SQL Server databases | Online migration | DMS |
| File shares | Storage Migration Service | Azure Files |
| Large datasets (>10 TB) | Offline transfer | Azure Data Box |
| Blob data | AzCopy / Data Factory | Storage Account |
| NoSQL (MongoDB) | Online migration | DMS to Cosmos DB |

---

## 6. Summary Decision Matrix

| Scenario | Solution |
|----------|---------|
| Discover and assess on-prem VMs | Azure Migrate (discovery + assessment) |
| Migrate VMware VMs to Azure | Azure Migrate (agentless) |
| Migrate SQL Server to SQL MI (minimal downtime) | DMS online migration |
| Move 50 TB of data to Azure | Azure Data Box |
| Migrate .NET web app to PaaS | App Service Migration Assistant |
| Set up enterprise Azure environment | CAF Landing Zone Accelerator |
| "No code changes allowed" | Rehost (VMs) |
| "Minimize management overhead" | Refactor to PaaS |
| "Need microservices architecture" | Rearchitect (Container Apps/AKS) |
| "Replace custom CRM" | Replace with SaaS (Dynamics 365) |

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
