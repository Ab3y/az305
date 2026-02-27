# Lesson 1: Relational Data Storage

**Duration:** 60 minutes | **Domain Weight:** Part of 20-25%

---

## Learning Objectives

- Recommend a solution for storing relational data
- Recommend a database service tier and compute tier
- Recommend a solution for database scalability
- Recommend a solution for data protection

---

## 1. Azure Relational Database Services

### Service Comparison

| Service | SQL Compatibility | Key Differentiator | Exam Use Case |
|---------|------------------|-------------------|---------------|
| **Azure SQL Database** | T-SQL subset | Fully managed PaaS, elastic pools | New cloud-native apps |
| **Azure SQL Managed Instance** | ~100% SQL Server | VNet integration, Agent jobs, CLR | Lift-and-shift SQL Server |
| **SQL Server on Azure VM** | 100% SQL Server | Full OS control | Legacy apps, custom configs |
| **Azure Database for PostgreSQL** | PostgreSQL | Open source, Citus for scale-out | PostgreSQL workloads |
| **Azure Database for MySQL** | MySQL | Open source | LAMP stack, WordPress |

### Decision Tree

```
Do you need full SQL Server feature compatibility?
  │
  ├── YES ──> Do you need OS-level control?
  │            ├── YES ──> SQL Server on Azure VM
  │            └── NO  ──> Azure SQL Managed Instance
  │
  └── NO  ──> Is it PostgreSQL or MySQL?
               ├── PostgreSQL ──> Azure Database for PostgreSQL
               ├── MySQL ──> Azure Database for MySQL
               └── SQL Server (T-SQL) ──> Azure SQL Database
```

### SQL MI vs. SQL Database — When It Matters

| Feature | SQL Database | SQL Managed Instance |
|---------|-------------|---------------------|
| SQL Agent jobs | No (use Elastic Jobs) | Yes |
| CLR integration | No | Yes |
| Service Broker | No | Yes (within instance) |
| Cross-database queries | No (elastic query limited) | Yes |
| VNet integration | Private endpoint | Native VNet deployment |
| Linked servers | No | Yes |
| SSIS | No (use Data Factory) | No (use Data Factory) |
| Migration from on-prem | Partial compatibility | Near-seamless |

---

## 2. Service Tiers and Compute Models

### Purchasing Models

| Model | Best For | How It Works |
|-------|----------|-------------|
| **DTU** (Database Transaction Unit) | Simple, predictable workloads | Bundled CPU + memory + IO |
| **vCore** | Fine-grained control, hybrid benefit | Choose CPU cores and storage independently |

**Exam Rule:** vCore is recommended for most production scenarios. DTU is simpler but inflexible.

### vCore Service Tiers

| Tier | Use Case | Key Features | SLA |
|------|----------|-------------|-----|
| **General Purpose** | Most workloads | Remote storage, zone redundant option | 99.99% |
| **Business Critical** | Low latency, HA | Local SSD, built-in read replica, zone redundant | 99.99% |
| **Hyperscale** | Very large databases (up to 100 TB) | Rapid scale-out, instant backups, up to 4 read replicas | 99.99% |

### Compute Tiers (SQL Database)

| Tier | Best For | Key Feature |
|------|----------|-------------|
| **Provisioned** | Predictable workloads | Reserved compute, Azure Hybrid Benefit eligible |
| **Serverless** | Variable/intermittent workloads | Auto-pause (no cost when idle), auto-scale |

### Serverless Auto-Pause Decision

```
Is the database idle for extended periods?
  ├── YES ──> Serverless (auto-pause saves cost)
  └── NO
        Is workload predictable?
          ├── YES ──> Provisioned (reserved capacity discount)
          └── NO  ──> Serverless (auto-scale handles bursts)
```

**Exam Trap:** Serverless has a warm-up delay when resuming from pause. Do NOT recommend for latency-sensitive production apps.

---

## 3. Database Scalability

### Vertical Scaling (Scale Up)

| Approach | When | Impact |
|----------|------|--------|
| Change service tier | Need more IO or features | Brief connectivity interruption |
| Add vCores | CPU-bound workload | Usually online |
| Increase max storage | Running out of space | Online, no downtime |

### Horizontal Scaling Options

