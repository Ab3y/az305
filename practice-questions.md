# AZ-305 Comprehensive Practice Questions

**Exam:** Microsoft Certified: Azure Solutions Architect Expert (AZ-305)

This comprehensive practice question set covers all five course modules aligned with the AZ-305 exam domains. Each question includes detailed explanations and direct references to Microsoft Learn documentation.

**Total Questions:** 50 (10 per module)
**Target Score:** 80%+ to demonstrate exam readiness

---

## How to Use This Resource

1. **Take the full assessment** — complete all 50 questions in one sitting (aim for 90 minutes)
2. **Review explanations** — understand WHY each answer is correct, not just which option
3. **Follow reference links** — dive deeper into Microsoft Learn for topics you missed
4. **Identify gaps** — if you score below 80% in any module, review that module's lessons
5. **Retake** — aim for 90%+ on your second attempt before scheduling the exam

---

## Table of Contents

- [Module 1: Identity, Governance & Monitoring (10 Questions)](#module-1-identity-governance--monitoring)
- [Module 2: Data Storage Solutions (10 Questions)](#module-2-data-storage-solutions)
- [Module 3: Business Continuity & Disaster Recovery (10 Questions)](#module-3-business-continuity--disaster-recovery)
- [Module 4: Infrastructure & Compute Solutions (10 Questions)](#module-4-infrastructure--compute-solutions)
- [Module 5: Network Solutions (10 Questions)](#module-5-network-solutions)
- [Scoring Guide](#scoring-guide)

---

## Module 1: Identity, Governance & Monitoring

*Exam Weight: 25-30% | Questions 1-10*

---

### Question 1: Log Analytics Workspace Architecture

Contoso Ltd. operates 50+ Azure subscriptions across multiple business units. They need centralized log collection with 90-day retention for compliance, cost-efficient storage for older logs, and the ability to query across all subscriptions. What should you recommend?

- A. One Log Analytics workspace per subscription with cross-workspace queries
- B. A single centralized Log Analytics workspace with resource-context RBAC
- C. Azure Monitor Logs with dedicated cluster and customer-managed keys
- D. Multiple Log Analytics workspaces federated with Azure Data Explorer

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

A single centralized workspace with resource-context RBAC provides unified querying, cost efficiency (bulk ingestion pricing via commitment tiers), and granular access control based on Azure resource permissions. This is the recommended pattern for multi-subscription enterprises.

**Why other answers are incorrect:**
- **A is wrong:** Multiple workspaces increase cost and complexity. Cross-workspace queries have limits and are slower.
- **C is wrong:** Dedicated clusters require 500GB+/day commitment — overkill unless you need CMK or higher performance.
- **D is wrong:** ADX federation adds complexity; only justified for petabyte-scale analytics.

**Reference:**
- [Design a Log Analytics workspace architecture](https://learn.microsoft.com/azure/azure-monitor/logs/workspace-design)
- [Azure Monitor Logs overview](https://learn.microsoft.com/azure/azure-monitor/logs/data-platform-logs)

</details>

---

### Question 2: Diagnostic Settings for Multi-Destination Routing

Wingtip Toys needs to route Azure Activity Logs to their SIEM system (Splunk), retain logs in Azure for 7 years for compliance, and enable near-real-time alerting. Which architecture should you recommend?

- A. Diagnostic settings to Event Hub (SIEM) + Storage Account (archive) + Log Analytics (alerting)
- B. Diagnostic settings to Log Analytics only with 7-year retention
- C. Azure Monitor Agent to Log Analytics with export rules to Storage
- D. Direct API integration from SIEM to Azure Activity Log

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

The fan-out pattern using diagnostic settings to multiple destinations: Event Hub for real-time SIEM streaming, Storage Account for cost-effective 7-year archive, Log Analytics for alerting and investigation.

**Why other answers are incorrect:**
- **B is wrong:** Log Analytics interactive retention max is 730 days (2 years). Archive tier extends to 12 years, but Storage Account is more cost-effective for 7-year retention.
- **C is wrong:** Azure Monitor Agent is for VMs, not Activity Logs. Export rules go to Storage, not Log Analytics.
- **D is wrong:** Polling APIs is inefficient and doesn't meet real-time requirements.

**Reference:**
- [Diagnostic settings in Azure Monitor](https://learn.microsoft.com/azure/azure-monitor/essentials/diagnostic-settings)
- [Azure Activity Log](https://learn.microsoft.com/azure/azure-monitor/essentials/activity-log)

</details>

---

### Question 3: Application Performance Monitoring

Fabrikam runs microservices on AKS. They require distributed tracing, auto-scaling based on custom metrics, and cost control. What should you recommend?

- A. Application Insights with workspace-based mode, sampling enabled, and custom metrics for KEDA
- B. Application Insights with classic mode and Prometheus integration
- C. Azure Monitor for Containers with built-in Application Insights
- D. Third-party APM tool with OpenTelemetry export

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Workspace-based Application Insights is the modern standard — unified querying, sampling reduces costs, and custom metrics can drive KEDA autoscaling.

**Why other answers are incorrect:**
- **B is wrong:** Classic mode is deprecated. Prometheus doesn't provide distributed tracing.
- **C is wrong:** Azure Monitor for Containers provides infrastructure metrics, not application-level traces.
- **D is wrong:** Third-party tools add cost and complexity when native options meet requirements.

**Reference:**
- [Application Insights overview](https://learn.microsoft.com/azure/azure-monitor/app/app-insights-overview)
- [Workspace-based Application Insights](https://learn.microsoft.com/azure/azure-monitor/app/create-workspace-resource)

</details>

---

### Question 4: External Partner Access with B2B

Contoso needs to give 500 consultants (external users) access to specific Azure resources. Consultants should use their own corporate credentials, access must be reviewable quarterly, and least privilege is mandatory. What should you recommend?

- A. Microsoft Entra B2B with access packages and access reviews
- B. Microsoft Entra B2C with custom policies
- C. Sync external users to Microsoft Entra ID with Entra Connect
- D. Create cloud-only accounts for each consultant

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

B2B collaboration with Entitlement Management (access packages) and access reviews is the enterprise pattern for external partner access. Users keep their own credentials, access is time-bound and reviewable.

**Why other answers are incorrect:**
- **B is wrong:** B2C / External ID is for consumer-facing apps, not business partner collaboration.
- **C is wrong:** Syncing external users violates identity sovereignty and complicates management.
- **D is wrong:** Cloud-only accounts create credential sprawl and don't support quarterly reviews natively.

**Reference:**
- [Microsoft Entra B2B collaboration](https://learn.microsoft.com/entra/external-id/what-is-b2b)
- [Entitlement management overview](https://learn.microsoft.com/entra/id-governance/entitlement-management-overview)
- [Access reviews overview](https://learn.microsoft.com/entra/id-governance/access-reviews-overview)

</details>

---

### Question 5: Managed Identity for Zero-Secret Authentication

Wingtip Toys runs an e-commerce app on Azure App Service that needs to access Azure SQL Database, Azure Storage, and Azure Key Vault. The solution must have zero secrets in application code and support automatic credential rotation. What should you recommend?

- A. User-assigned managed identity for all services
- B. System-assigned managed identity for each App Service instance
- C. Service principal with certificate authentication stored in Key Vault
- D. Microsoft Entra application with client secret rotated monthly

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

User-assigned managed identity provides zero-secret authentication, automatic credential management, and can be shared across deployment slots and resources.

**Why other answers are incorrect:**
- **B is wrong:** System-assigned identities work but create access management overhead with multiple instances (each gets a unique identity).
- **C is wrong:** Service principals with certificates still require certificate management — managed identity eliminates this.
- **D is wrong:** Client secrets require rotation management and risk exposure.

**Reference:**
- [Managed identities for Azure resources](https://learn.microsoft.com/entra/identity/managed-identities-azure-resources/overview)
- [User-assigned managed identities](https://learn.microsoft.com/entra/identity/managed-identities-azure-resources/how-manage-user-assigned-managed-identities)

</details>

---

### Question 6: Key Vault Design for Financial Compliance

Fabrikam's financial services application must store database connection strings, API keys, and SSL certificates. They require FIPS 140-2 Level 3 compliance, automatic secret rotation, and private network access only. What should you recommend?

- A. Key Vault Premium with Private Link, Event Grid for rotation, purge protection enabled
- B. Key Vault Standard with VNet service endpoints and manual rotation
- C. Azure App Configuration with Key Vault references
- D. Key Vault Premium with access policies and public endpoint

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Key Vault Premium provides HSM-backed keys (FIPS 140-2 Level 3). Private Link ensures private network access. Event Grid triggers automatic rotation. Purge protection is required for financial compliance.

**Why other answers are incorrect:**
- **B is wrong:** Standard tier doesn't provide FIPS 140-2 Level 3 (software-protected only). Service endpoints don't provide private IPs. Manual rotation doesn't meet requirements.
- **C is wrong:** App Configuration stores configuration, not secrets. Key Vault references are good practice but don't address the core requirements.
- **D is wrong:** Public endpoint violates "private network access only."

**Reference:**
- [Azure Key Vault security features](https://learn.microsoft.com/azure/key-vault/general/security-features)
- [Azure Key Vault private link](https://learn.microsoft.com/azure/key-vault/general/private-link-service)
- [Key rotation with Event Grid](https://learn.microsoft.com/azure/key-vault/secrets/tutorial-rotation)

</details>

---

### Question 7: RBAC Scope Design

A company has three Azure subscriptions: Dev, Test, and Prod. The security team must be able to manage role assignments across all subscriptions but should have no other permissions. What should you recommend?

- A. Assign User Access Administrator role at the management group scope containing all three subscriptions
- B. Assign Owner role at each subscription scope
- C. Assign Contributor role at the management group scope
- D. Create a custom role with all permissions at each subscription

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

User Access Administrator grants only the ability to manage role assignments. Assigning at management group scope covers all subscriptions with a single assignment. This follows least privilege.

**Why other answers are incorrect:**
- **B is wrong:** Owner has full permissions — violates least privilege.
- **C is wrong:** Contributor cannot manage role assignments.
- **D is wrong:** Unnecessary complexity; a built-in role meets the requirement.

**Reference:**
- [Azure built-in roles](https://learn.microsoft.com/azure/role-based-access-control/built-in-roles)
- [Azure management groups](https://learn.microsoft.com/azure/governance/management-groups/overview)

</details>

---

### Question 8: Azure Policy for Compliance Enforcement

An organization must ensure that all new Azure resources are created only in East US and West US regions, and all resources must have a `CostCenter` tag. Non-compliant existing resources should be flagged but not deleted. What should you recommend?

- A. Two Azure policies: `Deny` effect for allowed regions, `Audit` effect for the tag requirement on existing resources with `Deny` for new resources
- B. A single Azure Policy initiative with `Deny` effect for both policies
- C. Azure Blueprints with region and tag constraints
- D. Management group with subscription-level region restrictions

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Two separate policies address different requirements: Deny for regions (block new resources in wrong regions), and a combination approach for tags (Audit existing, Deny new). This enforces going forward while giving time to remediate existing resources.

**Why other answers are incorrect:**
- **B is wrong:** Deny on existing resources without tags would block updates to those resources.
- **C is wrong:** Blueprints are deprecated (July 2026).
- **D is wrong:** Management groups don't inherently restrict regions.

**Reference:**
- [Azure Policy overview](https://learn.microsoft.com/azure/governance/policy/overview)
- [Azure Policy effects](https://learn.microsoft.com/azure/governance/policy/concepts/effects)
- [Require tags with Azure Policy](https://learn.microsoft.com/azure/governance/policy/tutorials/govern-tags)

</details>

---

### Question 9: Privileged Identity Management Configuration

A company's database administrators need occasional Contributor access to the production subscription. Access should require approval, be time-limited, and create an audit trail. What should you recommend?

- A. PIM with eligible assignment, 4-hour maximum activation, approval required, justification required
- B. Permanent Contributor role with conditional access policy
- C. Just-in-time VM access through Defender for Cloud
- D. Custom RBAC role with time-based conditions

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

PIM with eligible assignments provides just-in-time access with all required controls: approval workflow, time-bound activation, justification, and full audit trail.

**Why other answers are incorrect:**
- **B is wrong:** Permanent role doesn't meet "occasional" or "time-limited" requirements. Conditional access controls authentication, not role activation.
- **C is wrong:** JIT VM access is for network ports (NSG), not RBAC.
- **D is wrong:** Custom RBAC roles don't support time-based activation natively.

**Reference:**
- [What is Privileged Identity Management?](https://learn.microsoft.com/entra/id-governance/privileged-identity-management/pim-configure)
- [Configure PIM for Azure resources](https://learn.microsoft.com/entra/id-governance/privileged-identity-management/pim-resource-roles-configure-role-settings)

</details>

---

### Question 10: Hybrid Identity with Pass-Through Authentication

A company is migrating to Azure. They have three disconnected AD forests, cannot allow password hashes in the cloud, and need seamless SSO. What should you recommend?

- A. Entra Connect Sync v2 with pass-through authentication and seamless SSO
- B. Entra Cloud Sync with password hash sync
- C. AD FS federation with each forest
- D. Entra Cloud Sync with pass-through authentication

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Entra Connect Sync v2 supports pass-through authentication (passwords never leave on-premises) and seamless SSO. It can be configured for multiple forests.

**Why other answers are incorrect:**
- **B is wrong:** Cloud Sync doesn't support pass-through authentication. PHS puts password hashes in the cloud.
- **C is wrong:** AD FS adds significant infrastructure complexity. Only use for legacy requirements.
- **D is wrong:** Cloud Sync does not support pass-through authentication.

**Reference:**
- [Microsoft Entra Connect Sync](https://learn.microsoft.com/entra/identity/hybrid/connect/whatis-azure-ad-connect-v2)
- [Pass-through authentication](https://learn.microsoft.com/entra/identity/hybrid/connect/how-to-connect-pta)
- [Seamless single sign-on](https://learn.microsoft.com/entra/identity/hybrid/connect/how-to-connect-sso)

</details>

---

## Module 2: Data Storage Solutions

*Exam Weight: 20-25% | Questions 11-20*

---

### Question 11: SQL Database Migration Strategy

A company is migrating a SQL Server database to Azure. The application uses SQL Agent jobs, CLR assemblies, and cross-database queries. They want a fully managed solution with minimal code changes. What should you recommend?

- A. Azure SQL Database with elastic jobs
- B. Azure SQL Managed Instance
- C. SQL Server on Azure VM
- D. Azure Database for PostgreSQL

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

SQL Managed Instance provides ~100% SQL Server compatibility including SQL Agent, CLR, and cross-database queries in a fully managed PaaS service — minimal code changes needed.

**Why other answers are incorrect:**
- **A is wrong:** SQL Database doesn't support SQL Agent jobs natively, CLR, or cross-database queries.
- **C is wrong:** SQL on VM works but isn't "fully managed" — you manage patching, HA, backups.
- **D is wrong:** PostgreSQL is a different database engine entirely.

**Reference:**
- [Azure SQL Managed Instance](https://learn.microsoft.com/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview)
- [Features comparison: Azure SQL Database vs SQL Managed Instance](https://learn.microsoft.com/azure/azure-sql/database/features-comparison)

</details>

---

### Question 12: Serverless Compute Tier

A startup has a database that is heavily used during business hours (8 AM - 6 PM) but nearly idle at night and on weekends. They want to minimize costs. What should you recommend?

- A. Azure SQL Database — Serverless compute tier
- B. Azure SQL Database — General Purpose provisioned
- C. Azure SQL Database — Hyperscale tier
- D. Azure SQL Managed Instance

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Serverless auto-pauses when idle (no compute charges) and auto-scales during active periods. Ideal for intermittent workloads with significant idle time.

**Why other answers are incorrect:**
- **B is wrong:** Provisioned compute charges continuously, even during idle hours.
- **C is wrong:** Hyperscale is for very large databases, not cost optimization for variable workloads.
- **D is wrong:** SQL MI is always running — no auto-pause capability.

**Reference:**
- [Azure SQL Database serverless](https://learn.microsoft.com/azure/azure-sql/database/serverless-tier-overview)
- [SQL Database service tiers](https://learn.microsoft.com/azure/azure-sql/database/service-tiers-general-purpose-business-critical)

</details>

---

### Question 13: Elastic Pools for Multi-Tenant SaaS

A SaaS company has 50 tenant databases. Each averages 5 DTUs but can spike to 50 DTUs. Spikes don't happen simultaneously. What should you recommend?

- A. 50 individual S3 databases (100 DTUs each)
- B. An elastic pool with 500 eDTUs shared across all databases
- C. 50 individual serverless databases
- D. A single database with row-level security for multi-tenancy

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Elastic pools are designed for this exact scenario — multiple databases with variable, non-overlapping peak usage sharing a common resource pool. 500 eDTUs handles peaks while averaging much lower usage.

**Why other answers are incorrect:**
- **A is wrong:** Over-provisioning each database at peak capacity wastes resources and budget.
- **C is wrong:** 50 individual serverless databases don't share resources and each has minimum billing.
- **D is wrong:** Single database with RLS is a different architecture — operational complexity and doesn't scale the same way.

**Reference:**
- [SQL Database elastic pools](https://learn.microsoft.com/azure/azure-sql/database/elastic-pool-overview)
- [Manage multiple databases with elastic pools](https://learn.microsoft.com/azure/azure-sql/database/elastic-pool-manage)

</details>

---

### Question 14: Cosmos DB Partition Key Selection

An e-commerce application stores orders in Cosmos DB. Queries are typically by customer (get all orders for a customer) and by order ID. The company has millions of customers worldwide. What partition key should you recommend?

- A. `/customerId`
- B. `/orderDate`
- C. `/status`
- D. `/region`

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

`/customerId` has high cardinality (millions of unique values), enables even distribution, and aligns with the most common query pattern (get orders by customer). Point reads by orderId within a customer partition are efficient.

**Why other answers are incorrect:**
- **B is wrong:** Date-based keys create hot partitions (all writes go to "today's" partition).
- **C is wrong:** Status has low cardinality (e.g., "pending," "shipped," "delivered") — creates very uneven distribution.
- **D is wrong:** Region has low cardinality and doesn't align with the primary query pattern.

**Reference:**
- [Partitioning in Azure Cosmos DB](https://learn.microsoft.com/azure/cosmos-db/partitioning-overview)
- [Choose a partition key](https://learn.microsoft.com/azure/cosmos-db/nosql/how-to-model-partition-example)

</details>

---

### Question 15: Cosmos DB Consistency Levels

A financial application processes bank transfers between accounts. The application must guarantee that after a transfer, both the debit and credit are immediately visible to all readers. What Cosmos DB consistency level should you recommend?

- A. Strong
- B. Session
- C. Bounded Staleness
- D. Eventual

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Strong consistency guarantees linearizable reads — after a write completes, all subsequent reads return the updated value. Required for financial transactions where read-after-write consistency across all clients is mandatory.

**Why other answers are incorrect:**
- **B is wrong:** Session consistency only guarantees read-your-writes within a single session, not across all readers.
- **C is wrong:** Bounded Staleness allows a configurable lag — not appropriate for immediate financial visibility.
- **D is wrong:** Eventual consistency offers no ordering guarantees — unacceptable for financial data.

**Reference:**
- [Consistency levels in Azure Cosmos DB](https://learn.microsoft.com/azure/cosmos-db/consistency-levels)
- [Choose the right consistency level](https://learn.microsoft.com/azure/cosmos-db/nosql/consistency-levels)

</details>

---

### Question 16: Storage Redundancy with Read Access

A healthcare company stores medical images in Azure Blob Storage. Regulatory requirements mandate that data must survive a regional outage, and the application must be able to read data even during a regional failover. What redundancy option should you recommend?

- A. RA-GRS (Read-Access Geo-Redundant Storage)
- B. GRS (Geo-Redundant Storage)
- C. ZRS (Zone-Redundant Storage)
- D. LRS (Locally Redundant Storage)

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

RA-GRS provides 6 copies across two regions (like GRS) PLUS read access to the secondary region during normal operations. The application can read from the secondary if the primary region fails.

**Why other answers are incorrect:**
- **B is wrong:** GRS replicates to a secondary region but data is NOT readable until Microsoft initiates a failover.
- **C is wrong:** ZRS protects against zone failures within a single region, not regional outages.
- **D is wrong:** LRS has 3 copies in a single datacenter — no protection against zone or regional failure.

**Reference:**
- [Azure Storage redundancy](https://learn.microsoft.com/azure/storage/common/storage-redundancy)
- [Geo-redundant storage](https://learn.microsoft.com/azure/storage/common/storage-redundancy#geo-redundant-storage)

</details>

---

### Question 17: Immutable Blob Storage for Compliance

A law firm must store legal documents that cannot be modified or deleted for 7 years to comply with SEC Rule 17a-4. What should you recommend?

- A. Blob Storage with time-based immutable retention policy (7 years)
- B. Blob Storage with soft delete enabled (7-year retention)
- C. Blob Storage with versioning enabled
- D. Data Lake Storage Gen2 with ACLs

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Time-based immutable retention policy implements true WORM (Write Once, Read Many) storage. Blobs cannot be modified or deleted until the retention period expires. This meets SEC 17a-4 compliance.

**Why other answers are incorrect:**
- **B is wrong:** Soft delete allows recovery of deleted data but doesn't prevent deletion in the first place.
- **C is wrong:** Versioning keeps copies but doesn't prevent deletion of all versions.
- **D is wrong:** ACLs control access permissions but don't enforce immutability.

**Reference:**
- [Immutable storage for Azure Blob Storage](https://learn.microsoft.com/azure/storage/blobs/immutable-storage-overview)
- [Store business-critical data with immutable storage](https://learn.microsoft.com/azure/storage/blobs/immutable-policy-configure-version-scope)

</details>

---

### Question 18: Data Lake Storage Gen2 Features

A retail company needs a data lake for analytics. They ingest data from 20 sources, need to perform transformations, and serve curated data to Power BI. They need file-level access control and atomic directory operations. What should you recommend?

- A. Azure Data Lake Storage Gen2 (Blob Storage with hierarchical namespace)
- B. Standard Azure Blob Storage
- C. Azure Files Premium
- D. Azure Cosmos DB with analytical store

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

ADLS Gen2 provides hierarchical namespace (true directories with atomic rename/move), file-level POSIX ACLs, and is optimized for analytics workloads (Synapse, Spark, Data Factory integration). Same cost as standard Blob Storage.

**Why other answers are incorrect:**
- **B is wrong:** Standard Blob Storage has a flat namespace — no atomic directory operations, no file-level ACLs.
- **C is wrong:** Azure Files is for file shares (SMB/NFS), not analytics data lakes.
- **D is wrong:** Cosmos DB analytical store is for operational analytics on Cosmos data, not a general-purpose data lake.

**Reference:**
- [Introduction to Azure Data Lake Storage Gen2](https://learn.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)
- [Access control model in Azure Data Lake Storage Gen2](https://learn.microsoft.com/azure/storage/blobs/data-lake-storage-access-control-model)

</details>

---

### Question 19: Data Integration with Azure Data Factory

A company needs to ingest data from on-premises SQL Server and Salesforce into Azure Data Lake Gen2, transform it, load it into a Synapse dedicated pool, and visualize in Power BI. Which service should orchestrate this pipeline?

- A. Azure Data Factory with self-hosted integration runtime
- B. Azure Stream Analytics
- C. Azure Logic Apps
- D. Azure Functions with timer trigger

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Data Factory is the purpose-built ETL/ELT orchestration service. Self-hosted integration runtime enables secure access to on-premises SQL Server. Built-in connectors for Salesforce, ADLS Gen2, and Synapse.

**Why other answers are incorrect:**
- **B is wrong:** Stream Analytics is for real-time streaming, not batch ETL orchestration.
- **C is wrong:** Logic Apps is for workflow automation, not data integration pipelines.
- **D is wrong:** Azure Functions can process data but lacks built-in connectors, monitoring, and pipeline orchestration features.

**Reference:**
- [What is Azure Data Factory?](https://learn.microsoft.com/azure/data-factory/introduction)
- [Integration runtime in Azure Data Factory](https://learn.microsoft.com/azure/data-factory/concepts-integration-runtime)

</details>

---

### Question 20: Analytics Platform for Machine Learning

A data science team needs to run Apache Spark notebooks for machine learning model training. They require collaborative notebooks, Delta Lake for reliable data processing, and MLflow for experiment tracking. What should you recommend?

- A. Azure Databricks
- B. Azure Synapse Spark pool
- C. Azure HDInsight
- D. Azure Machine Learning compute

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Databricks provides the richest Spark experience with collaborative notebooks, native Delta Lake support, and integrated MLflow for experiment tracking — exactly matching the requirements.

**Why other answers are incorrect:**
- **B is wrong:** Synapse Spark is good for unified analytics but has more limited notebook collaboration and no native MLflow.
- **C is wrong:** HDInsight is open-source Hadoop/Spark but requires more management and lacks Delta Lake integration.
- **D is wrong:** Azure ML compute is for ML training/inference, not general Spark data engineering with Delta Lake.

**Reference:**
- [What is Azure Databricks?](https://learn.microsoft.com/azure/databricks/introduction/)
- [Delta Lake on Azure Databricks](https://learn.microsoft.com/azure/databricks/delta/)
- [MLflow on Azure Databricks](https://learn.microsoft.com/azure/databricks/mlflow/)

</details>

---

## Module 3: Business Continuity & Disaster Recovery

*Exam Weight: 15-20% | Questions 21-30*

---

### Question 21: RTO and RPO Requirements

A financial services company requires an RTO of 30 seconds and RPO of near zero for their web application and database. What architecture should you recommend?

- A. Azure Backup with geo-restore
- B. Azure Site Recovery with 5-minute RPO
- C. Active-active deployment across two regions with Cosmos DB multi-region writes
- D. Active-passive with SQL auto-failover groups

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

Active-active deployment with Cosmos DB multi-region writes provides near-zero RPO (synchronous within region) and near-instant failover (RTO ~seconds). Both regions serve traffic simultaneously.

**Why other answers are incorrect:**
- **A is wrong:** Backup + geo-restore has RTO of hours and RPO of up to 24 hours.
- **B is wrong:** ASR provides 5-minute RPO and RTO of minutes — doesn't meet 30-second RTO.
- **D is wrong:** Auto-failover groups have ~30-second RTO but this is active-passive, not the lowest RTO option. However, the 30-second RTO requirement combined with near-zero RPO points to active-active as the best solution.

**Reference:**
- [Design for disaster recovery](https://learn.microsoft.com/azure/architecture/framework/resiliency/backup-and-recovery)
- [Cosmos DB high availability](https://learn.microsoft.com/azure/cosmos-db/high-availability)

</details>

---

### Question 22: Recovery Services Vault for VMs and SQL

A company needs to back up Azure VMs and SQL Server databases running on Azure VMs. They need 7-year retention for compliance and the ability to restore in a different region if the primary region fails. What should you configure?

- A. Recovery Services Vault with GRS and long-term retention policy
- B. Backup Vault with LRS
- C. Azure Site Recovery with 7-year retention
- D. Storage account with blob versioning

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

Recovery Services Vault supports both Azure VMs and SQL in VMs. GRS provides cross-region restore capability. Long-term retention policies support up to 10 years.

**Why other answers are incorrect:**
- **B is wrong:** Backup Vault supports blobs and disks, not VMs or SQL. LRS doesn't enable cross-region restore.
- **C is wrong:** ASR is for disaster recovery (replication), not long-term backup retention.
- **D is wrong:** Blob versioning is for blob data, not VM or SQL backups, and doesn't provide structured backup management.

**Reference:**
- [Recovery Services vaults overview](https://learn.microsoft.com/azure/backup/backup-azure-recovery-services-vault-overview)
- [Long-term retention using Azure Backup](https://learn.microsoft.com/azure/backup/backup-azure-long-term-retention)

</details>

---

### Question 23: Azure Site Recovery with Ordered Failover

A company runs a 3-tier application on Azure VMs. They need to ensure the VMs start in the correct order during DR failover: database first, then application servers, then web servers. What ASR feature should you use?

- A. Replication policy with app-consistent snapshots
- B. Recovery plan with groups and sequenced actions
- C. Automation runbook triggered by Azure Monitor
- D. Availability set with fault domains

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Recovery plans allow you to group VMs and define startup order. Group 1 (database), Group 2 (app tier), Group 3 (web tier) with pre/post scripts between groups.

**Why other answers are incorrect:**
- **A is wrong:** Replication policy controls RPO and snapshot frequency, not failover sequencing.
- **C is wrong:** Runbooks can be part of a recovery plan but don't define VM startup order by themselves.
- **D is wrong:** Availability sets provide rack-level redundancy, not DR failover sequencing.

**Reference:**
- [About Site Recovery recovery plans](https://learn.microsoft.com/azure/site-recovery/site-recovery-create-recovery-plans)
- [Customize recovery plans](https://learn.microsoft.com/azure/site-recovery/site-recovery-runbook-automation)

</details>

---

### Question 24: Composite SLA Calculation

An application uses App Service (99.95% SLA), Azure SQL (99.99% SLA), and Azure Cache for Redis Standard (99.9% SLA) in a chain. What is the composite SLA?

- A. 99.99%
- B. 99.95%
- C. 99.84%
- D. 99.9%

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

Composite SLA = 0.9995 × 0.9999 × 0.999 = 0.99840 = **99.84%**

For chained services, multiply individual SLAs. The result is always lower than the lowest individual SLA.

**Why other answers are incorrect:**
- **A is wrong:** You can't exceed the lowest individual SLA (99.9%) without redundancy.
- **B is wrong:** That's just the App Service SLA — you must account for all dependencies.
- **D is wrong:** That's just the Redis SLA.

**Reference:**
- [Composite SLAs](https://learn.microsoft.com/azure/architecture/framework/resiliency/business-metrics#composite-slas)
- [SLA for Azure services](https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services)

</details>

---

### Question 25: Availability Zones for 99.99% SLA

A company is deploying a new production application and needs the highest availability within a single region. The application uses VMs and requires a 99.99% SLA. What deployment model should you recommend?

- A. Single VM with Premium SSD
- B. VMs in an Availability Set
- C. VMs across Availability Zones
- D. VMs in a Virtual Machine Scale Set (single zone)

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

Availability Zones provide 99.99% SLA by distributing VMs across physically separate datacenters within a region.

**Why other answers are incorrect:**
- **A is wrong:** Single VM with Premium SSD provides only 99.9% SLA.
- **B is wrong:** Availability Sets provide 99.95% SLA (rack-level, not datacenter-level).
- **D is wrong:** VMSS in a single zone doesn't protect against datacenter failure.

**Reference:**
- [What are Availability Zones?](https://learn.microsoft.com/azure/reliability/availability-zones-overview)
- [SLA for Virtual Machines](https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services)

</details>

---

### Question 26: SQL Database Auto-Failover Groups

A company has an Azure SQL Database that serves users in East US and West Europe. They need automatic failover if East US goes down, with a single connection endpoint that doesn't change after failover. What should you recommend?

- A. Active geo-replication
- B. Auto-failover groups
- C. Point-in-time restore
- D. Geo-restore from GRS backup

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Auto-failover groups provide automatic failover with a stable DNS endpoint (e.g., `myserver-group.database.windows.net`) that doesn't change after failover. Applications don't need connection string changes.

**Why other answers are incorrect:**
- **A is wrong:** Active geo-replication provides readable replicas but requires manual failover and connection string changes.
- **C is wrong:** PITR restores to a point in time, doesn't provide automatic cross-region failover.
- **D is wrong:** Geo-restore creates a new database from GRS backup — slow (hours) and requires connection string changes.

**Reference:**
- [Auto-failover groups overview](https://learn.microsoft.com/azure/azure-sql/database/auto-failover-group-overview)
- [Configure a failover group](https://learn.microsoft.com/azure/azure-sql/database/auto-failover-group-configure-sql-db)

</details>

---

### Question 27: Storage Account Failover During Regional Outage

An application reads blobs from Azure Storage. During a regional outage, the application must continue reading blobs without waiting for Microsoft to initiate a failover. What redundancy should you recommend?

- A. GRS
- B. ZRS
- C. RA-GRS
- D. LRS

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

RA-GRS (Read-Access Geo-Redundant Storage) provides a secondary read endpoint that is accessible even during a primary region outage. The application can read from `*.secondary.blob.core.windows.net` immediately.

**Why other answers are incorrect:**
- **A is wrong:** GRS replicates to a paired region, but data is not accessible until Microsoft or customer initiates failover.
- **B is wrong:** ZRS protects against zone failure, not regional failure.
- **D is wrong:** LRS provides no cross-region protection.

**Reference:**
- [Azure Storage redundancy](https://learn.microsoft.com/azure/storage/common/storage-redundancy)
- [Read access to data in the secondary region](https://learn.microsoft.com/azure/storage/common/storage-redundancy#read-access-to-data-in-the-secondary-region)

</details>

---

### Question 28: Ransomware Protection for Backups

A company experienced a ransomware attack that encrypted their files and attempted to delete their Azure Backups. What features should you enable to protect backup data from deletion? (Choose the best combination)

- A. Soft delete + Immutable vault + Multi-user authorization
- B. Geo-redundant storage only
- C. Azure Site Recovery with daily snapshots
- D. Storage account firewall rules

<details>
<summary>Show Answer</summary>

**Correct Answer: A**

This combination provides defense-in-depth for backup data:
- **Soft delete:** Retains deleted backup data for 14+ days
- **Immutable vault:** Prevents disabling backup or reducing retention periods
- **Multi-user authorization (Resource Guard):** Requires additional approval for destructive operations

**Why other answers are incorrect:**
- **B is wrong:** GRS replicates backups across regions but doesn't prevent deletion.
- **C is wrong:** ASR is for VM replication, not backup protection.
- **D is wrong:** Firewall rules control network access but don't prevent authorized users from deleting backups.

**Reference:**
- [Enhanced soft delete for Azure Backup](https://learn.microsoft.com/azure/backup/backup-azure-enhanced-soft-delete-about)
- [Immutable vault for Azure Backup](https://learn.microsoft.com/azure/backup/backup-azure-immutable-vault-concept)
- [Multi-user authorization for Azure Backup](https://learn.microsoft.com/azure/backup/multi-user-authorization-concept)

</details>

---

### Question 29: Global Load Balancing with WAF and CDN

A company wants to deploy their web application across two Azure regions. They want traffic routed to the closest region and must have WAF protection and built-in CDN capabilities. What should you use as the global load balancer?

- A. Azure Traffic Manager
- B. Azure Front Door
- C. Azure Load Balancer (Standard)
- D. Azure Application Gateway

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Azure Front Door provides global HTTP/HTTPS load balancing with built-in CDN, WAF, and proximity-based routing. It operates at Layer 7 with edge POP locations worldwide.

**Why other answers are incorrect:**
- **A is wrong:** Traffic Manager does DNS-based routing but has no WAF or CDN capabilities.
- **C is wrong:** Load Balancer is regional (Layer 4), not global.
- **D is wrong:** Application Gateway is regional (Layer 7), not global.

**Reference:**
- [What is Azure Front Door?](https://learn.microsoft.com/azure/frontdoor/front-door-overview)
- [Azure Front Door tier comparison](https://learn.microsoft.com/azure/frontdoor/standard-premium/tier-comparison)

</details>

---

### Question 30: Cosmos DB Highest Availability SLA

A global e-commerce platform needs the highest possible availability SLA from Cosmos DB while serving both reads and writes from multiple regions. What should you configure?

- A. Single-region Cosmos DB with automatic failover
- B. Multi-region read replicas (single-write region)
- C. Multi-region writes with availability zones enabled
- D. Serverless Cosmos DB with geo-replication

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

Multi-region writes with availability zones provides the highest Cosmos DB SLA (99.999% for both reads and writes). Each region can accept writes, and zones protect against datacenter failure.

**Why other answers are incorrect:**
- **A is wrong:** Single region provides 99.99% SLA, lower than multi-region write (99.999%).
- **B is wrong:** Multi-region read gives 99.999% read SLA but only 99.99% write SLA (single write region).
- **D is wrong:** Serverless mode doesn't support multi-region writes or geo-replication.

**Reference:**
- [High availability with Azure Cosmos DB](https://learn.microsoft.com/azure/cosmos-db/high-availability)
- [Multi-region writes in Azure Cosmos DB](https://learn.microsoft.com/azure/cosmos-db/nosql/how-to-multi-master)

</details>

---

## Module 4: Infrastructure & Compute Solutions

*Exam Weight: 30-35% (Part 1) | Questions 31-40*

---

### Question 31: Compute Service for Variable Traffic

A company wants to deploy a web application that processes variable traffic. During peak hours, it handles 1000 requests/second; at night, it drops to near zero. The team has no container or Kubernetes experience. They want to minimize cost and management. What should you recommend?

- A. Azure Virtual Machines with VMSS
- B. Azure App Service (Standard plan)
- C. Azure Container Apps (Consumption plan)
- D. Azure App Service (Premium v3 plan)

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

Container Apps with Consumption plan scales to zero (no cost when idle), auto-scales on HTTP traffic, and requires no K8s expertise. Minimizes both cost and management for variable workloads.

**Why other answers are incorrect:**
- **A is wrong:** VMSS requires managing VMs and doesn't scale to zero.
- **B is wrong:** Standard App Service plan charges 24/7 even with no traffic.
- **D is wrong:** Premium v3 is even more expensive and doesn't scale to zero.

**Reference:**
- [Azure Container Apps overview](https://learn.microsoft.com/azure/container-apps/overview)
- [Container Apps pricing](https://learn.microsoft.com/azure/container-apps/billing)

</details>

---

### Question 32: Azure Functions for Long-Running Tasks with VNet

A company has an Azure Function that processes messages from a Service Bus queue. The processing takes 15 minutes per message. The Function must access resources in a VNet. What hosting plan should you recommend?

- A. Consumption plan
- B. Flex Consumption plan
- C. Premium plan
- D. Free tier App Service plan

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

Premium plan supports unlimited execution time (no timeout), VNet integration, and pre-warmed instances. Required for long-running + VNet scenarios.

**Why other answers are incorrect:**
- **A is wrong:** Consumption plan has a maximum 10-minute timeout, which can't handle 15-minute processing.
- **B is wrong:** Flex Consumption supports VNet and long execution but Premium is the established recommendation for guaranteed VNet + long-running.
- **D is wrong:** Free tier doesn't support Functions Premium capabilities.

**Reference:**
- [Azure Functions hosting options](https://learn.microsoft.com/azure/azure-functions/functions-scale)
- [Azure Functions Premium plan](https://learn.microsoft.com/azure/azure-functions/functions-premium-plan)

</details>

---

### Question 33: Event Hubs for High-Volume Telemetry

An IoT platform ingests telemetry from 100,000 sensors sending data every second. The data needs to be processed in near-real-time and archived to Azure Data Lake. What messaging service should you use?

- A. Azure Service Bus
- B. Azure Event Grid
- C. Azure Event Hubs
- D. Azure Queue Storage

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

Event Hubs handles millions of events per second with partitioned consumers, Capture (auto-archive to ADLS), and Kafka compatibility. Purpose-built for high-volume telemetry ingestion.

**Why other answers are incorrect:**
- **A is wrong:** Service Bus is for commands and workflows, not high-volume telemetry. Lower throughput ceiling.
- **B is wrong:** Event Grid is for discrete events (resource changes), not continuous telemetry streams.
- **D is wrong:** Queue Storage has limited throughput and lacks streaming features like partitions and capture.

**Reference:**
- [What is Azure Event Hubs?](https://learn.microsoft.com/azure/event-hubs/event-hubs-about)
- [Event Hubs Capture overview](https://learn.microsoft.com/azure/event-hubs/event-hubs-capture-overview)

</details>

---

### Question 34: Service Bus Topics for Pub/Sub

An application needs to notify multiple downstream services when a new order is placed. Each service should receive the notification independently. Messages must support dead-lettering for failed deliveries. What should you recommend?

- A. Azure Service Bus Queue
- B. Azure Service Bus Topic with subscriptions
- C. Azure Event Grid
- D. Azure Event Hubs

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Service Bus Topics support pub/sub with multiple subscriptions (each service gets its own copy), dead-letter queues for failed messages, and reliable delivery guarantees.

**Why other answers are incorrect:**
- **A is wrong:** Queues are point-to-point — only one consumer gets each message, not fan-out.
- **C is wrong:** Event Grid supports pub/sub but has limited dead-letter capabilities compared to Service Bus and is better for events, not commands.
- **D is wrong:** Event Hubs is for streaming, not pub/sub command patterns.

**Reference:**
- [Service Bus topics and subscriptions](https://learn.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions)
- [Service Bus dead-letter queues](https://learn.microsoft.com/azure/service-bus-messaging/service-bus-dead-letter-queues)

</details>

---

### Question 35: API Management with Internal VNet

A company is exposing internal APIs to external partners. They need rate limiting, OAuth 2.0 token validation, and the ability to publish API documentation for partners. The APIs are deployed in a VNet and must not be directly accessible from the internet. What should you recommend?

- A. APIM Consumption tier
- B. APIM Developer tier
- C. APIM Standard tier
- D. APIM Premium tier with internal VNet mode

<details>
<summary>Show Answer</summary>

**Correct Answer: D**

Premium tier supports internal VNet deployment (APIs not directly internet-accessible), rate limiting, JWT validation policies, and a developer portal for partner documentation.

**Why other answers are incorrect:**
- **A is wrong:** Consumption tier doesn't support VNet integration.
- **B is wrong:** Developer tier supports external VNet only, not internal mode. Also no SLA.
- **C is wrong:** Standard tier doesn't support VNet integration.

**Reference:**
- [API Management in virtual networks](https://learn.microsoft.com/azure/api-management/virtual-network-concepts)
- [API Management tier comparison](https://learn.microsoft.com/azure/api-management/api-management-features)

</details>

---

### Question 36: Caching with Azure Cache for Redis

A web application reads product catalog data from Azure SQL Database. The same data is read millions of times but updated only hourly. Response latency must be under 5ms. What should you recommend?

- A. Increase SQL Database tier to Business Critical
- B. Azure Cache for Redis with cache-aside pattern
- C. Cosmos DB with session consistency
- D. Azure CDN

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Redis provides sub-millisecond latency for cached data. Cache-aside pattern: check cache first → on miss, read from SQL → populate cache. Hourly updates can invalidate/refresh the cache.

**Why other answers are incorrect:**
- **A is wrong:** Upgrading SQL tier reduces query latency but can't match Redis sub-ms performance for repeated reads.
- **C is wrong:** Cosmos DB is a database, not a caching layer — adds complexity without solving the caching need.
- **D is wrong:** CDN caches static content at edge locations, not dynamic database query results.

**Reference:**
- [Azure Cache for Redis overview](https://learn.microsoft.com/azure/azure-cache-for-redis/cache-overview)
- [Cache-aside pattern](https://learn.microsoft.com/azure/architecture/patterns/cache-aside)

</details>

---

### Question 37: Migration Strategy for Legacy .NET Application

A company has a legacy .NET Framework 4.5 application running on IIS with a SQL Server 2016 backend. They have a 2-month deadline, no developer resources for code changes, and the database uses SQL Agent jobs and CLR assemblies. What migration strategy and target should you recommend?

- A. Rehost: VMs for app + SQL Server on Azure VM
- B. Refactor: App Service + Azure SQL Database
- C. Rehost: VMs for app + SQL Managed Instance
- D. Rearchitect: Container Apps + Cosmos DB

<details>
<summary>Show Answer</summary>

**Correct Answer: C**

The app is lift-and-shifted to a VM (no code changes needed). SQL Server migrates to SQL Managed Instance because it supports SQL Agent jobs and CLR (Azure SQL Database does not). This is a PaaS upgrade for the database while keeping the app as-is.

**Why other answers are incorrect:**
- **A is wrong:** SQL Server on VM works but misses the opportunity to use managed PaaS for the database.
- **B is wrong:** Azure SQL Database doesn't support SQL Agent or CLR. .NET Framework 4.5 on App Service may have compatibility issues.
- **D is wrong:** Rearchitecting violates the "no code changes" and 2-month deadline constraints.

**Reference:**
- [Migration guide: SQL Server to SQL Managed Instance](https://learn.microsoft.com/azure/azure-sql/migration-guides/managed-instance/sql-server-to-managed-instance-guide)
- [Cloud adoption strategy](https://learn.microsoft.com/azure/cloud-adoption-framework/migrate/azure-migration-guide/)

</details>

---

### Question 38: Azure Migrate for VMware Assessment

A company wants to migrate 200 VMware VMs to Azure. They need to assess readiness, right-size VMs, estimate costs, and understand dependencies between servers before migrating. What tools should they use?

- A. Azure Site Recovery only
- B. Azure Migrate with discovery, assessment, and dependency analysis
- C. Azure Data Box
- D. Azure Resource Mover

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Azure Migrate provides the complete discovery-assess-migrate workflow: automatic discovery of VMware VMs, readiness assessment, right-sizing recommendations, cost estimates, and dependency mapping (agent-based or agentless).

**Why other answers are incorrect:**
- **A is wrong:** ASR handles replication/failover but doesn't provide assessment, right-sizing, or dependency analysis.
- **C is wrong:** Data Box is for offline data transfer, not VM migration.
- **D is wrong:** Resource Mover moves existing Azure resources between regions, not on-premises to Azure.

**Reference:**
- [About Azure Migrate](https://learn.microsoft.com/azure/migrate/migrate-services-overview)
- [Discover and assess VMware VMs](https://learn.microsoft.com/azure/migrate/tutorial-discover-vmware)

</details>

---

### Question 39: Centralized Application Configuration

A development team deploys the same application to dev, staging, and production environments. They need to manage environment-specific configuration centrally, toggle features without redeployment, and keep secrets secure. What should you recommend?

- A. App Service application settings per environment
- B. Azure App Configuration with labels + feature flags + Key Vault references
- C. Environment variables in Docker containers
- D. Azure Key Vault only

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

App Configuration with labels (dev/staging/prod) provides centralized config per environment. Feature flags enable toggling without redeployment. Key Vault references securely pull secrets through App Configuration.

**Why other answers are incorrect:**
- **A is wrong:** App Service settings are per-instance, not centralized. No feature flag support.
- **C is wrong:** Docker environment variables are per-container, not centralized. No feature flags.
- **D is wrong:** Key Vault stores secrets but isn't designed for general configuration or feature flags.

**Reference:**
- [What is Azure App Configuration?](https://learn.microsoft.com/azure/azure-app-configuration/overview)
- [Use Key Vault references in App Configuration](https://learn.microsoft.com/azure/azure-app-configuration/use-key-vault-references-dotnet-core)
- [Feature management overview](https://learn.microsoft.com/azure/azure-app-configuration/concept-feature-management)

</details>

---

### Question 40: Azure Kubernetes Service for Advanced Scenarios

A company is deploying a microservices application with 15 services. The team has strong Kubernetes expertise and needs custom operators, a service mesh (Istio), and fine-grained control over pod networking with Azure CNI. What should you recommend?

- A. Azure Container Apps
- B. Azure Kubernetes Service (AKS)
- C. Azure Container Instances
- D. Azure App Service with containers

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

AKS provides full Kubernetes control: custom operators, CRDs, Istio service mesh, Azure CNI networking, and granular pod configuration. Required when teams need Kubernetes-level customization.

**Why other answers are incorrect:**
- **A is wrong:** Container Apps is opinionated and doesn't support custom operators, arbitrary service meshes, or Azure CNI.
- **C is wrong:** ACI runs individual containers, not orchestrated microservices with service mesh.
- **D is wrong:** App Service supports containers but not custom operators, Istio, or K8s-level networking.

**Reference:**
- [Azure Kubernetes Service (AKS)](https://learn.microsoft.com/azure/aks/intro-kubernetes)
- [Network concepts for AKS](https://learn.microsoft.com/azure/aks/concepts-network)
- [Istio-based service mesh add-on](https://learn.microsoft.com/azure/aks/istio-about)

</details>

---

## Module 5: Network Solutions

*Exam Weight: 30-35% (Part 2) | Questions 41-50*

---

### Question 41: Hub-Spoke Topology Design

A mid-sized company (10 VNets, 2 branch offices) needs a hub-spoke topology with centralized firewall, VPN gateway, and spoke isolation. Spokes should not communicate directly. What should you recommend?

- A. Azure Virtual WAN (Standard)
- B. Customer-managed hub-spoke with Azure Firewall and UDRs
- C. Full mesh VNet peering
- D. Azure Virtual WAN (Basic)

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

For small to medium deployments (< 30 VNets), a customer-managed hub-spoke is cost-effective and provides full control. Azure Firewall in the hub handles centralized filtering, and UDRs enforce spoke-to-hub routing. Spoke isolation is achieved by not peering spokes directly.

**Why other answers are incorrect:**
- **A is wrong:** Virtual WAN Standard works but is more expensive and complex than needed for 10 VNets.
- **C is wrong:** Full mesh peering allows direct spoke-to-spoke communication (violates isolation requirement) and doesn't scale.
- **D is wrong:** Virtual WAN Basic supports only S2S VPN, not ExpressRoute or transit routing.

**Reference:**
- [Hub-spoke network topology](https://learn.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
- [Azure Firewall architecture overview](https://learn.microsoft.com/azure/architecture/example-scenario/firewalls/)

</details>

---

### Question 42: ExpressRoute for Private Connectivity

A healthcare organization needs private connectivity from their on-premises datacenter to Azure. Traffic must NOT traverse the public internet. They need 2 Gbps bandwidth and connections to Azure services in their region. What should you recommend?

- A. VPN Gateway (VpnGw3)
- B. ExpressRoute (Standard)
- C. VPN Gateway with Azure Virtual WAN
- D. Azure Peering Service

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

ExpressRoute provides private connectivity that does NOT traverse the public internet. Standard SKU covers same geopolitical region. 2 Gbps circuits are available.

**Why other answers are incorrect:**
- **A is wrong:** VPN Gateway uses encrypted tunnels over the public internet — the requirement explicitly states "must NOT traverse the public internet."
- **C is wrong:** VPN through Virtual WAN still uses the internet.
- **D is wrong:** Peering Service improves internet routing to Microsoft services but still uses the internet path.

**Reference:**
- [What is Azure ExpressRoute?](https://learn.microsoft.com/azure/expressroute/expressroute-introduction)
- [ExpressRoute connectivity models](https://learn.microsoft.com/azure/expressroute/expressroute-connectivity-models)

</details>

---

### Question 43: Private Endpoints vs Service Endpoints

A company uses Azure SQL Database and Azure Storage. They need to ensure these services are only accessible from within their VNet and from on-premises via ExpressRoute. They also need to prevent data exfiltration to other Azure SQL instances. What should you recommend?

- A. Service Endpoints on both services
- B. Private Endpoints for both services
- C. Azure Firewall with application rules
- D. NSG rules blocking internet traffic

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Private Endpoints assign private IPs in the VNet, accessible via ExpressRoute from on-premises. They prevent data exfiltration because the endpoint points to a specific resource instance (not any SQL server). Service Endpoints don't prevent exfiltration and aren't accessible from on-premises.

**Why other answers are incorrect:**
- **A is wrong:** Service Endpoints don't prevent data exfiltration (can access any storage account in the service), and aren't accessible from on-premises.
- **C is wrong:** Azure Firewall controls traffic flow but doesn't give PaaS services private IPs for VNet/on-prem access.
- **D is wrong:** NSGs can't restrict traffic to specific PaaS resource instances.

**Reference:**
- [What is Azure Private Link?](https://learn.microsoft.com/azure/private-link/private-link-overview)
- [Private Endpoints](https://learn.microsoft.com/azure/private-link/private-endpoint-overview)
- [Virtual Network service endpoints](https://learn.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview)

</details>

---

### Question 44: Application Security Groups for Logical Grouping

A company needs to filter traffic at the subnet level within a spoke VNet. They need to allow HTTP traffic from web VMs to app VMs using logical groupings, without managing individual IP addresses. What should you use?

- A. Azure Firewall with network rules
- B. NSG with Application Security Groups (ASGs)
- C. Azure Firewall with application rules
- D. NSG with IP-based rules

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

NSGs with ASGs allow you to define rules using logical groups (WebASG → AppASG on port 80/443) without managing individual IP addresses. This is the simplest and most cost-effective solution for subnet-level filtering.

**Why other answers are incorrect:**
- **A is wrong:** Azure Firewall is centralized (hub-level), more expensive, and overkill for simple subnet-level rules.
- **C is wrong:** Same as A — application rules filter by FQDN, unnecessary for VM-to-VM traffic.
- **D is wrong:** IP-based NSG rules work but require manual IP management, violating the "without managing individual IPs" requirement.

**Reference:**
- [Application security groups](https://learn.microsoft.com/azure/virtual-network/application-security-groups)
- [Network security groups](https://learn.microsoft.com/azure/virtual-network/network-security-groups-overview)

</details>

---

### Question 45: Azure Front Door for Global Application

A company runs a global e-commerce website across East US and West Europe. They need OWASP protection, CDN caching for static assets, and fast failover between regions. What should you recommend?

- A. Application Gateway WAF v2 in each region
- B. Azure Front Door Premium with WAF
- C. Traffic Manager with Application Gateway WAF in each region
- D. Azure CDN (Standard) with NSG rules

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Azure Front Door Premium provides global L7 load balancing, built-in CDN, WAF with OWASP protection, and fast connection-level failover. Single service covers all three requirements.

**Why other answers are incorrect:**
- **A is wrong:** Application Gateway is regional. Two separate WAF instances don't provide global load balancing or CDN.
- **C is wrong:** Traffic Manager + App Gateway works but has slower DNS-based failover, no built-in CDN, and more complexity.
- **D is wrong:** Azure CDN doesn't provide WAF or intelligent routing. NSGs don't protect against OWASP attacks.

**Reference:**
- [What is Azure Front Door?](https://learn.microsoft.com/azure/frontdoor/front-door-overview)
- [Web Application Firewall on Azure Front Door](https://learn.microsoft.com/azure/web-application-firewall/afds/afds-overview)

</details>

---

### Question 46: Load Balancing for Multi-Tier Application

An application has a web tier (HTTP), an application tier (TCP port 8080), and a database tier. The web tier needs URL-based routing and SSL offload. The app tier just needs TCP load balancing. What combination should you use?

- A. Azure Front Door for web tier, Load Balancer for app tier
- B. Application Gateway for web tier, Internal Load Balancer for app tier
- C. Load Balancer for both tiers
- D. Application Gateway for both tiers

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Application Gateway provides L7 features (URL routing, SSL offload) for the web tier. Internal Load Balancer efficiently handles TCP load balancing for the app tier. Right tool for each tier.

**Why other answers are incorrect:**
- **A is wrong:** Front Door is global — overkill for a single-region internal architecture.
- **C is wrong:** Load Balancer is L4 only — can't do URL-based routing or SSL offload.
- **D is wrong:** Application Gateway handles L7 HTTP/HTTPS only. TCP 8080 is better served by Load Balancer (simpler, lower latency).

**Reference:**
- [What is Azure Application Gateway?](https://learn.microsoft.com/azure/application-gateway/overview)
- [What is Azure Load Balancer?](https://learn.microsoft.com/azure/load-balancer/load-balancer-overview)

</details>

---

### Question 47: DDoS Protection Cost Optimization

A company has 3 public IP addresses in Azure. They want DDoS mitigation beyond the default infrastructure protection. They want the most cost-effective option. What should you recommend?

- A. DDoS Network Protection
- B. DDoS IP Protection
- C. Azure Firewall Premium
- D. NSG rules to block suspicious IPs

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

DDoS IP Protection costs ~$199/month per IP (3 × $199 = $597/month). DDoS Network Protection costs ~$2,944/month regardless of IP count. For 3 IPs, IP Protection is significantly cheaper.

**Why other answers are incorrect:**
- **A is wrong:** Network Protection at $2,944/month is much more expensive for only 3 IPs. It becomes cost-effective at ~15+ IPs.
- **C is wrong:** Azure Firewall provides network filtering, not DDoS protection specifically.
- **D is wrong:** NSG rules can block known IPs but can't handle volumetric DDoS attacks dynamically.

**Reference:**
- [Azure DDoS Protection overview](https://learn.microsoft.com/azure/ddos-protection/ddos-protection-overview)
- [DDoS Protection SKU comparison](https://learn.microsoft.com/azure/ddos-protection/ddos-protection-sku-comparison)

</details>

---

### Question 48: Azure DNS Private Resolver

A company has a hub-spoke network with Private Endpoints for Azure SQL and Storage. On-premises servers connected via ExpressRoute need to resolve the `privatelink.*` DNS zones. What should you deploy?

- A. Custom DNS server in hub VNet
- B. Azure DNS Private Resolver with inbound endpoint
- C. Conditional forwarders on on-premises DNS only
- D. Public DNS zone with A records

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Azure DNS Private Resolver with an inbound endpoint allows on-premises DNS servers to forward `privatelink.*` queries to Azure, which resolves them using the Private DNS zones linked to the VNet.

**Why other answers are incorrect:**
- **A is wrong:** Custom DNS VMs work but require managing OS, patching, and HA — Private Resolver is a managed service.
- **C is wrong:** On-prem conditional forwarders need something in Azure to forward TO — the Private Resolver's inbound endpoint serves as that target.
- **D is wrong:** Public DNS would expose private IP addresses publicly and bypass the purpose of Private Endpoints.

**Reference:**
- [What is Azure DNS Private Resolver?](https://learn.microsoft.com/azure/dns/dns-private-resolver-overview)
- [Resolve Azure Private Endpoint DNS configuration](https://learn.microsoft.com/azure/private-link/private-endpoint-dns)

</details>

---

### Question 49: Azure Bastion with Native Client Support

A company's security policy requires that no VMs have public IP addresses. Administrators need to RDP into Windows VMs and SSH into Linux VMs from their laptops using native RDP/SSH clients (not just the Azure portal). What Bastion tier do you need?

- A. Basic
- B. Standard
- C. Premium
- D. Bastion is not needed — use JIT VM access

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Standard tier supports native client connectivity (az network bastion rdp/ssh commands) in addition to portal access. Basic tier only supports portal-based RDP/SSH.

**Why other answers are incorrect:**
- **A is wrong:** Basic tier only supports browser-based access via Azure portal, not native RDP/SSH clients.
- **C is wrong:** Premium adds session recording but Standard is sufficient for native client support.
- **D is wrong:** JIT VM access temporarily opens NSG rules but still requires a public IP on the VM, violating the security policy.

**Reference:**
- [What is Azure Bastion?](https://learn.microsoft.com/azure/bastion/bastion-overview)
- [Azure Bastion SKU comparison](https://learn.microsoft.com/azure/bastion/configuration-settings#skus)

</details>

---

### Question 50: Traffic Manager for Non-HTTP Protocols

A company deploys a non-HTTP application (custom TCP protocol) across East US and West Europe. They need automatic failover to the healthy region with the lowest latency. What global load balancing solution should they use?

- A. Azure Front Door
- B. Azure Traffic Manager with Performance routing
- C. Azure Application Gateway
- D. Azure Load Balancer (Standard)

<details>
<summary>Show Answer</summary>

**Correct Answer: B**

Traffic Manager supports any protocol (including custom TCP) with DNS-based routing. Performance routing directs users to the lowest-latency endpoint. Health probes detect failures for failover.

**Why other answers are incorrect:**
- **A is wrong:** Front Door only supports HTTP/HTTPS, not custom TCP protocols.
- **C is wrong:** Application Gateway is regional, not global.
- **D is wrong:** Standard Load Balancer is regional. Cross-region LB exists but is simpler than needed; Traffic Manager with Performance routing is the standard recommendation.

**Reference:**
- [What is Azure Traffic Manager?](https://learn.microsoft.com/azure/traffic-manager/traffic-manager-overview)
- [Traffic Manager routing methods](https://learn.microsoft.com/azure/traffic-manager/traffic-manager-routing-methods)

</details>

---

## Scoring Guide

### Overall Assessment

| Score | Readiness Level | Recommendation |
|-------|----------------|----------------|
| 45-50 / 50 (90-100%) | Excellent | You're ready to schedule the exam. Review any missed questions. |
| 40-44 / 50 (80-88%) | Good | Review missed topics and retake weak sections before scheduling. |
| 30-39 / 50 (60-78%) | Needs Improvement | Study modules where you scored below 70% before retaking. |
| Below 30 / 50 (<60%) | Not Ready | Review all course materials and retake the full assessment. |

### Module-Level Assessment

Review your score in each module section:

| Module | Questions | Target Score |
|--------|-----------|-------------|
| Module 1: Identity, Governance & Monitoring | Q1-Q10 | 8+ / 10 |
| Module 2: Data Storage Solutions | Q11-Q20 | 8+ / 10 |
| Module 3: Business Continuity & DR | Q21-Q30 | 8+ / 10 |
| Module 4: Infrastructure & Compute | Q31-Q40 | 8+ / 10 |
| Module 5: Network Solutions | Q41-Q50 | 8+ / 10 |

If you score below 70% in any module, revisit those lessons before taking the official exam.

---

## Final Exam Preparation Steps

1. **[IMMEDIATE]** Take the [official Microsoft practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
2. **[SHORT-TERM]** Review the [AZ-305 Study Guide](https://learn.microsoft.com/credentials/certifications/resources/study-guides/az-305) and ensure you understand all exam objectives
3. **[LONG-TERM]** [Schedule your exam](https://learn.microsoft.com/credentials/certifications/exams/az-305) when you consistently score 80%+ on practice assessments

---

## Additional Resources

- **Exam Page:** [AZ-305: Designing Microsoft Azure Infrastructure Solutions](https://learn.microsoft.com/credentials/certifications/exams/az-305)
- **Study Guide:** [AZ-305 Study Guide](https://learn.microsoft.com/credentials/certifications/resources/study-guides/az-305)
- **Azure Architecture Center:** [Architecture best practices](https://learn.microsoft.com/azure/architecture/)
- **Well-Architected Framework:** [Five pillars](https://learn.microsoft.com/azure/well-architected/)
- **Cloud Adoption Framework:** [Migration guidance](https://learn.microsoft.com/azure/cloud-adoption-framework/)
- **Official Labs:** [Microsoft Learning AZ-305 Labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/)

---

**Good luck with your AZ-305 exam preparation!**
