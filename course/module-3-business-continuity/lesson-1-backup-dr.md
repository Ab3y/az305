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

| Metric | Definition | Question It Answers |
|--------|-----------|-------------------|
| **RTO** (Recovery Time Objective) | Maximum acceptable downtime | "How long can you be down?" |
| **RPO** (Recovery Point Objective) | Maximum acceptable data loss | "How much data can you lose?" |

### Mapping Requirements to Solutions

| RTO / RPO | Solution Tier | Example Services |
|-----------|--------------|-----------------|
| RTO: hours, RPO: 24h | Basic | Azure Backup, geo-restore |
| RTO: minutes, RPO: hours | Standard | Azure Site Recovery, SQL PITR |
| RTO: seconds, RPO: ~0 | Premium | Active-active, synchronous replication |

```
   RPO (data loss)
   │
   │  High cost, complex
   │  ┌─────────────┐
   │  │ Active-Active│ (multi-region writes)
   │  │ Sync repl.   │
   │  └──────┬───────┘
   │         │
   │  ┌──────┴───────┐
   │  │ Hot Standby   │ (ASR, auto-failover groups)
   │  │ Near-sync     │
   │  └──────┬───────┘
   │         │
   │  ┌──────┴───────┐
   │  │ Warm Standby  │ (pilot light, snapshot restore)
   │  │ Periodic sync │
   │  └──────┬───────┘
   │         │
   │  ┌──────┴───────┐
   │  │ Cold / Backup │ (Azure Backup, geo-restore)
   │  │ Daily backups │
   │  └─────────────┘
   │  Low cost, simple
   └──────────────────────────> RTO (downtime)
```

---

## 2. Azure Backup

### What Can Azure Backup Protect?

| Workload | Agent / Method | Backup Frequency |
|----------|---------------|-----------------|
| **Azure VMs** | VM backup extension | Daily |
| **SQL Server in VM** | SQL backup extension | Full: daily; Log: every 15 min |
| **Azure Files** | Share snapshot | Daily |
| **Azure Blobs** | Operational/vaulted backup | Continuous / daily |
| **Azure Database for PostgreSQL** | Vaulted backup | Daily with log backup |
| **SAP HANA in VM** | HANA backup extension | Full: daily; Log: every 15 min |
| **Azure Managed Disks** | Disk backup | Hourly/daily |

### Recovery Services Vault vs. Backup Vault

| Feature | Recovery Services Vault | Backup Vault |
|---------|------------------------|-------------|
| Supports | VMs, SQL in VM, SAP HANA, Files, MARS | Blobs, Disks, PostgreSQL |
| Soft delete | 14 days (extendable) | 14 days (extendable) |
| Cross-region restore | Yes (GRS vaults) | Some workloads |
| Immutable vaults | Yes | Yes |

### Backup Redundancy

| Option | Protection | Exam Use Case |
|--------|-----------|--------------|
| **LRS** | 3 copies, single location | Cost-sensitive, low criticality |
| **ZRS** | 3 copies across zones | Zone resilience |
| **GRS** | 6 copies, paired region | Regional disaster recovery |

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

| Source | Destination | Use Case |
|--------|------------|----------|
| Azure VM (Region A) | Azure VM (Region B) | Azure-to-Azure DR |
| On-premises VMware | Azure | Cloud migration / DR |
| On-premises Hyper-V | Azure | Cloud migration / DR |
| Physical servers | Azure | Legacy server DR |

### Key Components

| Component | Purpose |
|-----------|---------|
| **Replication policy** | Defines RPO, recovery point retention, app-consistent snapshots |
| **Recovery plan** | Orchestrates failover sequence, groups VMs, includes scripts |
| **Test failover** | Non-disruptive DR drill in isolated network |
| **Failover** | Actual cutover to secondary region |
| **Failback** | Return to primary after outage resolved |

### RPO and Recovery Points

