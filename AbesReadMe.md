# Abe's AZ-305 Repo Navigation Guide

> **Exam:** AZ-305 — Designing Microsoft Azure Infrastructure Solutions  
> **Passing Score:** 700 / 1000 | **Questions:** 40–60 | **Duration:** 120 min  
> **Prerequisite:** AZ-104 (Azure Administrator)

---

## Repo Map at a Glance

```
az305/
├── AbesReadMe.md              ← YOU ARE HERE
├── course/                    ← Self-paced training course (start here)
│   ├── syllabus.md            ← Course entry point, 12-week study plan
│   ├── hands-on-labs.md       ← Lab index with official case studies
│   ├── module-1-identity-governance/
│   ├── module-2-data-storage/
│   ├── module-3-business-continuity/
│   ├── module-4-compute-apps/
│   └── module-5-networking/
├── docs/                      ← Exam reference materials
│   ├── az305-objective-domain.md
│   ├── practice-questions.md
│   ├── quick-reference-cards.md
│   └── reference-architectures.md
├── infra/                     ← Bicep/ARM IaC templates (30+ labs)
│   ├── domain1-identity/
│   ├── domain4-compute/
│   └── *.bicep / *.parameters.json
├── scripts/                   ← Runnable scripts by language
│   ├── az-cli/        (8 scripts)
│   ├── powershell/    (11 scripts)
│   ├── kql/           (6 query files)
│   └── examples/      (9 multi-language examples)
├── images/                    ← 15 Mermaid architecture diagrams
├── azure-architect-library/   ← CAF, WAF, Architecture Center summaries
├── az305-demo/                ← Live demo environment & topology diagrams
├── az305-course-flow.md       ← Original 5-segment instructor schedule
├── az305-punchlist.md         ← Tim Warner's demo punchlist
├── CLAUDE.md                  ← AI assistant guidance for this repo
└── README.md                  ← Original repo README
```

---

## Exam Domain Weights

| Domain | Weight | Course Module |
|--------|--------|---------------|
| Design identity, governance, and monitoring | 25–30% | Module 1 |
| Design data storage solutions | 20–25% | Module 2 |
| Design business continuity solutions | 15–20% | Module 3 |
| Design infrastructure solutions | 30–35% | Modules 4 & 5 |

---

## Step-by-Step Study Plan

### Phase 0 — Orient (Day 1)

1. **Read this file** to understand the repo layout.
2. **Open [`course/syllabus.md`](course/syllabus.md)** — your course home page with the 12-week study plan, official MS Learn paths, and case study links.
3. **Skim [`docs/az305-objective-domain.md`](docs/az305-objective-domain.md)** to see every exam objective in one place.
4. **Bookmark the practice assessment:** <https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15>

---

### Phase 1 — Module 1: Identity, Governance & Monitoring (Weeks 1–3)

**Exam weight: 25–30%** — Covers Entra ID, RBAC, managed identities, Azure Policy, Azure Monitor, and governance.

| Order | File | What You'll Learn |
|-------|------|-------------------|
| 1 | [`module-1-identity-governance/overview.md`](course/module-1-identity-governance/overview.md) | Module objectives, MS Learn links, case studies |
| 2 | [`lesson-1-logging-monitoring.md`](course/module-1-identity-governance/lesson-1-logging-monitoring.md) | Azure Monitor, Log Analytics, App Insights, alerts, Sentinel |
| 3 | [`lesson-2-auth.md`](course/module-1-identity-governance/lesson-2-auth.md) | Entra ID, B2B, hybrid identity, RBAC, managed identity, Conditional Access |
| 4 | [`lesson-3-governance.md`](course/module-1-identity-governance/lesson-3-governance.md) | Management groups, Azure Policy, tagging, PIM, landing zones |
| 5 | [`knowledge-check.md`](course/module-1-identity-governance/knowledge-check.md) | 10 scenario-based questions with answers |

**Hands-on labs to run:**

