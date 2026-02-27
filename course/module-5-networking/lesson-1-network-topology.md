# Lesson 1: Network Topology & Connectivity

**Duration:** 60 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a network architecture (hub-spoke, Virtual WAN)
- Recommend a solution for network addressing and name resolution
- Recommend a solution for hybrid connectivity (VPN, ExpressRoute)

---

## 1. Virtual Network (VNet) Fundamentals

### Key Concepts

| Concept | Description |
|---------|-------------|
| **VNet** | Isolated network in Azure, regional scope |
| **Subnet** | Segment within a VNet, can have NSGs and route tables |
| **Address space** | CIDR block (e.g., 10.0.0.0/16) — plan for no overlap |
| **VNet peering** | Connects VNets (same or different region), non-transitive |
| **Service endpoints** | Route traffic to PaaS via Azure backbone |
| **Private endpoints** | Private IP in your VNet for PaaS services |

### Address Space Planning

```
Enterprise Address Plan (10.0.0.0/8)
  ├── Hub VNet: 10.1.0.0/16
  │     ├── GatewaySubnet: 10.1.0.0/24
  │     ├── AzureFirewallSubnet: 10.1.1.0/24
  │     ├── AzureBastionSubnet: 10.1.2.0/24
  │     └── SharedServicesSubnet: 10.1.3.0/24
  ├── Spoke 1 (Prod): 10.2.0.0/16
  │     ├── WebSubnet: 10.2.1.0/24
  │     ├── AppSubnet: 10.2.2.0/24
  │     └── DataSubnet: 10.2.3.0/24
  └── Spoke 2 (Dev): 10.3.0.0/16
        ├── WebSubnet: 10.3.1.0/24
        └── AppSubnet: 10.3.2.0/24
```

**Key Rules:**
- No overlapping address spaces between peered VNets
- `/24` minimum for most subnets (251 usable IPs)
- `/27` minimum for GatewaySubnet
- `/26` minimum for AzureBastionSubnet
- `/26` minimum for AzureFirewallSubnet

---

## 2. Hub-Spoke Topology

### Architecture

```
                    On-Premises
                        │
                  VPN / ExpressRoute
                        │
                 ┌──────┴──────┐
                 │   Hub VNet   │
                 │  ┌────────┐  │
                 │  │Firewall│  │
                 │  │Gateway │  │
                 │  │Bastion │  │
                 │  └────────┘  │
                 └──┬───┬───┬──┘
                    │   │   │
          ┌─────┐  │   │  ┌─────┐
          │Spoke│──┘   └──│Spoke│
          │ 1   │         │ 2   │
          │(Prod)│        │(Dev)│
          └─────┘         └─────┘
```

### Components

| Component | Location | Purpose |
|-----------|----------|---------|
| Azure Firewall | Hub | Centralized traffic filtering |
| VPN/ER Gateway | Hub | Hybrid connectivity |
| Azure Bastion | Hub | Secure VM access (no public IPs) |
| DNS | Hub | Centralized name resolution |
| Workloads | Spokes | Application VMs, PaaS services |

### Hub-Spoke Rules

| Rule | Details |
|------|---------|
| Peering is non-transitive | Spoke-to-spoke traffic must route through hub (firewall/NVA) |
| Use UDR for spoke-to-spoke | User-Defined Routes force traffic via hub firewall |
| Gateway transit | Spokes can use the hub's VPN/ER gateway |
| Spoke isolation | Each spoke is a separate security boundary |

---

## 3. Azure Virtual WAN

### When to Use Virtual WAN vs. Hub-Spoke

| Factor | Hub-Spoke (DIY) | Azure Virtual WAN |
|--------|-----------------|-------------------|
| Scale | Small-medium (< 30 VNets) | Large (30+ VNets, many branches) |
| Branch connectivity | Managed VPN/ER gateways | Automated branch-to-branch |
| Transitive routing | Requires UDR + NVA/Firewall | Built-in transit |
| Management | Customer managed | Microsoft managed |
| Cost | Lower (build your own) | Higher (managed service) |
| Exam keyword | "Small/medium enterprise" | "Large enterprise, many branches" |

### Virtual WAN Components

| Component | Purpose |
|-----------|---------|
| **Virtual WAN** | Parent resource |
| **Virtual Hub** | Managed hub VNet per region |
| **Connections** | VNet, VPN site, ExpressRoute, or P2S |
| **Routing** | Automatic route propagation between hubs |

### Virtual WAN Tiers

| Tier | Features |
|------|---------|
| **Basic** | S2S VPN only |
| **Standard** | S2S VPN, P2S VPN, ExpressRoute, inter-hub transit, Azure Firewall |

