# Hands-On Labs Index

This index maps all Bicep templates, scripts, KQL queries, and official Microsoft case studies to their corresponding course modules.

---

## Official Microsoft Case Studies

Complete these scenario-based exercises from the [AZ-305 Microsoft Learning labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):

| # | Case Study | Module | Topic |
|---|-----------|--------|-------|
| 1 | [Design a governance solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/01-Governance.html) | M1 | Governance |
| 2 | [Design authentication and authorization solutions](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/06-Authentication.html) | M1 | Identity |
| 3 | [Fabrikam Residences — Logging and monitoring](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/07-Access.html) | M1 | Monitoring |
| 4 | [Design a relational storage solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/03-Relationalstorage.html) | M2 | SQL |
| 5 | [Design a non-relational storage solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/04-Nonrelationalstorage.html) | M2 | Cosmos DB / Storage |
| 6 | [Design a compute solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/02-Compute.html) | M4 | Compute |
| 7 | [Design an app architecture solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/05-Apparchitecture.html) | M4 | App patterns |
| 8 | [Design a network solution — BI enterprise application](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/08-Logging.html) | M5 | Networking |

> **Note:** Modules 3 (Business Continuity) and Migration topics do not have formal case studies. Use the Bicep labs and [practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) for those areas.

---

## Prerequisites

