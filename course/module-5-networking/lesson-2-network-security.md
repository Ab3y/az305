# Lesson 2: Network Security

**Duration:** 60 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a solution for network security (NSG, Azure Firewall, WAF)
- Recommend a solution for private connectivity to Azure PaaS services
- Recommend a solution for securing internet-facing applications

---

## 1. Network Security Layers

### Defense-in-Depth

```
Internet
  │
  ├── DDoS Protection ──────────────── Layer 1: Volumetric attack mitigation
  │
  ├── Azure Front Door / WAF ───────── Layer 2: L7 application protection
  │
  ├── Azure Firewall ───────────────── Layer 3: Centralized network filtering
  │
  ├── NSG (Network Security Group) ─── Layer 4: Subnet/NIC-level ACLs
  │
  ├── Private Endpoints ────────────── Layer 5: PaaS service isolation
  │
  └── Application-level security ──── Layer 6: Auth, encryption, RBAC
```

---

## 2. Network Security Groups (NSG)

### How NSGs Work

| Scope | Attachment | Effect |
|-------|-----------|--------|
| **Subnet** | Applied to all resources in subnet | Default for most scenarios |
| **NIC** | Applied to specific VM NIC | Fine-grained per-VM rules |
| **Both** | Subnet + NIC | Most restrictive combination wins |

### Default Rules

| Priority | Direction | Action | Traffic |
|----------|-----------|--------|---------|
| 65000 | Inbound | Allow | VNet-to-VNet |
| 65001 | Inbound | Allow | Azure Load Balancer probes |
| 65500 | Inbound | Deny | All other inbound |
| 65000 | Outbound | Allow | VNet-to-VNet |
| 65001 | Outbound | Allow | Internet outbound |
| 65500 | Outbound | Deny | All other outbound |

### NSG Best Practices for Exam

| Practice | Why |
|----------|-----|
| Apply at subnet level (not NIC) | Simpler management, consistent rules |
| Use Application Security Groups (ASG) | Group VMs by role (web, app, data) |
| Deny internet inbound by default | Only open what's needed |
| Use service tags | `AzureCloud`, `Storage`, `Sql` instead of IPs |

### Application Security Groups (ASG)

```
NSG Rule: Allow HTTP from WebASG to AppASG on port 443
  ├── WebASG: [WebVM-1, WebVM-2, WebVM-3]
  └── AppASG: [AppVM-1, AppVM-2]
```

No need to manage individual IP addresses — ASGs group VMs logically.

---

## 3. Azure Firewall

### NSG vs. Azure Firewall

| Feature | NSG | Azure Firewall |
|---------|-----|---------------|
| Scope | Subnet or NIC | VNet or cross-VNet (hub) |
| Layer | L3/L4 (IP, port) | L3/L4/L7 (FQDN, URL, TLS) |
| FQDN filtering | No | Yes (`*.microsoft.com`) |
| Threat intelligence | No | Yes (block known malicious IPs) |
| TLS inspection | No | Yes (Premium) |
| Cost | Free | Significant (per hour + per GB) |
| Exam keyword | "Subnet-level filtering" | "Centralized, FQDN, threat intelligence" |

### Azure Firewall Tiers

| Tier | Key Features |
|------|-------------|
| **Standard** | L3/L4/L7 filtering, FQDN, threat intel, NAT rules |
| **Premium** | Standard + TLS inspection, IDPS, URL filtering, web categories |
| **Basic** | Limited features, lower cost, small environments |

### Azure Firewall Policy

```
Firewall Policy (parent)
  ├── Rule Collection Group: "NetworkRules" (Priority: 100)
  │     ├── Rule: Allow DNS (UDP 53)
  │     └── Rule: Allow NTP (UDP 123)
  ├── Rule Collection Group: "ApplicationRules" (Priority: 200)
  │     ├── Rule: Allow *.microsoft.com (HTTPS)
  │     └── Rule: Allow *.ubuntu.com (HTTP)
  └── Rule Collection Group: "NAT" (Priority: 300)
        └── Rule: DNAT port 443 to internal web server
```

### Firewall Placement (Hub-Spoke)

```
All spoke traffic ──> UDR (0.0.0.0/0 → Firewall) ──> Azure Firewall (hub) ──> Internet
Spoke-to-spoke ──> UDR ──> Azure Firewall (hub) ──> UDR ──> Target spoke
```

---

## 4. Private Endpoints vs. Service Endpoints

### Comparison

| Feature | Service Endpoint | Private Endpoint |
|---------|-----------------|-----------------|
| Network path | Azure backbone (optimized route) | Private IP in your VNet |
| Source IP (PaaS sees) | VNet subnet IP | Private endpoint IP |
| Data exfiltration risk | Can access any instance of the service | Only your specific resource |
| DNS | Public DNS (no change) | Requires Private DNS zone |
| Cost | Free | Per-hour + per-GB |
| On-prem access | No (VNet only) | Yes (via VPN/ER + DNS) |
| Exam preference | Budget-sensitive, simple | **Default recommendation** |