---

## 4. Hybrid Connectivity

### VPN Gateway

| Feature | Details |
|---------|---------|
| Protocol | IPSec/IKEv2 over public internet |
| Bandwidth | Up to 10 Gbps (VpnGw5) |
| Encryption | AES-256 |
| Use case | Branch offices, dev/test, backup connectivity |

| SKU | Max S2S | Max P2S | Max Bandwidth |
|-----|---------|---------|--------------|
| VpnGw1 | 30 | 250 | 650 Mbps |
| VpnGw2 | 30 | 500 | 1 Gbps |
| VpnGw3 | 30 | 1000 | 1.25 Gbps |
| VpnGw5 | 100 | 10000 | 10 Gbps |

### ExpressRoute

| Feature | Details |
|---------|---------|
| Protocol | Private connectivity via partner/direct peering |
| Bandwidth | 50 Mbps to 100 Gbps |
| Internet | Does NOT travel over public internet |
| Use case | Production, compliance, high bandwidth |

| SKU | Use Case |
|-----|----------|
| **Local** | Same metro as ER location, unlimited data |
| **Standard** | Same geopolitical region |
| **Premium** | Global reach (cross-region), Microsoft 365 |

### ExpressRoute vs. VPN Decision

```
Need private connectivity (not over internet)?
  ├── YES ──> ExpressRoute
  │            Need multi-region / global?
  │              ├── YES ──> ExpressRoute Premium + Global Reach
  │              └── NO  ──> ExpressRoute Standard or Local
  └── NO
        Need encrypted tunnel over internet?
          ├── YES ──> VPN Gateway
          │            Budget for redundancy?
          │              ├── YES ──> Active-Active VPN + ExpressRoute (backup)
          │              └── NO  ──> VPN Gateway standalone
          └── NO ──> Public connectivity (CDN, Front Door)
```

### Coexistence Pattern

```
On-Premises ──> ExpressRoute (primary, private) ──> Hub VNet
On-Premises ──> VPN Gateway (backup, encrypted) ──> Hub VNet
```

**Exam Tip:** ExpressRoute + VPN as backup is a common best-practice pattern.

---

## 5. DNS in Azure

### Azure DNS Options

| Option | Use Case |
|--------|----------|
| **Azure DNS (public zones)** | Host public domain DNS records |
| **Azure DNS (private zones)** | Name resolution for VNet resources |
| **Azure DNS Private Resolver** | Conditional forwarding between on-prem and Azure |

### Private DNS Zones

| Zone | Purpose |
|------|---------|
| `privatelink.blob.core.windows.net` | Private endpoints for Blob Storage |
| `privatelink.database.windows.net` | Private endpoints for Azure SQL |
| `privatelink.vaultcore.azure.net` | Private endpoints for Key Vault |
| Custom zones (e.g., `contoso.internal`) | Internal name resolution |

### DNS Resolution Flow (Hybrid)

```
On-premises DNS ──> Azure DNS Private Resolver (inbound endpoint)
                              │
                              v
                    Azure Private DNS Zone
                    (resolves privatelink.* names)

Azure VNet ──> Azure DNS Private Resolver (outbound endpoint)
                              │
                              v
                    On-premises DNS
                    (resolves on-prem names)
```

---

## 6. Summary Decision Matrix

| Scenario | Solution |
|----------|---------|
| Small-medium enterprise networking | Hub-spoke topology |
| Large enterprise, many branches | Azure Virtual WAN (Standard) |
| Private connectivity, not over internet | ExpressRoute |
| Encrypted tunnel over internet | VPN Gateway |
| Primary + backup connectivity | ExpressRoute + VPN coexistence |
| Cross-region ExpressRoute | ExpressRoute Premium + Global Reach |
| Resolve Azure private endpoints from on-prem | Azure DNS Private Resolver |
| Secure VM access without public IPs | Azure Bastion (in hub) |

---

## Next Steps

- **Lab:** Deploy [hub-spoke-network.bicep](../../infra/hub-spoke-network.bicep)
- **Diagram:** Review [hub-spoke-network.mmd](../../images/hub-spoke-network.mmd)
- **Continue:** [Lesson 2 — Network Security](lesson-2-network-security.md)

---

## References

- [Hub-Spoke Topology](https://learn.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
- [Virtual WAN Overview](https://learn.microsoft.com/azure/virtual-wan/virtual-wan-about)
- [ExpressRoute Overview](https://learn.microsoft.com/azure/expressroute/expressroute-introduction)
- [VPN Gateway Overview](https://learn.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)
- [Azure DNS Private Resolver](https://learn.microsoft.com/azure/dns/dns-private-resolver-overview)