| Pattern | Service | Use Case |
|---------|---------|----------|
| **Elastic pools** | SQL Database | Multi-tenant SaaS (shared resources across databases) |
| **Read replicas** | SQL Database (Business Critical/Hyperscale) | Offload read-heavy reporting |
| **Sharding** | SQL Database (Elastic Database tools) | Very large datasets split across databases |
| **Hyperscale** | SQL Database Hyperscale | Large databases needing instant scale |
| **Geo-replication** | SQL Database | Cross-region read offload |

### Elastic Pools Deep Dive

```
Elastic Pool (200 vCores, 1 TB storage)
  ├── Database A: Peak usage 100 vCores (weekdays 9-5)
  ├── Database B: Peak usage 80 vCores (weekdays 6pm-midnight)
  ├── Database C: Peak usage 50 vCores (weekends)
  └── Database D: Minimal usage (dev/test)

Result: All databases share 200 vCores, peaks don't overlap = cost savings
```

**When to use elastic pools:**
- Multiple databases with variable, non-overlapping peak usage
- Multi-tenant applications (one DB per tenant)
- Cost savings when per-database provisioned cost would be higher

**When NOT to use elastic pools:**
- Single database with consistent, high utilization
- Databases that always peak simultaneously
- Databases needing different service tiers

---

## 4. Data Protection

### Encryption

| Layer | Feature | Default? |
|-------|---------|----------|
| **At rest** | Transparent Data Encryption (TDE) | Yes (service-managed key) |
| **At rest (custom)** | TDE with customer-managed key (BYOK) | Optional (Key Vault) |
| **In transit** | TLS 1.2+ | Yes, enforced |
| **In use** | Always Encrypted | Optional (client-side encryption) |

### Always Encrypted vs. Dynamic Data Masking

| Feature | Always Encrypted | Dynamic Data Masking |
|---------|-----------------|---------------------|
| **Protection level** | Data encrypted in DB, only client decrypts | Data visible to privileged users, masked for others |
| **Use case** | DBA should NOT see sensitive data (SSN, credit cards) | Non-privileged users see masked data |
| **Performance** | Client-side crypto overhead | No performance impact |
| **Exam keyword** | "Even DBAs cannot see data" | "Hide data from non-privileged users" |

### Row-Level Security

Controls which rows a user can access in a table:
```
CREATE SECURITY POLICY SalesFilter
  ADD FILTER PREDICATE dbo.fn_securitypredicate(SalesRepId)
  ON dbo.Sales
```

**Exam Keyword:** "Users should only see their own data" → Row-Level Security

### Backup and Recovery

| Feature | SQL Database | SQL MI |
|---------|-------------|--------|
| Automated backups | Yes (full weekly, diff 12-24hr, log 5-10min) | Yes |
| Point-in-time restore (PITR) | 1-35 days (default 7) | 1-35 days |
| Long-term retention (LTR) | Up to 10 years | Up to 10 years |
| Geo-restore | Yes (from GRS backup) | Yes |
| Backup redundancy | LRS, ZRS, GRS | LRS, ZRS, GRS |

---

## 5. Summary Decision Matrix

| Exam Scenario | Recommended Service / Feature |
|---------------|------------------------------|
| Cloud-native app, no legacy SQL features | Azure SQL Database |
| Lift-and-shift SQL Server with Agent jobs | SQL Managed Instance |
| Full OS control, third-party tools | SQL Server on Azure VM |
| Multi-tenant SaaS, variable workloads | Elastic pools |
| Intermittent, dev/test database | Serverless compute |
| Read-heavy reporting offload | Read replicas (Business Critical) |
| DBAs cannot see sensitive data | Always Encrypted |
| Non-privileged users see masked data | Dynamic Data Masking |
| Users see only their own rows | Row-Level Security |
| 7-year backup retention | Long-term retention (LTR) policy |

---

## Next Steps

- **Lab:** Deploy [sql-database-elastic-pool.bicep](../../infra/sql-database-elastic-pool.bicep)
- **Lab:** Deploy [sql-failover-group.bicep](../../infra/sql-failover-group.bicep)
- **Continue:** [Lesson 2 — Non-Relational Data](lesson-2-non-relational-data.md)

---

## References

- [Azure SQL Database Overview](https://learn.microsoft.com/azure/azure-sql/database/sql-database-paas-overview)
- [SQL Managed Instance Overview](https://learn.microsoft.com/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview)
- [vCore vs. DTU](https://learn.microsoft.com/azure/azure-sql/database/purchasing-models)
- [Elastic Pools](https://learn.microsoft.com/azure/azure-sql/database/elastic-pool-overview)
- [Always Encrypted](https://learn.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)
