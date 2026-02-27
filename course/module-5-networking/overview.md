# Module 5: Network Solutions

**Estimated Duration:** 3-4 hours | **Exam Weight:** Part of 30-35% (Infrastructure)

---

## Module Overview

Design network topologies, connectivity, security, and load balancing solutions for Azure infrastructure.

---

## Domain Objectives Covered

| # | Objective |
|---|-----------|
| 5.1 | Design a network architecture |
| 5.2 | Design for network security and connectivity |

---

## Lessons

| # | Lesson | Duration | Focus |
|---|--------|----------|-------|
| 1 | [Network Topology & Connectivity](lesson-1-network-topology.md) | 60 min | VNet design, hub-spoke, Virtual WAN, hybrid connectivity |
| 2 | [Network Security](lesson-2-network-security.md) | 60 min | NSG, Firewall, WAF, Private Link, DDoS Protection |
| 3 | [Load Balancing](lesson-3-load-balancing.md) | 45 min | Load Balancer, App Gateway, Front Door, Traffic Manager |

---

## Key Concepts to Master

| Concept | Why It Matters |
|---------|---------------|
| **Hub-spoke vs. Virtual WAN** | Most common topology question |
| **Private Link vs. Service Endpoints** | Critical security decision |
| **NSG vs. Azure Firewall** | Different scopes of protection |
| **Load balancer selection** | L4 vs. L7, regional vs. global |
| **ExpressRoute vs. VPN** | Hybrid connectivity options |

---

## Hands-On Labs

| Lab | Template | Purpose |
|-----|----------|---------|
| Hub-Spoke Network | [hub-spoke-network.bicep](../../infra/hub-spoke-network.bicep) | VNet peering with hub topology |
| Application Gateway WAF | [application-gateway-waf.bicep](../../infra/application-gateway-waf.bicep) | L7 load balancer with WAF |
| Front Door | [front-door-global.bicep](../../infra/front-door-global.bicep) | Global load balancing with CDN |
| Private Endpoints | [private-endpoint-services.bicep](../../infra/private-endpoint-services.bicep) | Private access to PaaS services |

---

## Architecture Diagrams

- [Hub-Spoke Network](../../images/hub-spoke-network.mmd)
- [Private Link Topology](../../images/private-link-topology.mmd)

---

## Exam Tips

- Network questions often combine security + topology requirements
- Private Link is preferred over Service Endpoints for data exfiltration protection
- Azure Firewall is centralized (hub-level), NSG is per-subnet/NIC
- Know the 4 Azure load balancing services and when to use each
- ExpressRoute provides private connectivity (not internet), VPN uses encrypted internet tunnel

---

## Knowledge Check

Complete the [Module 5 Knowledge Check](knowledge-check.md) before the final review.

**Target:** 80%+ (8/10 correct)

---

## Official Microsoft Resources

### MS Learn Path
Networking is covered within [AZ-305: Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/) (3 hr 39 min)
- [Design network solutions](https://learn.microsoft.com/training/modules/design-network-solutions/) (53 min)

### Case Studies
Complete this scenario-based exercise from the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):
- [Design a network solution — BI enterprise application](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/08-Logging.html)

### Practice Assessment
[Take the free AZ-305 practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) after completing all 5 modules.