| Bicep Template | Service |
|----------------|---------|
| `infra/managed-identity.bicep` | User-assigned managed identity |
| `infra/custom-rbac-role.bicep` | Custom RBAC role definition |
| `infra/azure-policy-initiative.bicep` | Policy initiative |
| `infra/keyvault-with-private-link.bicep` | Key Vault + Private Link |
| `infra/log-analytics-workspace.bicep` | Log Analytics workspace |

**Scripts to explore:**

- `scripts/powershell/Configure-ConditionalAccess.ps1`
- `scripts/powershell/Enable-EntraPIM.ps1`
- `scripts/powershell/Configure-PolicyInitiative.ps1`
- `scripts/powershell/New-ManagedIdentity.ps1`
- `scripts/az-cli/create-rbac-assignments.sh`
- `scripts/kql/security-audit.kql`

---

### Phase 2 — Module 2: Data Storage (Weeks 4–5)

**Exam weight: 20–25%** — Covers SQL Database, Cosmos DB, Blob Storage, Data Lake, and data integration.

| Order | File | What You'll Learn |
|-------|------|-------------------|
| 1 | [`module-2-data-storage/overview.md`](course/module-2-data-storage/overview.md) | Module objectives, MS Learn links, case studies |
| 2 | [`lesson-1-relational-data.md`](course/module-2-data-storage/lesson-1-relational-data.md) | SQL DB vs SQL MI, DTU vs vCore, elastic pools, encryption |
| 3 | [`lesson-2-non-relational-data.md`](course/module-2-data-storage/lesson-2-non-relational-data.md) | Cosmos DB APIs, partitioning, consistency, Blob, ADLS Gen2 |
| 4 | [`lesson-3-data-integration.md`](course/module-2-data-storage/lesson-3-data-integration.md) | Data Factory, Synapse, Databricks, Stream Analytics |
| 5 | [`knowledge-check.md`](course/module-2-data-storage/knowledge-check.md) | 10 scenario-based questions with answers |

**Hands-on labs to run:**

| Bicep Template | Service |
|----------------|---------|
| `infra/sql-database-elastic-pool.bicep` | SQL DB + elastic pool |
| `infra/sql-failover-group.bicep` | SQL failover group |
| `infra/cosmosdb-multi-region.bicep` | Cosmos DB multi-region |
| `infra/storage-account-tiered.bicep` | Storage with lifecycle tiers |

**Scripts to explore:**

- `scripts/powershell/New-CosmosDBAccount.ps1`
- `scripts/powershell/Set-StorageLifecycle.ps1`
- `scripts/az-cli/setup-sql-failover-group.sh`
- `scripts/kql/cost-analysis.kql`

---

### Phase 3 — Module 3: Business Continuity (Weeks 6–7)

**Exam weight: 15–20%** — Covers backup, disaster recovery, SLA calculations, and high availability patterns.

| Order | File | What You'll Learn |
|-------|------|-------------------|
| 1 | [`module-3-business-continuity/overview.md`](course/module-3-business-continuity/overview.md) | Module objectives, MS Learn links |
| 2 | [`lesson-1-backup-dr.md`](course/module-3-business-continuity/lesson-1-backup-dr.md) | RTO/RPO, Azure Backup, ASR, geo-redundancy, multi-region |
| 3 | [`lesson-2-high-availability.md`](course/module-3-business-continuity/lesson-2-high-availability.md) | SLA tiers, composite SLA, availability zones/sets, HA patterns |
| 4 | [`knowledge-check.md`](course/module-3-business-continuity/knowledge-check.md) | 10 scenario-based questions with answers |

**Hands-on labs to run:**

| Bicep Template | Service |
|----------------|---------|
| `infra/recovery-services-vault.bicep` | Recovery Services vault |
| `infra/site-recovery-config.bicep` | Azure Site Recovery |

**Scripts to explore:**

- `scripts/az-cli/configure-backup-policy.sh`

---

### Phase 4 — Module 4: Compute & Application Architecture (Weeks 8–9)

