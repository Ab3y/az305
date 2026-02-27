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

| API | Use Case | Data Model | Exam Keyword |
|-----|----------|-----------|--------------|
| **NoSQL (Core)** | New applications, most flexible | JSON documents | Default recommendation |
| **MongoDB** | Existing MongoDB apps | BSON documents | "Migrate MongoDB" |
| **Cassandra** | Wide-column, write-heavy | Column families | "Migrate Cassandra" |
| **Gremlin** | Graph relationships | Graph (vertices/edges) | "Social network, recommendations" |
| **Table** | Key-value, simple | Key-value pairs | "Migrate from Table Storage" |

**Exam Rule:** For new projects, always recommend the **NoSQL (Core) API** unless the question explicitly mentions an existing MongoDB/Cassandra/Graph workload.

### Partition Key Selection

The most critical Cosmos DB design decision. **Cannot be changed after creation.**

| Criteria | Good Partition Key | Bad Partition Key |
|----------|------------------|-------------------|
| Cardinality | High (tenantId, userId) | Low (status, country) |
| Distribution | Even across partitions | Hot partitions (all writes to one) |
| Query scope | Included in most queries | Rarely in WHERE clause |
| Size | Each logical partition < 20 GB | Single partition > 20 GB |

**Example Decisions:**
| Scenario | Good Key | Bad Key | Why |
|----------|----------|---------|-----|
| Multi-tenant SaaS | `/tenantId` | `/status` | Even distribution, tenant-scoped queries |
| E-commerce orders | `/customerId` | `/orderDate` | Customer queries are common |
| IoT telemetry | `/deviceId` | `/sensorType` | Per-device queries, even distribution |

### Consistency Levels

| Level | Guarantee | Latency | Cost | Exam Use Case |
|-------|----------|---------|------|--------------|
| **Strong** | Linearizable reads | Highest | Highest | Financial transactions |
| **Bounded Staleness** | Reads lag by K versions or T time | High | High | Leaderboards, counters |
| **Session** | Read-your-writes within session | Medium | Medium | **Default — recommended for most** |
| **Consistent Prefix** | Reads never see out-of-order writes | Low | Low | Social media feeds |
| **Eventual** | No ordering guarantee | Lowest | Lowest | Analytics, non-critical reads |

### Provisioned vs. Serverless

| Model | Best For | RU Billing |
|-------|----------|-----------|
| **Provisioned** | Production, predictable throughput | Per-second RU/s (reserved) |
| **Autoscale** | Variable but somewhat predictable | Auto-scales 10%-100% of max RU/s |
| **Serverless** | Dev/test, low/intermittent traffic | Per-request RU consumption |

### Global Distribution

```
Multi-Region Writes:
  East US (Read/Write) <──> West Europe (Read/Write) <──> SE Asia (Read/Write)
  
Single-Region Write + Multi-Region Read:
  East US (Write) ──replicate──> West Europe (Read) ──replicate──> SE Asia (Read)
```

| Configuration | Latency | Cost | Use Case |
|--------------|---------|------|----------|
| Single region | Lowest cost | $ | Regional apps |
| Multi-region read | Low reads globally | $$ | Global apps, read-heavy |
| Multi-region write | <10ms writes globally | $$$ | Global apps, write-heavy |

**Conflict Resolution (multi-region writes):**
- Last-Writer-Wins (LWW): Default, simple, uses `_ts` timestamp
- Custom: Stored procedure for merge logic

---

## 2. Azure Blob Storage

### Storage Account Types

| Type | Performance | Redundancy | Use Case |
|------|-------------|-----------|----------|
| **General-purpose v2** | Standard (HDD) | LRS/ZRS/GRS/GZRS | Most workloads |
| **Premium Block Blob** | Premium (SSD) | LRS/ZRS | Low-latency, high transaction |
| **Premium File Shares** | Premium (SSD) | LRS/ZRS | Enterprise file shares |
| **Premium Page Blobs** | Premium (SSD) | LRS | VM disks (unmanaged) |

### Access Tiers

| Tier | Min Retention | Access Cost | Storage Cost | Use Case |
|------|-------------|-------------|-------------|----------|
| **Hot** | None | Lowest | Highest | Frequently accessed data |
| **Cool** | 30 days | Medium | Medium | Infrequent access (monthly) |
| **Cold** | 90 days | Higher | Lower | Rare access (quarterly) |
| **Archive** | 180 days | Highest (rehydrate first) | Lowest | Compliance, long-term backup |

### Lifecycle Management

Automate tier transitions with policies:

