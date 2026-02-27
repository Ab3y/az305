# Lesson 3: Load Balancing

**Duration:** 45 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a load balancing solution
- Choose between regional and global load balancers
- Choose between Layer 4 and Layer 7 load balancers

---

## 1. Azure Load Balancing Services

### The Four Load Balancers

| Service | Scope | Layer | Protocol | Key Feature |
|---------|-------|-------|----------|-------------|
| **Azure Load Balancer** | Regional | L4 | TCP/UDP | Ultra-low latency, HA ports |
| **Application Gateway** | Regional | L7 | HTTP/HTTPS | URL routing, SSL offload, WAF |
| **Azure Front Door** | Global | L7 | HTTP/HTTPS | CDN, WAF, global distribution |
| **Traffic Manager** | Global | DNS | Any | DNS-based routing, any protocol |

### Decision Tree

```
Is the traffic HTTP/HTTPS?
  ├── YES
  │     Is it multi-region (global)?
  │       ├── YES ──> Azure Front Door
  │       └── NO  ──> Application Gateway
  └── NO
        Is it multi-region?
          ├── YES ──> Traffic Manager (DNS) or Cross-region LB
          └── NO  ──> Azure Load Balancer
```

---

## 2. Azure Load Balancer (L4)

### SKUs

| Feature | Basic | Standard |
|---------|-------|---------|
| SLA | None | 99.99% |
| Backend pool | Availability Set only | Any VMs in VNet |
| Health probes | TCP, HTTP | TCP, HTTP, HTTPS |
| HA Ports | No | Yes |
| Availability Zones | No | Zone-redundant |
| Outbound rules | No | Yes |
| **Exam:** | "Don't use for production" | **Default recommendation** |

### Key Concepts

| Concept | Description |
|---------|-------------|
| **Frontend IP** | Public or internal IP that receives traffic |
| **Backend pool** | VMs/VMSS that serve traffic |
| **Health probes** | TCP/HTTP checks to detect unhealthy instances |
| **Load balancing rules** | Map frontend port to backend port |
| **HA Ports** | Load balance ALL ports (useful for NVA/firewall) |
| **Outbound rules** | Control SNAT for outbound internet access |

### Internal vs. Public

| Type | Use Case |
|------|----------|
| **Public** | Internet-facing services |
| **Internal** | Internal services (app tier behind web tier) |

---

## 3. Application Gateway (L7)

### Key Features

| Feature | Description |
|---------|-------------|
| **URL-based routing** | Route `/api/*` to one pool, `/web/*` to another |
| **Multi-site hosting** | Route by host header (`app1.contoso.com`, `app2.contoso.com`) |
| **SSL termination** | Decrypt at gateway, re-encrypt or HTTP to backend |
| **SSL end-to-end** | Decrypt, inspect, re-encrypt to backend |
| **Cookie-based affinity** | Session stickiness |
| **Autoscaling** | Scale instances based on traffic (v2) |
| **WAF** | Built-in OWASP protection (v2) |
| **Zone redundancy** | Deploy across availability zones |

### Application Gateway SKUs

| SKU | Key Feature | Use Case |
|-----|-------------|----------|
| **Standard v2** | Autoscale, zone redundancy | Production web apps |
| **WAF v2** | Standard v2 + WAF | Web apps needing OWASP protection |

### Components

```
Client ──> Frontend IP ──> Listener (port/protocol/hostname)
                              │
                              v
                        Routing Rule
                              │
                    ┌─────────┴──────────┐
                    │                    │
              URL Path Map          Backend Settings
              (path-based)          (protocol, port, timeout)
                    │                    │
                    v                    v
              Backend Pool         Backend Pool
              (API servers)        (Web servers)
```

---

## 4. Azure Front Door (Global L7)

### Key Features

| Feature | Description |
|---------|-------------|
| **Global anycast** | Routes to nearest POP (250+ edge locations) |
| **CDN integration** | Built-in content caching at edge |
| **WAF** | Global WAF with custom rules and bot protection |
| **SSL offload** | Edge termination, managed certificates |
| **URL routing** | Path-based and host-based routing |
| **Session affinity** | Optional sticky sessions |
| **Health probes** | Active health monitoring of backends |
| **Traffic splitting** | Weighted routing for blue-green deployments |
| **Private Link origin** | Connect to private backends |