**Exam weight: Part of 30–35%** — Covers VMs, App Service, Container Apps, AKS, Functions, messaging, APIM, and migrations.

| Order | File | What You'll Learn |
|-------|------|-------------------|
| 1 | [`module-4-compute-apps/overview.md`](course/module-4-compute-apps/overview.md) | Module objectives, MS Learn links, case studies |
| 2 | [`lesson-1-compute.md`](course/module-4-compute-apps/lesson-1-compute.md) | VMs, App Service, Container Apps, AKS, Functions decision trees |
| 3 | [`lesson-2-app-architecture.md`](course/module-4-compute-apps/lesson-2-app-architecture.md) | Service Bus, Event Grid, Event Hubs, Redis, APIM, microservices |
| 4 | [`lesson-3-migrations.md`](course/module-4-compute-apps/lesson-3-migrations.md) | CAF phases, 5 Rs, Azure Migrate, DMS, landing zones |
| 5 | [`knowledge-check.md`](course/module-4-compute-apps/knowledge-check.md) | 10 scenario-based questions with answers |

**Hands-on labs to run:**

| Bicep Template | Service |
|----------------|---------|
| `infra/container-apps-environment.bicep` | Container Apps environment |
| `infra/aks-cluster.bicep` | AKS cluster |
| `infra/apim-with-backends.bicep` | API Management |
| `infra/domain4-compute/vm-compute-fleet.bicep` | VM compute fleet |
| `infra/domain4-compute/logic-app-conditional.bicep` | Logic App |

**Scripts to explore:**

- `scripts/az-cli/deploy-container-apps.sh`
- `scripts/az-cli/deploy-apim.sh`
- `scripts/powershell/Deploy-LandingZone.ps1`
- `scripts/powershell/Export-ResourceInventory.ps1`

---

### Phase 5 — Module 5: Networking (Weeks 10–11)

**Exam weight: Part of 30–35%** — Covers VNet design, hub-spoke, NSG, Firewall, Private Endpoints, load balancing, and Front Door.

| Order | File | What You'll Learn |
|-------|------|-------------------|
| 1 | [`module-5-networking/overview.md`](course/module-5-networking/overview.md) | Module objectives, MS Learn links, case study |
| 2 | [`lesson-1-network-topology.md`](course/module-5-networking/lesson-1-network-topology.md) | VNet design, hub-spoke, Virtual WAN, peering, ExpressRoute, DNS |
| 3 | [`lesson-2-network-security.md`](course/module-5-networking/lesson-2-network-security.md) | NSG, ASG, Azure Firewall, WAF, Private Endpoints, DDoS, Bastion |
| 4 | [`lesson-3-load-balancing.md`](course/module-5-networking/lesson-3-load-balancing.md) | Load Balancer, App Gateway, Front Door, Traffic Manager |
| 5 | [`knowledge-check.md`](course/module-5-networking/knowledge-check.md) | 10 scenario-based questions with answers |

**Hands-on labs to run:**

| Bicep Template | Service |
|----------------|---------|
| `infra/hub-spoke-network.bicep` | Hub-spoke VNet topology |
| `infra/application-gateway-waf.bicep` | Application Gateway + WAF |
| `infra/front-door-global.bicep` | Azure Front Door |
| `infra/private-endpoint-services.bicep` | Private Endpoints |

**Scripts to explore:**

- `scripts/az-cli/deploy-hub-spoke.sh`
- `scripts/az-cli/create-private-endpoints.sh`
- `scripts/powershell/Test-PrivateEndpoint.ps1`
- `scripts/kql/network-diagnostics.kql`

---

### Phase 6 — Review & Exam Prep (Week 12)

