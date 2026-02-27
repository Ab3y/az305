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

<details>
<summary>Show Answer</summary>

**Correct: B**

SQL Managed Instance provides ~100% SQL Server compatibility including SQL Agent, CLR, and cross-database queries in a fully managed PaaS service — minimal code changes needed.

- **A is wrong:** SQL Database doesn't support SQL Agent jobs natively, CLR, or cross-database queries.
- **C is wrong:** SQL on VM works but isn't "fully managed" — you manage patching, HA, backups.
- **D is wrong:** PostgreSQL is a different database engine entirely.
</details>

---

### Q2. Compute Tier Selection

A startup has a database that is heavily used during business hours (8 AM - 6 PM) but nearly idle at night and on weekends. They want to minimize costs. What should you recommend?

- A. Azure SQL Database — Serverless compute tier
- B. Azure SQL Database — General Purpose provisioned
- C. Azure SQL Database — Hyperscale tier
- D. Azure SQL Managed Instance

<details>
<summary>Show Answer</summary>

**Correct: A**

Serverless auto-pauses when idle (no compute charges) and auto-scales during active periods. Ideal for intermittent workloads with significant idle time.

- **B is wrong:** Provisioned compute charges continuously, even during idle hours.
- **C is wrong:** Hyperscale is for very large databases, not cost optimization for variable workloads.
- **D is wrong:** SQL MI is always running — no auto-pause capability.
</details>

---

### Q3. Elastic Pools

A SaaS company has 50 tenant databases. Each averages 5 DTUs but can spike to 50 DTUs. Spikes don't happen simultaneously. What should you recommend?

- A. 50 individual S3 databases (100 DTUs each)
- B. An elastic pool with 500 eDTUs shared across all databases
- C. 50 individual serverless databases
- D. A single database with row-level security for multi-tenancy

<details>
<summary>Show Answer</summary>

**Correct: B**

Elastic pools are designed for this exact scenario — multiple databases with variable, non-overlapping peak usage sharing a common resource pool. 500 eDTUs handles peaks while averaging much lower usage.

- **A is wrong:** Over-provisioning each database at peak capacity wastes resources and budget.
- **C is wrong:** 50 individual serverless databases don't share resources and each has minimum billing.
- **D is wrong:** Single database with RLS is a different architecture — operational complexity and doesn't scale the same way.
</details>

---

### Q4. Cosmos DB Partition Key

An e-commerce application stores orders in Cosmos DB. Queries are typically by customer (get all orders for a customer) and by order ID. The company has millions of customers worldwide. What partition key should you recommend?

- A. `/customerId`
- B. `/orderDate`
- C. `/status`
- D. `/region`

<details>
<summary>Show Answer</summary>

**Correct: A**

`/customerId` has high cardinality (millions of unique values), enables even distribution, and aligns with the most common query pattern (get orders by customer). Point reads by orderId within a customer partition are efficient.

- **B is wrong:** Date-based keys create hot partitions (all writes go to "today's" partition).
- **C is wrong:** Status has low cardinality (e.g., "pending," "shipped," "delivered") — creates very uneven distribution.
- **D is wrong:** Region has low cardinality and doesn't align with the primary query pattern.
</details>

---

### Q5. Cosmos DB Consistency

A financial application processes bank transfers between accounts. The application must guarantee that after a transfer, both the debit and credit are immediately visible to all readers. What Cosmos DB consistency level should you recommend?

- A. Strong
- B. Session
- C. Bounded Staleness
- D. Eventual

<details>
<summary>Show Answer</summary>

**Correct: A**

Strong consistency guarantees linearizable reads — after a write completes, all subsequent reads return the updated value. Required for financial transactions where read-after-write consistency across all clients is mandatory.

- **B is wrong:** Session consistency only guarantees read-your-writes within a single session, not across all readers.
- **C is wrong:** Bounded Staleness allows a configurable lag — not appropriate for immediate financial visibility.
- **D is wrong:** Eventual consistency offers no ordering guarantees — unacceptable for financial data.
</details>

---

### Q6. Storage Redundancy

A healthcare company stores medical images in Azure Blob Storage. Regulatory requirements mandate that data must survive a regional outage, and the application must be able to read data even during a regional failover. What redundancy option should you recommend?

- A. RA-GRS (Read-Access Geo-Redundant Storage)
- B. GRS (Geo-Redundant Storage)
- C. ZRS (Zone-Redundant Storage)
- D. LRS (Locally Redundant Storage)

<details>
<summary>Show Answer</summary>

**Correct: A**

RA-GRS provides 6 copies across two regions (like GRS) PLUS read access to the secondary region during normal operations. The application can read from the secondary if the primary region fails.