### Private Endpoint Architecture

```
VNet (10.1.0.0/16)
  └── Subnet (10.1.1.0/24)
        └── Private Endpoint (10.1.1.5)
              │
              └── Connected to: My SQL Server (mydb.database.windows.net)
                    └── Private DNS Zone: privatelink.database.windows.net
                          └── A record: mydb → 10.1.1.5
```

### When to Use Which

| Scenario | Solution |
|----------|---------|
| Block access from internet, PaaS in VNet | Private Endpoint |
| Access PaaS from on-premises via VPN/ER | Private Endpoint |
| Prevent data exfiltration to other storage accounts | Private Endpoint |
| Quick, free optimization of traffic path | Service Endpoint |
| Exam default recommendation | **Private Endpoint** |

---

## 5. Web Application Firewall (WAF)

### Where WAF Can Run

| Service | WAF | Use Case |
|---------|-----|----------|
| **Application Gateway** | WAF v2 | Regional web apps |
| **Azure Front Door** | WAF | Global web apps |
| **Azure CDN (from Microsoft)** | WAF | CDN edge protection |

### WAF Features

| Feature | Description |
|---------|-------------|
| OWASP rule sets | Protect against SQL injection, XSS, etc. |
| Custom rules | IP-based, geo-based, rate-limiting |
| Bot protection | Block/allow known bot categories |
| Modes | Detection (log only) or Prevention (block) |
| Per-site policies | Different WAF policies per listener/route |

### WAF Decision

```
Need WAF for web applications?
  ├── Global (multi-region)? ──> Azure Front Door WAF
  └── Regional (single region)? ──> Application Gateway WAF v2
```

---

## 6. DDoS Protection

### Tiers

| Feature | DDoS Network Protection | DDoS IP Protection |
|---------|------------------------|-------------------|
| Scope | VNet (all public IPs) | Per public IP |
| Cost | ~$2,944/month + overage | ~$199/month per IP |
| Added features | Cost protection, rapid response, diagnostics | Basic diagnostics |
| Best for | Enterprise with many public IPs | Few public IPs |

### Always-On Protection

Azure **DDoS Infrastructure Protection** (free, default) protects against common network-layer attacks. DDoS Protection plans add:
- Adaptive tuning for your traffic profiles
- Attack analytics and alerting
- Cost protection (credit for scale-out during attack)
- DDoS Rapid Response team access

---

## 7. Azure Bastion

Secure RDP/SSH access to VMs without public IP addresses.

| Tier | Features |
|------|---------|
| **Basic** | RDP/SSH via portal |
| **Standard** | + Native client, IP-based, shareable link, scaling |
| **Premium** | + Session recording |

### Bastion vs. Alternatives

| Access Method | Security | Exam Keyword |
|---------------|----------|-------------|
| Public IP + NSG | Exposed to internet | "Legacy, not recommended" |
| JIT VM Access (Defender) | Temporary NSG rule | "Time-limited access" |
| Azure Bastion | No public IP needed | "Secure VM access" |
| VPN + private IP | Requires VPN client | "Existing VPN infrastructure" |

---

## 8. Summary Decision Matrix

| Scenario | Solution |
|----------|---------|
| Subnet/NIC traffic filtering | NSG |
| Group VMs by role for rules | Application Security Groups (ASG) |
| Centralized FQDN filtering, threat intel | Azure Firewall (Standard) |
| TLS inspection, IDPS | Azure Firewall (Premium) |
| PaaS private access, prevent exfiltration | Private Endpoint |
| Quick traffic optimization, budget | Service Endpoint |
| Protect web apps from OWASP attacks | WAF (App Gateway or Front Door) |
| Volumetric DDoS protection | DDoS Protection plan |
| Secure VM access, no public IPs | Azure Bastion |

---

## Next Steps

- **Lab:** Deploy [private-endpoint-services.bicep](../../infra/private-endpoint-services.bicep)
- **Lab:** Deploy [application-gateway-waf.bicep](../../infra/application-gateway-waf.bicep)
- **Diagram:** Review [private-link-topology.mmd](../../images/private-link-topology.mmd)
- **Continue:** [Lesson 3 — Load Balancing](lesson-3-load-balancing.md)

---

## References

- [NSG Overview](https://learn.microsoft.com/azure/virtual-network/network-security-groups-overview)
- [Azure Firewall Overview](https://learn.microsoft.com/azure/firewall/overview)
- [Private Link / Private Endpoints](https://learn.microsoft.com/azure/private-link/private-link-overview)
- [WAF on Application Gateway](https://learn.microsoft.com/azure/web-application-firewall/ag/ag-overview)
- [DDoS Protection Overview](https://learn.microsoft.com/azure/ddos-protection/ddos-protection-overview)
