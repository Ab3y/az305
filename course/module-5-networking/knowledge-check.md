# Module 5 Knowledge Check: Network Solutions

**Target Score:** 80%+ to complete the course

---

## Instructions

Choose the BEST answer for each scenario. Network questions often combine topology, security, and load balancing requirements.

---

### Q1. Network Topology

A mid-sized company (10 VNets, 2 branch offices) needs a hub-spoke topology with centralized firewall, VPN gateway, and spoke isolation. Spokes should not communicate directly. What should you recommend?

- A. Azure Virtual WAN (Standard)
- B. Customer-managed hub-spoke with Azure Firewall and UDRs
- C. Full mesh VNet peering
- D. Azure Virtual WAN (Basic)

<details>
<summary>Show Answer</summary>

**Correct: B**

For small to medium deployments (< 30 VNets), a customer-managed hub-spoke is cost-effective and provides full control. Azure Firewall in the hub handles centralized filtering, and UDRs enforce spoke-to-hub routing. Spoke isolation is achieved by not peering spokes directly.

- **A is wrong:** Virtual WAN Standard works but is more expensive and complex than needed for 10 VNets.
- **C is wrong:** Full mesh peering allows direct spoke-to-spoke communication (violates isolation requirement) and doesn't scale.
- **D is wrong:** Virtual WAN Basic supports only S2S VPN, not ExpressRoute or transit routing.
</details>

---

### Q2. Hybrid Connectivity

A healthcare organization needs private connectivity from their on-premises datacenter to Azure. Traffic must NOT traverse the public internet. They need 2 Gbps bandwidth and connections to Azure services in their region. What should you recommend?

- A. VPN Gateway (VpnGw3)
- B. ExpressRoute (Standard)
- C. VPN Gateway with Azure Virtual WAN
- D. Azure Peering Service

<details>
<summary>Show Answer</summary>

**Correct: B**

ExpressRoute provides private connectivity that does NOT traverse the public internet. Standard SKU covers same geopolitical region. 2 Gbps circuits are available.

- **A is wrong:** VPN Gateway uses encrypted tunnels over the public internet — the requirement explicitly states "must NOT traverse the public internet."
- **C is wrong:** VPN through Virtual WAN still uses the internet.
- **D is wrong:** Peering Service improves internet routing to Microsoft services but still uses the internet path.
</details>

---

### Q3. Private Endpoints

A company uses Azure SQL Database and Azure Storage. They need to ensure these services are only accessible from within their VNet and from on-premises via ExpressRoute. They also need to prevent data exfiltration to other Azure SQL instances. What should you recommend?

- A. Service Endpoints on both services
- B. Private Endpoints for both services
- C. Azure Firewall with application rules
- D. NSG rules blocking internet traffic

<details>
<summary>Show Answer</summary>

**Correct: B**

Private Endpoints assign private IPs in the VNet, accessible via ExpressRoute from on-premises. They prevent data exfiltration because the endpoint points to a specific resource instance (not any SQL server). Service Endpoints don't prevent exfiltration and aren't accessible from on-premises.

- **A is wrong:** Service Endpoints don't prevent data exfiltration (can access any storage account in the service), and aren't accessible from on-premises.
- **C is wrong:** Azure Firewall controls traffic flow but doesn't give PaaS services private IPs for VNet/on-prem access.
- **D is wrong:** NSGs can't restrict traffic to specific PaaS resource instances.
</details>

---

### Q4. NSG vs. Firewall

A company needs to filter traffic at the subnet level within a spoke VNet. They need to allow HTTP traffic from web VMs to app VMs using logical groupings, without managing individual IP addresses. What should you use?

- A. Azure Firewall with network rules
- B. NSG with Application Security Groups (ASGs)
- C. Azure Firewall with application rules
- D. NSG with IP-based rules

<details>
<summary>Show Answer</summary>

**Correct: B**

NSGs with ASGs allow you to define rules using logical groups (WebASG → AppASG on port 80/443) without managing individual IP addresses. This is the simplest and most cost-effective solution for subnet-level filtering.

- **A is wrong:** Azure Firewall is centralized (hub-level), more expensive, and overkill for simple subnet-level rules.
- **C is wrong:** Same as A — application rules filter by FQDN, unnecessary for VM-to-VM traffic.
- **D is wrong:** IP-based NSG rules work but require manual IP management, violating the "without managing individual IPs" requirement.
</details>

---

### Q5. WAF Placement

A company runs a global e-commerce website across East US and West Europe. They need OWASP protection, CDN caching for static assets, and fast failover between regions. What should you recommend?

- A. Application Gateway WAF v2 in each region
- B. Azure Front Door Premium with WAF
- C. Traffic Manager with Application Gateway WAF in each region
- D. Azure CDN (Standard) with NSG rules

<details>
<summary>Show Answer</summary>

**Correct: B**

Azure Front Door Premium provides global L7 load balancing, built-in CDN, WAF with OWASP protection, and fast connection-level failover. Single service covers all three requirements.

- **A is wrong:** Application Gateway is regional. Two separate WAF instances don't provide global load balancing or CDN.
- **C is wrong:** Traffic Manager + App Gateway works but has slower DNS-based failover, no built-in CDN, and more complexity.
- **D is wrong:** Azure CDN doesn't provide WAF or intelligent routing. NSGs don't protect against OWASP attacks.
</details>

---

### Q6. Load Balancing