- **B is wrong:** GRS replicates to a secondary region but data is NOT readable until Microsoft initiates a failover.
- **C is wrong:** ZRS protects against zone failures within a single region, not regional outages.
- **D is wrong:** LRS has 3 copies in a single datacenter — no protection against zone or regional failure.
</details>

---

### Q7. Immutable Storage

A law firm must store legal documents that cannot be modified or deleted for 7 years to comply with SEC Rule 17a-4. What should you recommend?

- A. Blob Storage with time-based immutable retention policy (7 years)
- B. Blob Storage with soft delete enabled (7-year retention)
- C. Blob Storage with versioning enabled
- D. Data Lake Storage Gen2 with ACLs

<details>
<summary>Show Answer</summary>

**Correct: A**

Time-based immutable retention policy implements true WORM (Write Once, Read Many) storage. Blobs cannot be modified or deleted until the retention period expires. This meets SEC 17a-4 compliance.

- **B is wrong:** Soft delete allows recovery of deleted data but doesn't prevent deletion in the first place.
- **C is wrong:** Versioning keeps copies but doesn't prevent deletion of all versions.
- **D is wrong:** ACLs control access permissions but don't enforce immutability.
</details>

---

### Q8. Data Lake Design

A retail company needs a data lake for analytics. They ingest data from 20 sources, need to perform transformations, and serve curated data to Power BI. They need file-level access control and atomic directory operations. What should you recommend?

- A. Azure Data Lake Storage Gen2 (Blob Storage with hierarchical namespace)
- B. Standard Azure Blob Storage
- C. Azure Files Premium
- D. Azure Cosmos DB with analytical store

<details>
<summary>Show Answer</summary>

**Correct: A**

ADLS Gen2 provides hierarchical namespace (true directories with atomic rename/move), file-level POSIX ACLs, and is optimized for analytics workloads (Synapse, Spark, Data Factory integration). Same cost as standard Blob Storage.

- **B is wrong:** Standard Blob Storage has a flat namespace — no atomic directory operations, no file-level ACLs.
- **C is wrong:** Azure Files is for file shares (SMB/NFS), not analytics data lakes.
- **D is wrong:** Cosmos DB analytical store is for operational analytics on Cosmos data, not a general-purpose data lake.
</details>

---

### Q9. Data Integration

A company needs to ingest data from on-premises SQL Server and Salesforce into Azure Data Lake Gen2, transform it, load it into a Synapse dedicated pool, and visualize in Power BI. Which service should orchestrate this pipeline?

- A. Azure Data Factory with self-hosted integration runtime
- B. Azure Stream Analytics
- C. Azure Logic Apps
- D. Azure Functions with timer trigger

<details>
<summary>Show Answer</summary>

**Correct: A**

Data Factory is the purpose-built ETL/ELT orchestration service. Self-hosted integration runtime enables secure access to on-premises SQL Server. Built-in connectors for Salesforce, ADLS Gen2, and Synapse.

- **B is wrong:** Stream Analytics is for real-time streaming, not batch ETL orchestration.
- **C is wrong:** Logic Apps is for workflow automation, not data integration pipelines.
- **D is wrong:** Azure Functions can process data but lacks built-in connectors, monitoring, and pipeline orchestration features.
</details>

---

### Q10. Analytics Service Selection

A data science team needs to run Apache Spark notebooks for machine learning model training. They require collaborative notebooks, Delta Lake for reliable data processing, and MLflow for experiment tracking. What should you recommend?

- A. Azure Databricks
- B. Azure Synapse Spark pool
- C. Azure HDInsight
- D. Azure Machine Learning compute

<details>
<summary>Show Answer</summary>

**Correct: A**

Databricks provides the richest Spark experience with collaborative notebooks, native Delta Lake support, and integrated MLflow for experiment tracking — exactly matching the requirements.

- **B is wrong:** Synapse Spark is good for unified analytics but has more limited notebook collaboration and no native MLflow.
- **C is wrong:** HDInsight is open-source Hadoop/Spark but requires more management and lacks Delta Lake integration.
- **D is wrong:** Azure ML compute is for ML training/inference, not general Spark data engineering with Delta Lake.
</details>

---

## Scoring

| Score | Next Step |
|-------|----------|
| 9-10 / 10 (90-100%) | Excellent! Move to Module 3 |
| 8 / 10 (80%) | Good. Review missed questions, then move to Module 3 |
| 6-7 / 10 (60-70%) | Review the relevant lessons before proceeding |
| Below 6 / 10 (<60%) | Re-study the full module before retaking |

---

## Continue Learning

- **MS Learn Path:** [Design data storage solutions](https://learn.microsoft.com/training/paths/design-data-storage-solutions/)
- **Case Studies:** [Non-relational storage](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/04-Nonrelationalstorage.html) | [Relational storage](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/03-Relationalstorage.html)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Next:** [Module 3 — Business Continuity](../module-3-business-continuity/overview.md)