1. **Azure subscription** — [Free account](https://azure.microsoft.com/free/) or Visual Studio Enterprise benefit
2. **Azure CLI** — `az login` authenticated
3. **Bicep CLI** — bundled with Azure CLI (`az bicep install`)
4. **PowerShell 7** — for PowerShell scripts
5. **VS Code** with Bicep extension

### Deploying Bicep Templates

```bash
# Standard deployment pattern
az deployment group create \
  --resource-group <rg-name> \
  --template-file <file.bicep> \
  --parameters <file.parameters.json>
```

> **Cost Warning:** Some labs deploy resources that incur charges. Always delete resource groups after practicing.

---

## Module 1: Identity, Governance & Monitoring

### Bicep Templates

| Lab | Template | What You'll Deploy |
|-----|----------|--------------------|
| Log Analytics Workspace | [log-analytics-workspace.bicep](../infra/log-analytics-workspace.bicep) | Workspace with retention and solutions |
| Managed Identity | [managed-identity.bicep](../infra/managed-identity.bicep) | User-assigned managed identity with role assignments |
| Custom RBAC Role | [custom-rbac-role.bicep](../infra/custom-rbac-role.bicep) | Custom role definition with specific permissions |
| Key Vault with Private Link | [keyvault-with-private-link.bicep](../infra/keyvault-with-private-link.bicep) | Key Vault secured with Private Endpoint |
| Key Vault Assets | [keyvault-assets.bicep](../infra/keyvault-assets.bicep) | Secrets, certificates, and keys in Key Vault |
| Azure Policy Initiative | [azure-policy-initiative.bicep](../infra/azure-policy-initiative.bicep) | Custom policy initiative with definitions |

### Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| RBAC Assignments | [create-rbac-assignments.sh](../scripts/az-cli/create-rbac-assignments.sh) | Assign built-in roles to identities |
| Diagnostic Settings | [configure-diagnostic-settings.sh](../scripts/az-cli/configure-diagnostic-settings.sh) | Send logs to Log Analytics |
| Conditional Access | [Configure-ConditionalAccess.ps1](../scripts/powershell/Configure-ConditionalAccess.ps1) | Create Conditional Access policies |
| Policy Initiative | [Configure-PolicyInitiative.ps1](../scripts/powershell/Configure-PolicyInitiative.ps1) | Deploy and manage policy initiatives |
| Entra PIM | [Enable-EntraPIM.ps1](../scripts/powershell/Enable-EntraPIM.ps1) | Configure Privileged Identity Management |
| Managed Identity | [New-ManagedIdentity.ps1](../scripts/powershell/New-ManagedIdentity.ps1) | Create and assign managed identities |
| Defender for Cloud | [Enable-DefenderForCloud.ps1](../scripts/powershell/Enable-DefenderForCloud.ps1) | Enable and configure security features |

### KQL Queries

| Lab | Query File | What You'll Analyze |
|-----|------------|--------------------|
| Application Insights | [application-insights.kql](../scripts/kql/application-insights.kql) | App performance and dependency analysis |
| Security Audit | [security-audit.kql](../scripts/kql/security-audit.kql) | Sign-in anomalies and audit trail |
| Resource Changes | [resource-changes.kql](../scripts/kql/resource-changes.kql) | Track Azure resource modifications |

### Example Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Identity & Governance | [01-identity-governance.ps1](../scripts/examples/01-identity-governance.ps1) | End-to-end identity scenarios |
| Monitoring & Logging | [02-monitoring-logging.sh](../scripts/examples/02-monitoring-logging.sh) | Complete monitoring setup |
| KQL Monitoring | [07-kql-monitoring-queries.kql](../scripts/examples/07-kql-monitoring-queries.kql) | Advanced KQL queries |

---

## Module 2: Data Storage Solutions

### Bicep Templates

| Lab | Template | What You'll Deploy |
|-----|----------|--------------------|
| Cosmos DB Multi-Region | [cosmosdb-multi-region.bicep](../infra/cosmosdb-multi-region.bicep) | Globally distributed Cosmos DB with failover |
| SQL Elastic Pool | [sql-database-elastic-pool.bicep](../infra/sql-database-elastic-pool.bicep) | SQL Database with elastic pool |
| SQL Failover Group | [sql-failover-group.bicep](../infra/sql-failover-group.bicep) | SQL auto-failover across regions |
| Storage Account Tiered | [storage-account-tiered.bicep](../infra/storage-account-tiered.bicep) | Storage with access tiers and lifecycle |

### Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Cosmos DB Account | [New-CosmosDBAccount.ps1](../scripts/powershell/New-CosmosDBAccount.ps1) | Create and configure Cosmos DB |
| Storage Lifecycle | [Set-StorageLifecycle.ps1](../scripts/powershell/Set-StorageLifecycle.ps1) | Configure tier management policies |
| SQL Failover Group | [setup-sql-failover-group.sh](../scripts/az-cli/setup-sql-failover-group.sh) | Deploy SQL failover groups |

### Example Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Data Storage | [03-data-storage.ps1](../scripts/examples/03-data-storage.ps1) | End-to-end data scenarios |

---

## Module 3: Business Continuity & DR

### Bicep Templates

| Lab | Template | What You'll Deploy |
|-----|----------|--------------------|
| Recovery Services Vault | [recovery-services-vault.bicep](../infra/recovery-services-vault.bicep) | Backup vault with policies |
| Site Recovery Config | [site-recovery-config.bicep](../infra/site-recovery-config.bicep) | ASR replication configuration |

### Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Backup Policy | [configure-backup-policy.sh](../scripts/az-cli/configure-backup-policy.sh) | Set up Azure Backup policies |

### KQL Queries

| Lab | Query File | What You'll Analyze |
|-----|------------|--------------------|
| Cost Analysis | [cost-analysis.kql](../scripts/kql/cost-analysis.kql) | DR and backup cost monitoring |

### Example Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Business Continuity | [04-business-continuity.sh](../scripts/examples/04-business-continuity.sh) | DR and backup scenarios |

---

## Module 4: Compute & App Architecture

### Bicep Templates

| Lab | Template | What You'll Deploy |
|-----|----------|--------------------|
| AKS Cluster | [aks-cluster.bicep](../infra/aks-cluster.bicep) | Kubernetes cluster with node pools |
| Container Apps Environment | [container-apps-environment.bicep](../infra/container-apps-environment.bicep) | Container Apps with Dapr and scaling |
| APIM with Backends | [apim-with-backends.bicep](../infra/apim-with-backends.bicep) | API Management with backend services |

### Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Container Apps | [deploy-container-apps.sh](../scripts/az-cli/deploy-container-apps.sh) | Deploy containerized applications |
| APIM | [deploy-apim.sh](../scripts/az-cli/deploy-apim.sh) | Deploy and configure API Management |
| Resource Inventory | [Export-ResourceInventory.ps1](../scripts/powershell/Export-ResourceInventory.ps1) | Audit deployed resources |
| Landing Zone | [Deploy-LandingZone.ps1](../scripts/powershell/Deploy-LandingZone.ps1) | Deploy Azure landing zone components |

### Example Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Compute Solutions | [05-compute-solutions.ps1](../scripts/examples/05-compute-solutions.ps1) | End-to-end compute scenarios |
| Bicep Patterns | [09-bicep-patterns.bicep](../scripts/examples/09-bicep-patterns.bicep) | Advanced Bicep authoring techniques |
| Python Azure SDK | [08-python-azure-sdk.py](../scripts/examples/08-python-azure-sdk.py) | Azure SDK for Python examples |

---

## Module 5: Network Solutions

### Bicep Templates

| Lab | Template | What You'll Deploy |
|-----|----------|--------------------|
| Hub-Spoke Network | [hub-spoke-network.bicep](../infra/hub-spoke-network.bicep) | Full hub-spoke topology with peering |
| Application Gateway WAF | [application-gateway-waf.bicep](../infra/application-gateway-waf.bicep) | App Gateway with WAF v2 policies |
| Front Door Global | [front-door-global.bicep](../infra/front-door-global.bicep) | Global load balancing with CDN |
| Private Endpoint Services | [private-endpoint-services.bicep](../infra/private-endpoint-services.bicep) | Private Endpoints for PaaS services |

### Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Hub-Spoke Deploy | [deploy-hub-spoke.sh](../scripts/az-cli/deploy-hub-spoke.sh) | Deploy hub-spoke network |
| Private Endpoints | [create-private-endpoints.sh](../scripts/az-cli/create-private-endpoints.sh) | Create and test Private Endpoints |
| Test Private Endpoint | [Test-PrivateEndpoint.ps1](../scripts/powershell/Test-PrivateEndpoint.ps1) | Validate private endpoint connectivity |

### KQL Queries

| Lab | Query File | What You'll Analyze |
|-----|------------|--------------------|
| Network Diagnostics | [network-diagnostics.kql](../scripts/kql/network-diagnostics.kql) | NSG flows, connectivity issues |
| Performance Analysis | [performance-analysis.kql](../scripts/kql/performance-analysis.kql) | Network latency and throughput |

### Example Scripts

| Lab | Script | What You'll Practice |
|-----|--------|--------------------|
| Networking | [06-networking.sh](../scripts/examples/06-networking.sh) | End-to-end network scenarios |

---

## Lab Completion Checklist

Use this tracker to mark off completed labs:

| # | Lab | Module | Status |
|---|-----|--------|--------|
| 1 | Log Analytics Workspace | M1 | ⬜ |
| 2 | Managed Identity + RBAC | M1 | ⬜ |
| 3 | Key Vault with Private Link | M1 | ⬜ |
| 4 | Azure Policy Initiative | M1 | ⬜ |
| 5 | Conditional Access + PIM | M1 | ⬜ |
| 6 | Cosmos DB Multi-Region | M2 | ⬜ |
| 7 | SQL Elastic Pool + Failover | M2 | ⬜ |
| 8 | Storage Lifecycle + Tiers | M2 | ⬜ |
| 9 | Recovery Services Vault | M3 | ⬜ |
| 10 | Site Recovery Config | M3 | ⬜ |
| 11 | AKS Cluster | M4 | ⬜ |
| 12 | Container Apps Environment | M4 | ⬜ |
| 13 | APIM with Backends | M4 | ⬜ |
| 14 | Hub-Spoke Network | M5 | ⬜ |
| 15 | Application Gateway WAF | M5 | ⬜ |
| 16 | Front Door Global | M5 | ⬜ |
| 17 | Private Endpoints | M5 | ⬜ |

---

## Cleanup

After completing labs, delete resource groups to avoid charges:

```bash
# List resource groups
az group list --output table

# Delete a specific resource group
az group delete --name <rg-name> --yes --no-wait
```

---

## Exam Preparation Links

| Resource | Link |
|----------|------|
| Official Exam Page | [AZ-305 Exam](https://learn.microsoft.com/credentials/certifications/exams/az-305/) |
| Free Practice Assessment | [Practice Assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) |
| Exam Prep Videos | [Exam Readiness Zone](https://learn.microsoft.com/shows/exam-readiness-zone/preparing-for-az-305-design-identity-governance-and-monitoring-solutions-1-of-4) |
| Exam Sandbox | [Try the format](https://go.microsoft.com/fwlink/?linkid=2226877) |
| Study Guide | [AZ-305 Study Guide](https://aka.ms/AZ305-StudyGuide) |
| MS Learning Labs | [Case Studies](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/) |