An application has a web tier (HTTP), an application tier (TCP port 8080), and a database tier. The web tier needs URL-based routing and SSL offload. The app tier just needs TCP load balancing. What combination should you use?

- A. Azure Front Door for web tier, Load Balancer for app tier
- B. Application Gateway for web tier, Internal Load Balancer for app tier
- C. Load Balancer for both tiers
- D. Application Gateway for both tiers

<details>
<summary>Show Answer</summary>

**Correct: B**

Application Gateway provides L7 features (URL routing, SSL offload) for the web tier. Internal Load Balancer efficiently handles TCP load balancing for the app tier. Right tool for each tier.

- **A is wrong:** Front Door is global — overkill for a single-region internal architecture.
- **C is wrong:** Load Balancer is L4 only — can't do URL-based routing or SSL offload.
- **D is wrong:** Application Gateway handles L7 HTTP/HTTPS only. TCP 8080 is better served by Load Balancer (simpler, lower latency).
</details>

---

### Q7. DDoS Protection

A company has 3 public IP addresses in Azure. They want DDoS mitigation beyond the default infrastructure protection. They want the most cost-effective option. What should you recommend?

- A. DDoS Network Protection
- B. DDoS IP Protection
- C. Azure Firewall Premium
- D. NSG rules to block suspicious IPs

<details>
<summary>Show Answer</summary>

**Correct: B**

DDoS IP Protection costs ~$199/month per IP (3 × $199 = $597/month). DDoS Network Protection costs ~$2,944/month regardless of IP count. For 3 IPs, IP Protection is significantly cheaper.

- **A is wrong:** Network Protection at $2,944/month is much more expensive for only 3 IPs. It becomes cost-effective at ~15+ IPs.
- **C is wrong:** Azure Firewall provides network filtering, not DDoS protection specifically.
- **D is wrong:** NSG rules can block known IPs but can't handle volumetric DDoS attacks dynamically.
</details>

---

### Q8. DNS Resolution

A company has a hub-spoke network with Private Endpoints for Azure SQL and Storage. On-premises servers connected via ExpressRoute need to resolve the `privatelink.*` DNS zones. What should you deploy?

- A. Custom DNS server in hub VNet
- B. Azure DNS Private Resolver with inbound endpoint
- C. Conditional forwarders on on-premises DNS only
- D. Public DNS zone with A records

<details>
<summary>Show Answer</summary>

**Correct: B**

Azure DNS Private Resolver with an inbound endpoint allows on-premises DNS servers to forward `privatelink.*` queries to Azure, which resolves them using the Private DNS zones linked to the VNet.

- **A is wrong:** Custom DNS VMs work but require managing OS, patching, and HA — Private Resolver is a managed service.
- **C is wrong:** On-prem conditional forwarders need something in Azure to forward TO — the Private Resolver's inbound endpoint serves as that target.
- **D is wrong:** Public DNS would expose private IP addresses publicly and bypass the purpose of Private Endpoints.
</details>

---

### Q9. Azure Bastion

A company's security policy requires that no VMs have public IP addresses. Administrators need to RDP into Windows VMs and SSH into Linux VMs from their laptops using native RDP/SSH clients (not just the Azure portal). What Bastion tier do you need?

- A. Basic
- B. Standard
- C. Premium
- D. Bastion is not needed — use JIT VM access

<details>
<summary>Show Answer</summary>

**Correct: B**

Standard tier supports native client connectivity (az network bastion rdp/ssh commands) in addition to portal access. Basic tier only supports portal-based RDP/SSH.

- **A is wrong:** Basic tier only supports browser-based access via Azure portal, not native RDP/SSH clients.
- **C is wrong:** Premium adds session recording but Standard is sufficient for native client support.
- **D is wrong:** JIT VM access temporarily opens NSG rules but still requires a public IP on the VM, violating the security policy.
</details>

---

### Q10. Multi-Region Architecture

A company deploys a non-HTTP application (custom TCP protocol) across East US and West Europe. They need automatic failover to the healthy region with the lowest latency. What global load balancing solution should they use?

- A. Azure Front Door
- B. Azure Traffic Manager with Performance routing
- C. Azure Application Gateway
- D. Azure Load Balancer (Standard)

<details>
<summary>Show Answer</summary>

**Correct: B**

Traffic Manager supports any protocol (including custom TCP) with DNS-based routing. Performance routing directs users to the lowest-latency endpoint. Health probes detect failures for failover.

- **A is wrong:** Front Door only supports HTTP/HTTPS, not custom TCP protocols.
- **C is wrong:** Application Gateway is regional, not global.
- **D is wrong:** Standard Load Balancer is regional. Cross-region LB exists but is simpler than needed; Traffic Manager with Performance routing is the standard recommendation.
</details>

---

## Scoring

| Score | Next Step |
|-------|----------|
| 9-10 / 10 (90-100%) | Excellent! Proceed to final exam prep |
| 8 / 10 (80%) | Good. Review missed areas, then do full practice exam |
| 6-7 / 10 (60-70%) | Review the relevant lessons before the practice exam |
| Below 6 / 10 (<60%) | Re-study the full module before retaking |

---

## Continue Learning

- **MS Learn Path:** [Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/) (network module)
- **Case Study:** [Design a network solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/08-Logging.html)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Final Step:** Take the [full practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15), review [practice questions](../../docs/practice-questions.md), then [schedule your exam](https://learn.microsoft.com/credentials/certifications/exams/az-305/).
