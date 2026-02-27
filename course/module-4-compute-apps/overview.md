# Module 4: Infrastructure & Compute Solutions

**Estimated Duration:** 4-5 hours | **Exam Weight:** 30-35%

---

## Module Overview

Design compute, application architecture, and migration solutions. This is the **heaviest-weighted domain** on the AZ-305 exam.

---

## Domain Objectives Covered

| # | Objective |
|---|-----------|
| 4.1 | Design a compute solution |
| 4.2 | Design an application architecture |
| 4.3 | Design migrations |

---

## Lessons

| # | Lesson | Duration | Focus |
|---|--------|----------|-------|
| 1 | [Compute Solutions](lesson-1-compute.md) | 60 min | VMs, Container Apps, AKS, Functions, App Service |
| 2 | [Application Architecture](lesson-2-app-architecture.md) | 60 min | Messaging, caching, APIM, App Config, microservices |
| 3 | [Migrations](lesson-3-migrations.md) | 45 min | Cloud Adoption Framework, migration tools, strategies |

---

## Key Concepts to Master

| Concept | Why It Matters |
|---------|---------------|
| **Compute decision tree** | Most common exam pattern — pick the right compute service |
| **Messaging services** | Service Bus vs. Event Grid vs. Event Hubs |
| **API Management** | Policies, tiers, security |
| **Migration strategies** | 5 Rs (Rehost, Refactor, Rearchitect, Rebuild, Replace) |
| **Landing zones** | CAF-aligned migration patterns |

---

## Hands-On Labs

| Lab | Template | Purpose |
|-----|----------|---------|
| Container Apps | [container-apps-environment.bicep](../../infra/container-apps-environment.bicep) | Serverless containers |
| AKS | [aks-cluster.bicep](../../infra/aks-cluster.bicep) | Managed Kubernetes |
| API Management | [apim-with-backends.bicep](../../infra/apim-with-backends.bicep) | API gateway with policies |

---

## Architecture Diagrams

- [Container Apps Microservices](../../images/container-apps-microservices.mmd)
- [API Architecture](../../images/api-architecture.mmd)
- [Migration Landing Zone](../../images/migration-landing-zone.mmd)

---

## Exam Tips

- This domain is 30-35% of the exam — invest the most study time here
- Compute selection questions often hinge on requirements like OS-level access, event-driven triggers, or container orchestration
- Messaging service selection: know the difference between commands (Service Bus) and events (Event Grid/Event Hubs)
- Migration questions test CAF phases and the 5 Rs — know when to choose each strategy
- API Management tier selection is common — focus on VNet integration (Developer/Premium) and consumption pricing

---

## Knowledge Check

Complete the [Module 4 Knowledge Check](knowledge-check.md) before moving on.

**Target:** 80%+ (8/10 correct)

---

## Official Microsoft Resources

### MS Learn Path
[AZ-305: Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/) (3 hr 39 min, 4 modules)
- [Design an Azure compute solution](https://learn.microsoft.com/training/modules/design-compute-solution/) (1 hr 1 min)
- [Design an application architecture](https://learn.microsoft.com/training/modules/design-application-architecture/) (59 min)
- [Design network solutions](https://learn.microsoft.com/training/modules/design-network-solutions/) (53 min) — also covered in Module 5
- [Design migrations](https://learn.microsoft.com/training/modules/design-migrations/) (46 min)

### Case Studies
Complete these scenario-based exercises from the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):
- [Design a compute solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/02-Compute.html)
- [Design an app architecture solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/05-Apparchitecture.html)

### Practice Assessment
[Take the free AZ-305 practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) — infrastructure questions make up 30-35% of the exam (heaviest weighted).