### Front Door Tiers

| Tier | Key Feature |
|------|-------------|
| **Standard** | CDN, basic routing, basic WAF |
| **Premium** | Standard + enhanced WAF, Private Link origins, bot protection |

### Front Door vs. Traffic Manager

| Factor | Front Door | Traffic Manager |
|--------|-----------|----------------|
| Layer | L7 (HTTP/HTTPS) | DNS (any protocol) |
| Failover speed | Fast (connection-level) | Slow (DNS TTL) |
| CDN | Built-in | No |
| WAF | Built-in | No |
| Non-HTTP protocols | No | Yes |
| SSL offload | Yes | No |
| Path-based routing | Yes | No |
| **Exam default for HTTP** | **Yes** | Non-HTTP only |

---

## 5. Traffic Manager (Global DNS)

### Routing Methods

| Method | How | Use Case |
|--------|-----|----------|
| **Priority** | Always route to primary; failover if unhealthy | Active-passive DR |
| **Weighted** | Distribute by percentage | Blue-green, canary |
| **Performance** | Route to lowest-latency endpoint | Global UX optimization |
| **Geographic** | Route by user's geographic location | Data sovereignty |
| **Multivalue** | Return multiple healthy endpoints | Client-side load balancing |
| **Subnet** | Route by client subnet | Enterprise routing policies |

### Traffic Manager Limitations

- DNS-based: failover depends on TTL (typically 30-60 seconds)
- No CDN, WAF, or SSL offload
- Works with any protocol (not just HTTP)

---

## 6. Combined Patterns

### Global + Regional

```
Internet ──> Azure Front Door (global L7, CDN, WAF)
                    │                    │
                    v                    v
           Region: East US        Region: West Europe
           App Gateway (WAF)      App Gateway (WAF)
                    │                    │
                    v                    v
              Load Balancer         Load Balancer
              (VM backend)         (VM backend)
```

### Multi-Tier Internal

```
Internet ──> App Gateway (public, WAF) ──> Web VMs (subnet)
                                              │
                                     Internal LB
                                              │
                                         App VMs (subnet)
                                              │
                                     Internal LB
                                              │
                                         DB VMs (subnet)
```

---

## 7. Summary Decision Matrix

| Scenario | Service |
|----------|---------|
| Internal VM load balancing (TCP/UDP) | Azure Load Balancer (Standard, internal) |
| Internet-facing VM load balancing | Azure Load Balancer (Standard, public) |
| Web app with URL routing and WAF (single region) | Application Gateway WAF v2 |
| Global web app with CDN and WAF | Azure Front Door (Premium) |
| Multi-region failover (any protocol) | Traffic Manager |
| Multi-region HTTP with fast failover | Azure Front Door |
| NVA/firewall load balancing (all ports) | Load Balancer with HA Ports |
| Blue-green deployment (HTTP) | Front Door (weighted) or App Gateway (traffic splitting) |
| DNS-based geographic routing | Traffic Manager (geographic) |
| Global + regional combined | Front Door → App Gateway → Load Balancer |

---

## Next Steps

- **Lab:** Deploy [front-door-global.bicep](../../infra/front-door-global.bicep)
- **Lab:** Deploy [application-gateway-waf.bicep](../../infra/application-gateway-waf.bicep)
- **Knowledge Check:** [Module 5 Knowledge Check](knowledge-check.md)

---

## References

- [Load Balancing Decision Tree](https://learn.microsoft.com/azure/architecture/guide/technology-choices/load-balancing-overview)
- [Azure Load Balancer](https://learn.microsoft.com/azure/load-balancer/load-balancer-overview)
- [Application Gateway](https://learn.microsoft.com/azure/application-gateway/overview)
- [Azure Front Door](https://learn.microsoft.com/azure/frontdoor/front-door-overview)
- [Traffic Manager](https://learn.microsoft.com/azure/traffic-manager/traffic-manager-overview)
