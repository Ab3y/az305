# Module 3 Knowledge Check: Business Continuity & Disaster Recovery

**Target Score:** 80%+ before moving to Module 4

---

## Instructions

Choose the BEST answer for each scenario. Pay close attention to RTO, RPO, and cost requirements.

---

### Q1. RTO/RPO Requirements

A financial services company requires an RTO of 30 seconds and RPO of near zero for their web application and database. What architecture should you recommend?

- A. Azure Backup with geo-restore
- B. Azure Site Recovery with 5-minute RPO
- C. Active-active deployment across two regions with Cosmos DB multi-region writes
- D. Active-passive with SQL auto-failover groups

<details>
<summary>Show Answer</summary>

**Correct: C**

Active-active deployment with Cosmos DB multi-region writes provides near-zero RPO (synchronous within region) and near-instant failover (RTO ~seconds). Both regions serve traffic simultaneously.

- **A is wrong:** Backup + geo-restore has RTO of hours and RPO of up to 24 hours.
- **B is wrong:** ASR provides 5-minute RPO and RTO of minutes — doesn't meet 30-second RTO.
- **D is wrong:** Auto-failover groups have ~30-second RTO but this is active-passive, not the lowest RTO option. However, the 30-second RTO requirement combined with near-zero RPO points to active-active as the best solution.
</details>

---

### Q2. Azure Backup

A company needs to back up Azure VMs and SQL Server databases running on Azure VMs. They need 7-year retention for compliance and the ability to restore in a different region if the primary region fails. What should you configure?

- A. Recovery Services Vault with GRS and long-term retention policy
- B. Backup Vault with LRS
- C. Azure Site Recovery with 7-year retention
- D. Storage account with blob versioning

<details>
<summary>Show Answer</summary>

**Correct: A**

Recovery Services Vault supports both Azure VMs and SQL in VMs. GRS provides cross-region restore capability. Long-term retention policies support up to 10 years.

- **B is wrong:** Backup Vault supports blobs and disks, not VMs or SQL. LRS doesn't enable cross-region restore.
- **C is wrong:** ASR is for disaster recovery (replication), not long-term backup retention.
- **D is wrong:** Blob versioning is for blob data, not VM or SQL backups, and doesn't provide structured backup management.
</details>

---

### Q3. Azure Site Recovery

A company runs a 3-tier application on Azure VMs. They need to ensure the VMs start in the correct order during DR failover: database first, then application servers, then web servers. What ASR feature should you use?

- A. Replication policy with app-consistent snapshots
- B. Recovery plan with groups and sequenced actions
- C. Automation runbook triggered by Azure Monitor
- D. Availability set with fault domains

<details>
<summary>Show Answer</summary>

**Correct: B**

Recovery plans allow you to group VMs and define startup order. Group 1 (database), Group 2 (app tier), Group 3 (web tier) with pre/post scripts between groups.

- **A is wrong:** Replication policy controls RPO and snapshot frequency, not failover sequencing.
- **C is wrong:** Runbooks can be part of a recovery plan but don't define VM startup order by themselves.
- **D is wrong:** Availability sets provide rack-level redundancy, not DR failover sequencing.
</details>

---

### Q4. Composite SLA

An application uses App Service (99.95% SLA), Azure SQL (99.99% SLA), and Azure Cache for Redis Standard (99.9% SLA) in a chain. What is the composite SLA?

- A. 99.99%
- B. 99.95%
- C. 99.84%
- D. 99.9%

<details>
<summary>Show Answer</summary>

**Correct: C**

Composite SLA = 0.9995 × 0.9999 × 0.999 = 0.99840 = **99.84%**

For chained services, multiply individual SLAs. The result is always lower than the lowest individual SLA.

- **A is wrong:** You can't exceed the lowest individual SLA (99.9%) without redundancy.
- **B is wrong:** That's just the App Service SLA — you must account for all dependencies.
- **D is wrong:** That's just the Redis SLA.
</details>

---

### Q5. Availability Zones

A company is deploying a new production application and needs the highest availability within a single region. The application uses VMs and requires a 99.99% SLA. What deployment model should you recommend?

- A. Single VM with Premium SSD
- B. VMs in an Availability Set
- C. VMs across Availability Zones
- D. VMs in a Virtual Machine Scale Set (single zone)

<details>
<summary>Show Answer</summary>

**Correct: C**

Availability Zones provide 99.99% SLA by distributing VMs across physically separate datacenters within a region.

- **A is wrong:** Single VM with Premium SSD provides only 99.9% SLA.
- **B is wrong:** Availability Sets provide 99.95% SLA (rack-level, not datacenter-level).
- **D is wrong:** VMSS in a single zone doesn't protect against datacenter failure.
</details>

---

### Q6. SQL Database DR

A company has an Azure SQL Database that serves users in East US and West Europe. They need automatic failover if East US goes down, with a single connection endpoint that doesn't change after failover. What should you recommend?

- A. Active geo-replication
- B. Auto-failover groups
- C. Point-in-time restore
- D. Geo-restore from GRS backup

