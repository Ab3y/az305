# Lesson 2: High Availability

**Duration:** 60 minutes | **Domain Weight:** Part of 15-20%

---

## Learning Objectives

- Identify the SLA requirements for a solution
- Recommend a solution for compute, storage, and database high availability
- Recommend a solution for Azure availability zones and multi-region deployments
- Calculate composite SLAs

---

## 1. SLA Fundamentals

### Azure SLA Tiers

| SLA | Monthly Downtime | Annual Downtime | Achievable With |
|-----|-----------------|----------------|----------------|
| 99% | 7.31 hours | 3.65 days | Basic single instance |
| 99.9% | 43.8 minutes | 8.76 hours | Single instance with SSD |
| 99.95% | 21.9 minutes | 4.38 hours | Availability Set |
| 99.99% | 4.38 minutes | 52.6 minutes | Availability Zones |
| 99.999% | 26.3 seconds | 5.26 minutes | Multi-region active-active |

### Composite SLA Calculation

When services are **chained** (all must work): **multiply** SLAs.

```
Web App (99.95%) ──> SQL Database (99.99%) ──> Storage (99.9%)

Composite SLA = 0.9995 × 0.9999 × 0.999 = 0.9984 = 99.84%
```

When services are **redundant** (either can work): use complement formula.

```
Primary Web App (99.95%) OR Failover Web App (99.95%)

Probability both fail = (1 - 0.9995) × (1 - 0.9995) = 0.00000025
Composite SLA = 1 - 0.00000025 = 99.999975%
```

**Exam Trap:** Composite SLA is always **lower** than the lowest individual SLA for chained dependencies (unless you add redundancy).

---

## 2. Compute High Availability

### Availability Options

| Feature | What It Protects Against | SLA | Best For |
|---------|------------------------|-----|----------|
| **Single VM (Premium SSD)** | Hardware failure (limited) | 99.9% | Dev/test |
| **Availability Set** | Rack-level failure (FD+UD) | 99.95% | Legacy apps |
| **Availability Zones** | Datacenter failure | 99.99% | Production workloads |
| **VMSS across zones** | Datacenter failure + scaling | 99.99% | Auto-scaling workloads |
| **Multi-region** | Regional outage | ~99.99%+ | Mission-critical |

### Availability Sets Explained

```
Availability Set
  ├── Fault Domain 0 (Rack A)    ├── Fault Domain 1 (Rack B)    ├── Fault Domain 2 (Rack C)
  │     VM-1                      │     VM-2                      │     VM-3
  │     VM-4                      │     VM-5                      │     VM-6
  │                               │                               │
  Update Domain 0: VM-1, VM-5     Update Domain 1: VM-2, VM-6     Update Domain 2: VM-3, VM-4
```

| Component | Purpose | Max Count |
|-----------|---------|-----------|
| **Fault Domain (FD)** | Separate power/network rack | 3 (most regions) |
| **Update Domain (UD)** | Rolling update groups | 20 |

### Availability Zones Explained

```
Azure Region
  ├── Zone 1 (Datacenter A) ──> VM-1, SQL Primary, App Instance 1
  ├── Zone 2 (Datacenter B) ──> VM-2, SQL Secondary, App Instance 2
  └── Zone 3 (Datacenter C) ──> VM-3, Load Balancer, App Instance 3
```

**Exam Rule:** Availability Zones > Availability Sets for new deployments (99.99% vs. 99.95%).

### PaaS Compute HA

| Service | Zone-Redundant Option | Multi-Region Option |
|---------|----------------------|-------------------|
| App Service | Zone-redundant plan (Premium+ v3) | Traffic Manager / Front Door |
| Container Apps | Zone-redundant environment | Traffic Manager / Front Door |
| AKS | Zone-redundant node pools | Multi-cluster with Front Door |
| Azure Functions | Zone-redundant (Premium plan) | Traffic Manager / Front Door |

---

## 3. Database High Availability

### Azure SQL Database HA

| Tier | HA Model | RPO | Auto-Failover |
|------|----------|-----|--------------|
| **General Purpose** | Remote storage, zone-redundant option | ~10 sec failover | Within region |
| **Business Critical** | Always On AG (local replicas), zone-redundant | 0 (sync) | Within region |
| **Hyperscale** | Multi-replica, zone-redundant | 0 (sync) | Within region |

For **cross-region HA:**

| Feature | Same Region | Cross Region |
|---------|------------|-------------|
| Zone redundancy | Built-in HA | N/A |
| Active geo-replication | N/A | Manual failover |
| Auto-failover groups | N/A | Automatic DNS failover |

### Cosmos DB HA