```json
{
  "rules": [
    {
      "name": "MoveToCloseAfter30Days",
      "type": "Lifecycle",
      "definition": {
        "filters": { "blobTypes": ["blockBlob"], "prefixMatch": ["logs/"] },
        "actions": {
          "baseBlob": {
            "tierToCool": { "daysAfterModificationGreaterThan": 30 },
            "tierToArchive": { "daysAfterModificationGreaterThan": 180 },
            "delete": { "daysAfterModificationGreaterThan": 365 }
          }
        }
      }
    }
  ]
}
```

### Redundancy Options

| Option | Copies | Scope | SLA | Exam Keyword |
|--------|--------|-------|-----|-------------|
| **LRS** | 3 | Single datacenter | 99.9% | "Cost sensitive" |
| **ZRS** | 3 | 3 availability zones | 99.9% | "Zone failure" |
| **GRS** | 6 | 2 regions | 99.9% | "Regional outage" |
| **GZRS** | 6 | 3 zones + paired region | 99.9% | "Zone + regional failure" |
| **RA-GRS** | 6 | 2 regions, read in secondary | 99.99% | "Read during outage" |
| **RA-GZRS** | 6 | 3 zones + paired region, read | 99.99% | "Highest durability" |

### Data Protection Features

| Feature | Purpose | Exam Keyword |
|---------|---------|-------------|
| **Soft delete** | Recover deleted blobs (1-365 days) | "Accidental deletion" |
| **Versioning** | Keep previous versions of blobs | "Track changes" |
| **Point-in-time restore** | Restore container to a previous state | "Ransomware recovery" |
| **Immutable storage** | Prevent modification/deletion | "Regulatory compliance" |
| **Legal hold** | Immutable until hold removed | "Litigation hold" |
| **Time-based retention** | Immutable for set period | "WORM compliance" |

---

## 3. Azure Data Lake Storage Gen2

Data Lake Storage Gen2 = Blob Storage + Hierarchical Namespace (HNS)

| Feature | Blob Storage | Data Lake Gen2 |
|---------|-------------|----------------|
| Namespace | Flat | Hierarchical (true directories) |
| Rename/move operations | Expensive (copy+delete) | Atomic (instant) |
| ACLs | Container-level | File/directory-level (POSIX) |
| Analytics integration | Good | Optimized (Spark, Synapse) |
| Lifecycle management | Yes | Yes |
| Cost | Standard | Standard (same pricing) |

### Data Lake Design Pattern (Medallion Architecture)

```
Bronze (Raw)          Silver (Cleansed)      Gold (Curated)
  /raw/                 /cleansed/             /curated/
  ├── source1/          ├── domain1/           ├── sales-report/
  ├── source2/          ├── domain2/           ├── finance-summary/
  └── source3/          └── domain3/           └── ml-features/

  Hot tier              Cool tier              Hot tier
  Append-only           Updated daily          Queried frequently
```

---

## 4. Azure Files

| Feature | Standard | Premium |
|---------|----------|---------|
| Protocol | SMB 3.x, NFS 4.1 | SMB 3.x, NFS 4.1 |
| Performance | HDD-backed | SSD-backed |
| Max share size | 100 TiB | 100 TiB |
| IOPS | Up to 20,000 | Up to 100,000 |
| Use case | File shares, lift-and-shift | Low-latency file workloads |

### Azure Files vs. Azure NetApp Files

| Factor | Azure Files | Azure NetApp Files |
|--------|------------|-------------------|
| Performance | Standard/Premium | Ultra-low latency |
| Protocol | SMB, NFS 4.1 | SMB, NFS 3/4.1 |
| Use case | General file shares | SAP, HPC, databases |
| Cost | Lower | Higher |
| Management | Standard storage account | Dedicated NetApp service |

### Azure File Sync

Extends Azure Files to on-premises Windows Servers:
- **Cloud tiering:** Frequently accessed files local, cold files in cloud
- **Multi-site sync:** Sync same share across multiple Windows Servers
- **Rapid DR:** Provision new server, install agent, instant access to files

---

## 5. Summary Decision Matrix

| Data Type | Service | Key Decision Factor |
|-----------|---------|-------------------|
| JSON documents, globally distributed | Cosmos DB (NoSQL API) | Partition key, consistency level |
| Key-value, simple queries | Cosmos DB (Table API) or Table Storage | Cost vs. features |
| Graph relationships | Cosmos DB (Gremlin API) | Social, recommendation engines |
| Binary files, media, backups | Blob Storage | Access tier, redundancy |
| Big data analytics | Data Lake Storage Gen2 | Hierarchical namespace |
| File shares (SMB/NFS) | Azure Files | Standard vs. Premium |
| Ultra-low latency files | Azure NetApp Files | SAP, HPC |

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
