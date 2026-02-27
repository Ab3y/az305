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

| # | Lesson | Duration | Focus |
|---|--------|----------|-------|
| 1 | [Relational Data](lesson-1-relational-data.md) | 60 min | SQL Database, SQL MI, tiers, scalability, protection |
| 2 | [Non-Relational Data](lesson-2-non-relational-data.md) | 60 min | Cosmos DB, Blob Storage, Data Lake, Files |
| 3 | [Data Integration](lesson-3-data-integration.md) | 45 min | Data Factory, Synapse Analytics, data pipelines |

---

## Hands-On Labs

| # | Lab | Bicep Template | Estimated Time |
|---|-----|---------------|----------------|
| 1 | Deploy SQL elastic pool with vCore model | [sql-database-elastic-pool.bicep](../../infra/sql-database-elastic-pool.bicep) | 20 min |
| 2 | Deploy Cosmos DB with multi-region writes | [cosmosdb-multi-region.bicep](../../infra/cosmosdb-multi-region.bicep) | 25 min |
| 3 | Deploy storage account with lifecycle policies | [storage-account-tiered.bicep](../../infra/storage-account-tiered.bicep) | 15 min |
| 4 | Deploy SQL failover group across regions | [sql-failover-group.bicep](../../infra/sql-failover-group.bicep) | 20 min |

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
```
Need full SQL Server compatibility (CLR, Agent, SSIS)?
  ├── YES ──> SQL Managed Instance (or SQL Server on VM)
  └── NO
        Need elastic pool for multi-tenant?
          ├── YES ──> Azure SQL Database (Elastic Pool)
          └── NO ──> Azure SQL Database (Single)
                       ├── Predictable workload ──> Provisioned (vCore)
                       └── Variable workload ──> Serverless
```

### Cosmos DB Global Distribution
```
East US (Write) <──sync──> West Europe (Write) <──sync──> SE Asia (Write)
       │
Partition Strategy: /tenantId (high cardinality, even distribution)
Consistency: Session (default sweet spot)
```

### Storage Tiers Lifecycle
```
Hot (active data) ──30 days──> Cool ──90 days──> Cold ──180 days──> Archive
                                                                      │
                                              Rehydrate to Hot/Cool <─┘
```

---

## Exam Tips

| Keyword in Question | Answer Points To |
|---------------------|-----------------|
| "Full SQL Server compatibility" | SQL Managed Instance |
| "Multi-tenant, shared resources" | Elastic pools |
| "Variable workload, cost sensitive" | Serverless compute tier |
| "Global distribution, <10ms writes" | Cosmos DB multi-region writes |
| "Partition key" | High cardinality, included in most queries |
| "7-year archive" | Storage Account (Archive tier or cool) |
| "Immutable storage" | Legal hold or time-based retention |
| "Regional outage protection" | GRS / GZRS redundancy |
| "ETL / data orchestration" | Azure Data Factory |
| "Unified analytics" | Azure Synapse Analytics |

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
