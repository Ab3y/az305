# Module 3: Business Continuity & Disaster Recovery

**Estimated Duration:** 3-4 hours | **Exam Weight:** 15-20%

---

## Module Overview

Design solutions for backup, disaster recovery, and high availability that meet defined Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO).

---

## Domain Objectives Covered

| # | Objective |
|---|-----------|
| 3.1 | Design a solution for backup and disaster recovery |
| 3.2 | Design for high availability |

---

## Lessons

| # | Lesson | Duration | Focus |
|---|--------|----------|-------|
| 1 | [Backup & Disaster Recovery](lesson-1-backup-dr.md) | 60 min | Azure Backup, ASR, RTO/RPO, geo-redundancy |
| 2 | [High Availability](lesson-2-high-availability.md) | 60 min | Availability zones, database HA, storage redundancy, SLAs |

---

## Key Concepts to Master

| Concept | Why It Matters |
|---------|---------------|
| **RTO** (Recovery Time Objective) | Maximum acceptable downtime |
| **RPO** (Recovery Point Objective) | Maximum acceptable data loss |
| **Composite SLA** | Calculate multi-service SLA |
| **Availability Zones** | Physical datacenter isolation |
| **Active-Active vs. Active-Passive** | Architecture pattern trade-offs |

---

## Hands-On Labs

| Lab | Template | Purpose |
|-----|----------|---------|
| Recovery Services Vault | [recovery-services-vault.bicep](../../infra/recovery-services-vault.bicep) | Azure Backup vault with policies |
| Site Recovery | [site-recovery-config.bicep](../../infra/site-recovery-config.bicep) | ASR replication configuration |
| SQL Failover Group | [sql-failover-group.bicep](../../infra/sql-failover-group.bicep) | Auto-failover for Azure SQL |

---

## Architecture Diagrams

- [High Availability Patterns](../../images/high-availability-patterns.mmd)
- [Site Recovery DR](../../images/site-recovery-dr.mmd)
- [SQL HA/DR](../../images/sql-ha-dr.mmd)
- [Backup Architecture](../../images/backup-architecture.mmd)

---

## Exam Tips

- Questions often give you RTO/RPO numbers and ask you to select the cheapest/simplest solution that meets them
- Know the difference between Azure Backup and Azure Site Recovery
- Composite SLA calculation appears frequently — multiply individual SLAs
- Availability Zones provide 99.99% SLA vs. Availability Sets at 99.95%
- Database HA options vary by service (SQL auto-failover groups, Cosmos DB multi-region)

---

## Knowledge Check

Complete the [Module 3 Knowledge Check](knowledge-check.md) before moving on.

**Target:** 80%+ (8/10 correct)

---

## Official Microsoft Resources

### MS Learn Path
[AZ-305: Design business continuity solutions](https://learn.microsoft.com/training/paths/design-business-continuity-solutions/) (1 hr 46 min, 2 modules)
- [Describe high availability and disaster recovery strategies](https://learn.microsoft.com/training/modules/describe-high-availability-disaster-recovery-strategies/) (59 min)
- [Design a solution for backup and disaster recovery](https://learn.microsoft.com/training/modules/design-solution-for-backup-disaster-recovery/) (47 min)

### Case Studies
There is no formal case study for business continuity in the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/). Use the Bicep labs above and practice assessment to reinforce this domain.

### Practice Assessment
[Take the free AZ-305 practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) — business continuity questions make up 15-20% of the exam.