| Type | Frequency | Use Case |
|------|----------|----------|
| **Crash-consistent** | Every 5 minutes (default RPO) | VM state at point in time |
| **App-consistent** | Configurable (1-12 hours) | Consistent application state (VSS) |

### Recovery Plans

```
Recovery Plan: "Full Stack Failover"
  ├── Group 1: Database VMs (start first)
  │     ├── SQL Server Primary
  │     └── SQL Server Secondary
  ├── Pre-action: Script to verify DB replication
  ├── Group 2: Application VMs
  │     ├── App Server 1
  │     └── App Server 2
  ├── Post-action: Update DNS records
  └── Group 3: Web Front-End VMs
        ├── Web Server 1
        └── Web Server 2
```

---

## 4. Service-Specific DR Options

### Azure SQL Database DR

| Feature | Description | RTO | RPO |
|---------|------------|-----|-----|
| **Point-in-time restore** | Restore to any second within retention | Minutes-hours | Seconds |
| **Geo-restore** | Restore from GRS backup to any region | Hours | Up to 1 hour |
| **Active geo-replication** | Async replica in any region (up to 4) | Seconds | <5 seconds |
| **Auto-failover groups** | Automatic failover with DNS endpoint | 30 seconds | <5 seconds |

### Decision Matrix

```
Need automatic failover with DNS?
  ├── YES ──> Auto-failover groups
  └── NO
        Need cross-region readable replicas?
          ├── YES ──> Active geo-replication
          └── NO
                Need to recover from accidental deletion?
                  ├── YES ──> Point-in-time restore
                  └── NO  ──> Geo-restore (cheapest)
```

### Cosmos DB DR

| Configuration | RPO | How |
|--------------|-----|-----|
| Multi-region writes | ~0 | Synchronous within region, auto-failover |
| Single-region write + multi-region read | Seconds | Automatic regional failover |
| Service-managed failover | Minutes | Azure handles failover |

### Storage Account DR

| Feature | Description |
|---------|------------|
| **GRS/GZRS** | Async replication to paired region |
| **RA-GRS/RA-GZRS** | Read access during outage |
| **Customer-managed failover** | Initiate storage failover manually |
| **Object replication** | Async copy to another storage account (any region) |

---

## 5. Multi-Region Architecture Patterns

### Active-Passive

```
Traffic Manager / Front Door (failover routing)
  ├── Primary Region (ACTIVE)
  │     ├── App Service
  │     ├── SQL Database (R/W)
  │     └── Storage (R/W)
  └── Secondary Region (PASSIVE)
        ├── App Service (warm or cold)
        ├── SQL Database (read replica)
        └── Storage (GRS replication)

Failover: DNS reroutes to secondary (manual or auto)
```

### Active-Active

```
Front Door (priority or weighted routing)
  ├── Region A (ACTIVE)
  │     ├── App Service
  │     ├── Cosmos DB (multi-region writes)
  │     └── Storage (RA-GRS)
  └── Region B (ACTIVE)
        ├── App Service
        ├── Cosmos DB (multi-region writes)
        └── Storage (RA-GRS)

Both regions serve traffic simultaneously
```

| Pattern | RTO | Cost | Complexity | Exam Keyword |
|---------|-----|------|-----------|-------------|
| Active-Passive (cold) | Hours | $ | Low | "Minimize cost" |
| Active-Passive (warm) | Minutes | $$ | Medium | "Balance cost and RTO" |
| Active-Active | Seconds | $$$ | High | "Minimize downtime" |

---

## Summary Decision Matrix

| Scenario | Solution |
|----------|---------|
| VM disaster recovery | Azure Site Recovery |
| SQL Database auto-failover | Auto-failover groups |
| Protect against ransomware | Immutable vault + soft delete |
| VM/file backup | Recovery Services Vault |
| Blob backup | Backup Vault |
| On-prem to Azure DR | ASR with VMware/Hyper-V |
| Multi-region, zero downtime | Active-active with Cosmos DB |
| RTO: hours, RPO: daily | Azure Backup + geo-restore |

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