1. **Re-take all knowledge checks** — aim for 90%+ on every module.
2. **Review quick reference cards:** [`docs/quick-reference-cards.md`](docs/quick-reference-cards.md) — comparison tables and cheat sheets.
3. **Study reference architectures:** [`docs/reference-architectures.md`](docs/reference-architectures.md) — 9 key architectures mapped to exam objectives.
4. **Drill practice questions:** [`docs/practice-questions.md`](docs/practice-questions.md) — 100+ questions with explanations.
5. **Take the official practice assessment:** <https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15>
6. **Review Mermaid diagrams** in `images/` — visualize architectures (use a Mermaid preview extension).
7. **Read architecture library:** [`azure-architect-library/`](azure-architect-library/) — CAF, WAF, and Architecture Center summaries.

---

## How to Deploy Bicep Labs

Every Bicep template in `infra/` has a matching `.parameters.json` file. Deploy with:

```bash
# 1. Log in
az login

# 2. Create a resource group (or use existing)
az group create --name rg-az305-labs --location eastus

# 3. Deploy a template
az deployment group create \
  --resource-group rg-az305-labs \
  --template-file infra/<template-name>.bicep \
  --parameters infra/<template-name>.parameters.json

# 4. Clean up when done (IMPORTANT — avoid charges)
az group delete --name rg-az305-labs --yes --no-wait
```

> **Cost tip:** Always delete your resource group when you're done with a lab. Use the Azure Cost Management blade to monitor spending.

---

## Supporting Files Reference

| File | Purpose |
|------|---------|
| [`az305-course-flow.md`](az305-course-flow.md) | Tim Warner's original 5-segment live instructor schedule |
| [`az305-punchlist.md`](az305-punchlist.md) | Demo punchlist for live sessions |
| [`CLAUDE.md`](CLAUDE.md) | AI assistant guidance for this repo |
| [`az305-demo/`](az305-demo/) | Live demo environment docs & topology diagrams |
| [`infra/README.md`](infra/README.md) | Bicep template catalog and usage notes |
| [`scripts/README.md`](scripts/README.md) | Script inventory and execution guide |

---

## Mermaid Diagrams (images/)

Open these `.mmd` files with a Mermaid preview extension in VS Code to visualize:

| Diagram | Architecture |
|---------|-------------|
| `zero-trust-identity.mmd` | Zero Trust identity flow |
| `governance-hierarchy.mmd` | Management group / subscription hierarchy |
| `logging-architecture.mmd` | Azure Monitor / Log Analytics pipeline |
| `data-platform.mmd` | Data platform with Synapse, ADF, ADLS |
| `cosmosdb-global.mmd` | Cosmos DB multi-region distribution |
| `sql-ha-dr.mmd` | SQL HA / DR with failover groups |
| `backup-architecture.mmd` | Azure Backup architecture |
| `site-recovery-dr.mmd` | Azure Site Recovery DR flow |
| `high-availability-patterns.mmd` | Multi-zone / multi-region HA patterns |
| `container-apps-microservices.mmd` | Container Apps microservices topology |
| `api-architecture.mmd` | APIM + backend APIs |
| `migration-landing-zone.mmd` | Migration landing zone layout |
| `hub-spoke-network.mmd` | Hub-spoke network topology |
| `private-link-topology.mmd` | Private Link / Private Endpoint flow |

---

## Scripts Inventory

### Azure CLI (`scripts/az-cli/`) — 8 scripts

| Script | Module |
|--------|--------|
| `create-rbac-assignments.sh` | Module 1 |
| `configure-diagnostic-settings.sh` | Module 1 |
| `setup-sql-failover-group.sh` | Module 2 |
| `configure-backup-policy.sh` | Module 3 |
| `deploy-container-apps.sh` | Module 4 |
| `deploy-apim.sh` | Module 4 |
| `deploy-hub-spoke.sh` | Module 5 |
| `create-private-endpoints.sh` | Module 5 |

### PowerShell (`scripts/powershell/`) — 11 scripts

