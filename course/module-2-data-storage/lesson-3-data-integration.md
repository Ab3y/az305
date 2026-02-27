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

| Component | Purpose |
|-----------|---------|
| **Pipeline** | Logical grouping of activities |
| **Activity** | A processing step (copy, transform, control flow) |
| **Dataset** | Named reference to data (source or destination) |
| **Linked Service** | Connection string to data stores |
| **Trigger** | Defines when a pipeline runs (schedule, event, tumbling window) |
| **Integration Runtime** | Compute infrastructure for activities |

### Integration Runtime Types

| Type | Location | Use Case |
|------|----------|----------|
| **Azure** | Azure cloud | Cloud-to-cloud data movement |
| **Self-Hosted** | On-premises / VM | On-premises data access, private networks |
| **Azure-SSIS** | Azure cloud | Run existing SSIS packages |

### Key Patterns

| Pattern | Implementation | Exam Keyword |
|---------|---------------|-------------|
| **Full load** | Copy all data each run | Simple, small datasets |
| **Incremental load** | Copy only changed data (watermark column) | Large datasets, efficiency |
| **Event-driven** | Trigger pipeline on blob creation | Real-time ingestion |
| **Parameterized** | Dynamic datasets and linked services | Multi-tenant, reusable pipelines |
| **Metadata-driven** | Configuration table drives pipeline behavior | Enterprise-scale ingestion |

### Data Factory vs. Synapse Pipelines

| Feature | Data Factory | Synapse Pipelines |
|---------|-------------|-------------------|
| Engine | Same | Same |
| Standalone service | Yes | Embedded in Synapse workspace |
| Git integration | Yes | Yes |
| Monitoring | ADF Monitor | Synapse Studio Monitor |
| Best for | Pure ETL/ELT orchestration | Unified analytics (ETL + query + ML) |
| Data flows | Yes | Yes |
| Cost model | Per pipeline run | Per pipeline run |

**Exam Decision:** If the scenario is pure data movement/transformation → Data Factory. If the scenario includes analytics, Spark, or warehousing → Synapse (which includes pipelines).

---

## 2. Azure Synapse Analytics

### Components

| Component | Purpose | Billing Model |
|-----------|---------|--------------|
| **Dedicated SQL pool** | Data warehousing (MPP) | Reserved DWU (always running) |
| **Serverless SQL pool** | Ad-hoc queries over data lake | Per-TB scanned |
| **Apache Spark pool** | Big data processing, ML | Per-node-hour |
| **Pipelines** | Data orchestration (same as ADF) | Per-run |
| **Data Explorer pool** | Log and telemetry analytics (KQL) | Per-cluster |

### When to Use Each Pool

| Workload | Pool | Why |
|----------|------|-----|
| Enterprise data warehouse (star schema) | Dedicated SQL pool | MPP, optimized for complex queries |
| Ad-hoc queries over files in data lake | Serverless SQL pool | No infrastructure, pay-per-query |
| Data transformation, feature engineering | Spark pool | Distributed compute, Python/Scala/R |
| Real-time log analytics | Data Explorer pool | KQL, time-series optimized |

### Dedicated vs. Serverless Decision

```
Is the data warehouse queried continuously?
  ├── YES ──> Dedicated SQL pool (predictable performance)
  └── NO
        Is it ad-hoc/exploratory queries?
          ├── YES ──> Serverless SQL pool (pay per TB scanned)
          └── NO  ──> Consider dedicated (better TCO for frequent queries)
```

---

## 3. Other Analytics Services

### Azure Databricks

| Feature | Description |
|---------|-------------|
| Based on | Apache Spark (managed) |
| Differentiator | Collaborative notebooks, Delta Lake, MLflow |
| Best for | Advanced analytics, ML/AI, data engineering |
| Integration | Reads from ADLS Gen2, writes to SQL/Cosmos |

### Databricks vs. Synapse Spark

| Factor | Databricks | Synapse Spark |
|--------|-----------|---------------|
| Ecosystem | Rich partner ecosystem, Delta Lake | Integrated with Synapse workspace |
| Notebooks | Collaborative, multi-language | Integrated with SQL pools |
| ML support | MLflow, AutoML | SparkML, ONNX |
| Best for | Data science teams | Unified analytics teams |

### Azure Stream Analytics

Real-time stream processing using SQL-like query language.

| Pattern | Input | Processing | Output |
|---------|-------|-----------|--------|
| **IoT analytics** | IoT Hub / Event Hub | Windowed aggregation | Power BI, SQL, Cosmos |
| **Real-time dashboards** | Event Hub | Tumbling/sliding windows | Power BI |
| **Anomaly detection** | Event Hub | Built-in ML functions | Alert / Azure Function |

### Power BI Integration Points

| Data Source | Connection Type | Refresh |
|-------------|----------------|---------|
| Azure SQL | DirectQuery or Import | Real-time or scheduled |
| Synapse dedicated pool | DirectQuery | Real-time |
| Synapse serverless | DirectQuery | On-demand |
| Cosmos DB | Import | Scheduled |
| ADLS Gen2 | Dataflow | Scheduled |

---

## 4. Enterprise Data Platform Architecture

```
On-Premises / SaaS ──> Data Factory (orchestration) ──> ADLS Gen2 (Data Lake)
                              │                              │
                              v                              v
                        Self-Hosted IR              Bronze / Silver / Gold
                        (on-prem access)                     │
                                                             v
                                                    Synapse Analytics
                                                    ├── Dedicated pool (warehouse)
                                                    ├── Serverless pool (exploration)
                                                    └── Spark pool (transforms)
                                                             │
                                                             v
                                                         Power BI
                                                    (visualization layer)
```

### Key Design Principles

1. **Data Factory for orchestration**, Synapse/Spark for transformation
2. **ADLS Gen2 as the central data lake** (medallion architecture)
3. **Private endpoints for all data services**
4. **Managed identity for all pipeline authentication** (no connection strings in factories)
5. **Incremental loads** wherever possible (watermark pattern)

---

## 5. Summary Decision Matrix

| Scenario | Service |
|----------|---------|
| Cloud-to-cloud data movement | Data Factory |
| On-premises data access | Data Factory + Self-Hosted IR |
| Enterprise data warehouse | Synapse dedicated SQL pool |
| Ad-hoc queries on data lake files | Synapse serverless SQL pool |
| Big data / ML workloads | Databricks or Synapse Spark |
| Real-time stream processing | Stream Analytics |
| Business intelligence | Power BI |
| Unified analytics platform | Synapse Analytics workspace |

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