| Configuration | SLA | Writes | Reads |
|--------------|-----|--------|-------|
| Single region | 99.99% | Single region | Single region |
| Multi-region read | 99.99% write, 99.999% read | Single region | All regions |
| Multi-region write | 99.999% | All regions | All regions |
| + Availability Zones | Further protection | Zone-redundant | Zone-redundant |

### Azure Cache for Redis HA

| Tier | HA | Cross-Region |
|------|----|-----------  |
| Basic | None | No |
| Standard | 2 replicas | No |
| Premium | Cluster + zonal | Geo-replication (active-passive) |
| Enterprise | Active-active geo-replication | Active-active across regions |

---

## 4. Storage High Availability

### Redundancy Revisited (HA Perspective)

| Scenario | Minimum Redundancy | Why |
|----------|-------------------|-----|
| Survive disk failure | LRS | 3 copies, same datacenter |
| Survive zone failure | ZRS | 3 copies across 3 zones |
| Survive regional failure | GRS/GZRS | Copies in paired region |
| Read during regional failure | RA-GRS/RA-GZRS | Read from secondary |

### Storage Failover

| Type | Initiated By | RPO | Considerations |
|------|-------------|-----|---------------|
| **Microsoft-managed** | Microsoft (major disaster) | Hours | Rare, last resort |
| **Customer-managed** | Customer | Data since last sync | Secondary becomes primary, may lose recent writes |

**Exam Trap:** After customer-managed failover, storage becomes LRS in the new primary region. You must re-configure geo-replication.

---

## 5. Network High Availability

### Load Balancer Options for HA

| Service | Scope | Layer | Best For |
|---------|-------|-------|----------|
| **Azure Load Balancer** | Regional | L4 (TCP/UDP) | VM/VMSS within region |
| **Application Gateway** | Regional | L7 (HTTP/HTTPS) | Web apps, WAF, SSL offload |
| **Traffic Manager** | Global | DNS-based | Multi-region failover |
| **Azure Front Door** | Global | L7 (HTTP/HTTPS) | Global web apps, CDN, WAF |
| **Cross-region Load Balancer** | Global | L4 | Multi-region L4 |

### Multi-Region Load Balancing Decision

```
Is it HTTP/HTTPS traffic?
  ├── YES ──> Azure Front Door (global L7, CDN, WAF)
  └── NO
        Is it DNS-based failover?
          ├── YES ──> Traffic Manager (any protocol)
          └── NO  ──> Cross-region Load Balancer (global L4)
```

---

## 6. Designing for Target SLA

### Step-by-Step Process

1. **Define business RTO/RPO** — What's acceptable?
2. **Calculate composite SLA** — Multiply chained service SLAs
3. **Identify the weakest link** — Which service drags the SLA down?
4. **Add redundancy** — Zones, replicas, or multi-region to strengthen weak links
5. **Recalculate** — Verify composite SLA meets requirement
6. **Test regularly** — DR drills, chaos engineering

### Example: Web App with SQL Backend

| Configuration | Composite SLA |
|---------------|-------------|
| App Service (99.95%) × SQL (99.99%) | 99.94% |
| + Zone-redundant App Service (99.99%) | 99.98% |
| + Multi-region with Front Door (99.99%) + failover | ~99.9999% |

---

## Summary Decision Matrix

| Requirement | Solution |
|-------------|---------|
| Protect against rack failure | Availability Set (99.95%) |
| Protect against datacenter failure | Availability Zones (99.99%) |
| Protect against regional outage | Multi-region deployment |
| SQL cross-region auto-failover | Auto-failover groups |
| Global HTTP load balancing + CDN | Azure Front Door |
| Global any-protocol failover | Traffic Manager |
| Storage read during regional outage | RA-GRS or RA-GZRS |
| Cosmos DB highest SLA | Multi-region writes + zones |
| Calculate composite SLA | Multiply chained, complement for redundant |

---

## Next Steps

- **Lab:** Deploy [sql-failover-group.bicep](../../infra/sql-failover-group.bicep)
- **Lab:** Review [high-availability-patterns.mmd](../../images/high-availability-patterns.mmd)
- **Knowledge Check:** [Module 3 Knowledge Check](knowledge-check.md)

---

## References

- [Azure SLA Summary](https://azure.microsoft.com/support/legal/sla/summary/)
- [Availability Zones](https://learn.microsoft.com/azure/reliability/availability-zones-overview)
- [Composite SLA](https://learn.microsoft.com/azure/architecture/framework/resiliency/business-metrics)
- [Front Door Overview](https://learn.microsoft.com/azure/frontdoor/front-door-overview)