| Script | Module |
|--------|--------|
| `Configure-ConditionalAccess.ps1` | Module 1 |
| `Remove-ConditionalAccess.ps1` | Module 1 |
| `Enable-EntraPIM.ps1` | Module 1 |
| `Configure-PolicyInitiative.ps1` | Module 1 |
| `New-ManagedIdentity.ps1` | Module 1 |
| `Enable-DefenderForCloud.ps1` | Module 1 |
| `New-CosmosDBAccount.ps1` | Module 2 |
| `Set-StorageLifecycle.ps1` | Module 2 |
| `Deploy-LandingZone.ps1` | Module 4 |
| `Export-ResourceInventory.ps1` | Module 4 |
| `Test-PrivateEndpoint.ps1` | Module 5 |

### KQL Queries (`scripts/kql/`) — 6 files

| Query File | Use Case |
|------------|----------|
| `security-audit.kql` | Security posture review |
| `application-insights.kql` | App performance & errors |
| `cost-analysis.kql` | Spending & resource cost queries |
| `performance-analysis.kql` | VM/container performance |
| `network-diagnostics.kql` | NSG flow logs & connectivity |
| `resource-changes.kql` | Azure Activity log / change tracking |

### Examples (`scripts/examples/`) — 9 multi-language samples

| Example | Language |
|---------|----------|
| `01-identity-governance.ps1` | PowerShell |
| `02-monitoring-logging.sh` | Bash |
| `03-data-storage.ps1` | PowerShell |
| `04-business-continuity.sh` | Bash |
| `05-compute-solutions.ps1` | PowerShell |
| `06-networking.sh` | Bash |
| `07-kql-monitoring-queries.kql` | KQL |
| `08-python-azure-sdk.py` | Python |
| `09-bicep-patterns.bicep` | Bicep |

---

## Official Microsoft Resources

| Resource | Link |
|----------|------|
| AZ-305 Exam Page | <https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/> |
| Official Practice Assessment | <https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15> |
| MS Learn: Identity, Governance & Monitoring | <https://learn.microsoft.com/en-us/training/paths/design-identity-governance-monitor-solutions/> |
| MS Learn: Data Storage Solutions | <https://learn.microsoft.com/en-us/training/paths/design-data-storage-solutions/> |
| MS Learn: Business Continuity Solutions | <https://learn.microsoft.com/en-us/training/paths/design-business-continuity-solutions/> |
| MS Learn: Infrastructure Solutions | <https://learn.microsoft.com/en-us/training/paths/design-infra-solutions/> |
| MS Learn: Network Solutions | <https://learn.microsoft.com/en-us/training/paths/design-network-solutions/> |
| Official Case Studies & Labs | <https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/> |
| Azure Architecture Center | <https://learn.microsoft.com/en-us/azure/architecture/> |
| AZ-305 Study Guide | <https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-305> |

---

## Official Case Studies (from Microsoft Learning)

| # | Case Study | Relevant Module |
|---|-----------|-----------------|
| 1 | Design a governance solution | Module 1 |
| 2 | Design a compute solution | Module 4 |
| 3 | Design a non-relational storage solution | Module 2 |
| 4 | Design a relational storage solution | Module 2 |
| 5 | Design a network infrastructure solution | Module 5 |
| 6 | Design a business continuity solution | Module 3 |
| 7 | Design an authentication and authorization solution | Module 1 |
| 8 | Design a logging and monitoring solution | Module 1 |

Access all at: <https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/>

---

## Quick Tips for Exam Day

- **Read every word** — AZ-305 questions hinge on subtle requirements (e.g., "minimize cost" vs. "minimize latency").
- **Know the decision trees** — When to pick App Service vs. Container Apps vs. AKS vs. Functions.
- **Composite SLA math** — Multiply individual SLAs; know how to improve with availability zones and multi-region.
- **Private Link vs. Service Endpoint** — Private Link = private IP in your VNet; Service Endpoint = optimized route over Microsoft backbone.
- **Managed Identity always** — Default answer for any "how should the app authenticate" question.
- **Zero Trust** — Verify explicitly, least privilege, assume breach.
- **Cost keywords** — Reserved instances, spot VMs, consumption tier, serverless, lifecycle policies.

---

*Last updated: February 2026*