<details>
<summary>Show Answer</summary>

**Correct: B**

Auto-failover groups provide automatic failover with a stable DNS endpoint (e.g., `myserver-group.database.windows.net`) that doesn't change after failover. Applications don't need connection string changes.

- **A is wrong:** Active geo-replication provides readable replicas but requires manual failover and connection string changes.
- **C is wrong:** PITR restores to a point in time, doesn't provide automatic cross-region failover.
- **D is wrong:** Geo-restore creates a new database from GRS backup — slow (hours) and requires connection string changes.
</details>

---

### Q7. Storage Redundancy for HA

An application reads blobs from Azure Storage. During a regional outage, the application must continue reading blobs without waiting for Microsoft to initiate a failover. What redundancy should you recommend?

- A. GRS
- B. ZRS
- C. RA-GRS
- D. LRS

<details>
<summary>Show Answer</summary>

**Correct: C**

RA-GRS (Read-Access Geo-Redundant Storage) provides a secondary read endpoint that is accessible even during a primary region outage. The application can read from `*.secondary.blob.core.windows.net` immediately.

- **A is wrong:** GRS replicates to a paired region, but data is not accessible until Microsoft or customer initiates failover.
- **B is wrong:** ZRS protects against zone failure, not regional failure.
- **D is wrong:** LRS provides no cross-region protection.
</details>

---

### Q8. Ransomware Protection

A company experienced a ransomware attack that encrypted their files and attempted to delete their Azure Backups. What features should you enable to protect backup data from deletion? (Choose the best combination)

- A. Soft delete + Immutable vault + Multi-user authorization
- B. Geo-redundant storage only
- C. Azure Site Recovery with daily snapshots
- D. Storage account firewall rules

<details>
<summary>Show Answer</summary>

**Correct: A**

This combination provides defense-in-depth for backup data:
- **Soft delete:** Retains deleted backup data for 14+ days
- **Immutable vault:** Prevents disabling backup or reducing retention periods
- **Multi-user authorization (Resource Guard):** Requires additional approval for destructive operations

- **B is wrong:** GRS replicates backups across regions but doesn't prevent deletion.
- **C is wrong:** ASR is for VM replication, not backup protection.
- **D is wrong:** Firewall rules control network access but don't prevent authorized users from deleting backups.
</details>

---

### Q9. Multi-Region Architecture

A company wants to deploy their web application across two Azure regions. They want traffic routed to the closest region and must have WAF protection and built-in CDN capabilities. What should you use as the global load balancer?

- A. Azure Traffic Manager
- B. Azure Front Door
- C. Azure Load Balancer (Standard)
- D. Azure Application Gateway

<details>
<summary>Show Answer</summary>

**Correct: B**

Azure Front Door provides global HTTP/HTTPS load balancing with built-in CDN, WAF, and proximity-based routing. It operates at Layer 7 with edge POP locations worldwide.

- **A is wrong:** Traffic Manager does DNS-based routing but has no WAF or CDN capabilities.
- **C is wrong:** Load Balancer is regional (Layer 4), not global.
- **D is wrong:** Application Gateway is regional (Layer 7), not global.
</details>

---

### Q10. Cosmos DB HA

A global e-commerce platform needs the highest possible availability SLA from Cosmos DB while serving both reads and writes from multiple regions. What should you configure?

- A. Single-region Cosmos DB with automatic failover
- B. Multi-region read replicas (single-write region)
- C. Multi-region writes with availability zones enabled
- D. Serverless Cosmos DB with geo-replication

<details>
<summary>Show Answer</summary>

**Correct: C**

Multi-region writes with availability zones provides the highest Cosmos DB SLA (99.999% for both reads and writes). Each region can accept writes, and zones protect against datacenter failure.

- **A is wrong:** Single region provides 99.99% SLA, lower than multi-region write (99.999%).
- **B is wrong:** Multi-region read gives 99.999% read SLA but only 99.99% write SLA (single write region).
- **D is wrong:** Serverless mode doesn't support multi-region writes or geo-replication.
</details>

---

## Scoring

| Score | Next Step |
|-------|----------|
| 9-10 / 10 (90-100%) | Excellent! Move to Module 4 |
| 8 / 10 (80%) | Good. Review missed questions, then move to Module 4 |
| 6-7 / 10 (60-70%) | Review the relevant lessons before proceeding |
| Below 6 / 10 (<60%) | Re-study the full module before retaking |

---

## Continue Learning

- **MS Learn Path:** [Design business continuity solutions](https://learn.microsoft.com/training/paths/design-business-continuity-solutions/)
  - [Describe high availability and disaster recovery strategies](https://learn.microsoft.com/training/modules/describe-high-availability-disaster-recovery-strategies/)
  - [Design a solution for backup and disaster recovery](https://learn.microsoft.com/training/modules/design-solution-for-backup-disaster-recovery/)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Next:** [Module 4 — Infrastructure & Compute](../module-4-compute-apps/overview.md)
