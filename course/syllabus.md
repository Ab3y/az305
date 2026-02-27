# AZ-305 Self-Paced Training Course

**Designing Microsoft Azure Infrastructure Solutions**

---

## Course Overview

| Attribute | Details |
|-----------|---------|
| **Certification** | Microsoft Certified: Azure Solutions Architect Expert |
| **Exam Code** | AZ-305 |
| **Passing Score** | 700 / 1000 |
| **Duration** | 120 minutes, 40-60 questions |
| **Prerequisite** | AZ-104 Azure Administrator Associate |
| **Format** | Multiple choice, case studies, drag-and-drop, build list |

This self-paced course is organized into **5 modules** aligned with the AZ-305 exam domains. Each module contains lessons, knowledge checks, hands-on labs, and exam tips.

---

## Exam Domain Weights

| # | Domain | Weight | Module |
|---|--------|--------|--------|
| 1 | Identity, Governance & Monitoring | 25-30% | [Module 1](module-1-identity-governance/overview.md) |
| 2 | Data Storage Solutions | 20-25% | [Module 2](module-2-data-storage/overview.md) |
| 3 | Business Continuity Solutions | 15-20% | [Module 3](module-3-business-continuity/overview.md) |
| 4 | Infrastructure & Compute Solutions | 30-35% (part 1) | [Module 4](module-4-compute-apps/overview.md) |
| 5 | Networking & Migrations | 30-35% (part 2) | [Module 5](module-5-networking-migrations/overview.md) |

---

## Recommended Study Plan

### Week 1-2: Foundations (Module 1)
- [ ] Complete all 3 lessons in Module 1
- [ ] Deploy Log Analytics workspace lab
- [ ] Deploy custom RBAC role lab
- [ ] Deploy Key Vault with Private Link lab
- [ ] Score 80%+ on Module 1 knowledge check

### Week 3-4: Data (Module 2)
- [ ] Complete all 3 lessons in Module 2
- [ ] Deploy SQL elastic pool lab
- [ ] Deploy Cosmos DB multi-region lab
- [ ] Deploy storage account lifecycle lab
- [ ] Score 80%+ on Module 2 knowledge check

### Week 5-6: Resilience (Module 3)
- [ ] Complete all 2 lessons in Module 3
- [ ] Deploy Recovery Services Vault lab
- [ ] Deploy SQL failover group lab
- [ ] Score 80%+ on Module 3 knowledge check

### Week 7-8: Compute & Apps (Module 4)
- [ ] Complete all 3 lessons in Module 4
- [ ] Deploy Container Apps lab
- [ ] Deploy APIM lab
- [ ] Score 80%+ on Module 4 knowledge check

### Week 9-10: Networking & Review (Module 5)
- [ ] Complete all 3 lessons in Module 5
- [ ] Deploy hub-spoke network lab
- [ ] Deploy Application Gateway WAF lab
- [ ] Score 80%+ on Module 5 knowledge check
- [ ] Take Microsoft's free practice assessment

### Week 11-12: Final Prep
- [ ] Review all quick reference cards in [docs/quick-reference-cards.md](../docs/quick-reference-cards.md)
- [ ] Complete all 100+ practice questions in [docs/practice-questions.md](../docs/practice-questions.md)
- [ ] Re-do any labs where you scored below 80%
- [ ] Take the [official practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- [ ] Schedule your exam

---

## How to Use This Course

### Each Module Contains

| Component | Description |
|-----------|-------------|
| **README.md** | Module overview, learning objectives, key concepts |
| **Lessons** | Deep-dive content with architecture diagrams and decision matrices |
| **Knowledge Check** | 10-15 scenario-based questions per module with explanations |
| **Labs** | Hands-on exercises using Bicep templates from the `infra/` folder |

### Study Approach

1. **Read the lesson** — understand the "why" behind each design decision
2. **Study the diagrams** — architecture patterns appear frequently on the exam
3. **Do the lab** — deploy real resources to solidify understanding
4. **Take the knowledge check** — identify gaps before moving on
5. **Review exam tips** — know the keyword patterns that signal specific answers

### Key Principle

> The AZ-305 exam tests **design decision-making**, not memorization. Every question asks "what should you recommend?" — focus on understanding trade-offs between services.

---

## Prerequisites & Setup

### Required Knowledge
- Azure resource management (AZ-104 level)
- Basic networking (VNets, subnets, NSGs)
- Identity concepts (Entra ID, RBAC)

### Required Tools
- Azure subscription (free trial works for most labs)
- [Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli) 2.x
- [PowerShell 7](https://learn.microsoft.com/powershell/scripting/install/installing-powershell) with Az module
- [VS Code](https://code.visualstudio.com/) with [Bicep extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep)

### Lab Cost Estimate
Most labs can run within a free Azure trial. Estimated cost for all labs: **$30-$50** if completed within 2 weeks and resources are deleted promptly.

---

## Cross-Cutting Themes

These principles apply to EVERY module and EVERY exam question:

### Well-Architected Framework Pillars
| Pillar | Key Question to Ask |
|--------|-------------------|
| **Reliability** | What is the SLA? What happens when this fails? |
| **Security** | Who can access this? How are secrets managed? |
| **Cost Optimization** | What is the cost model? Can we right-size? |
| **Operational Excellence** | How do we monitor? How do we deploy? |
| **Performance Efficiency** | Can it scale? What are the limits? |

### Zero Trust Architecture
- **Verify explicitly** — authenticate and authorize every request
- **Least privilege access** — scoped RBAC, just-in-time access
- **Assume breach** — network segmentation, encryption at rest and in transit

### Managed Identity Pattern
Use managed identity for ALL service-to-service authentication. If a question offers managed identity as an option, it is almost always correct.

---

## Official Microsoft Learn Paths

Complete these learning paths alongside each course module for the best results.

| # | Learning Path | Duration | Maps to |
|---|--------------|----------|--------|
| 0 | [AZ-305 Prerequisites](https://learn.microsoft.com/training/paths/microsoft-azure-architect-design-prerequisites/) | 5 hr 26 min | Pre-work |
| 1 | [Design identity, governance, and monitor solutions](https://learn.microsoft.com/training/paths/design-identity-governance-monitor-solutions/) | 2 hr 25 min | Module 1 |
| 2 | [Design data storage solutions](https://learn.microsoft.com/training/paths/design-data-storage-solutions/) | 2 hr 44 min | Module 2 |
| 3 | [Design business continuity solutions](https://learn.microsoft.com/training/paths/design-business-continuity-solutions/) | 1 hr 46 min | Module 3 |
| 4 | [Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/) | 3 hr 39 min | Modules 4 & 5 |

---

## Microsoft Learning Case Studies

Scenario-based exercises from the [official AZ-305 labs](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/):

| Case Study | Maps to |
|------------|--------|
| [Design a governance solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/01-Governance.html) | Module 1 |
| [Design authentication and authorization solutions](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/06-Authentication.html) | Module 1 |
| [Fabrikam Residences — Logging and monitoring](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/07-Access.html) | Module 1 |
| [Design a non-relational storage solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/04-Nonrelationalstorage.html) | Module 2 |
| [Design a relational storage solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/03-Relationalstorage.html) | Module 2 |
| [Design a compute solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/02-Compute.html) | Module 4 |
| [Design an app architecture solution](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/05-Apparchitecture.html) | Module 4 |
| [Design a network solution — BI enterprise application](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/08-Logging.html) | Module 5 |

---

## External Resources

| Resource | Link |
|----------|------|
| AZ-305 Exam Page | [Official Exam Page](https://learn.microsoft.com/credentials/certifications/exams/az-305/) |
| AZ-305 Study Guide | [aka.ms/AZ305-StudyGuide](https://aka.ms/AZ305-StudyGuide) |
| Free Practice Assessment | [Practice Assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) |
| Exam Sandbox (try the format) | [aka.ms/examdemo](https://aka.ms/examdemo) |
| Exam Prep Videos | [Exam Readiness Zone](https://learn.microsoft.com/shows/exam-readiness-zone/preparing-for-az-305-design-identity-governance-and-monitoring-solutions-1-of-4) |
| Azure Architecture Center | [learn.microsoft.com/azure/architecture](https://learn.microsoft.com/azure/architecture/) |
| Well-Architected Framework | [learn.microsoft.com/azure/well-architected](https://learn.microsoft.com/azure/well-architected/) |
| Cloud Adoption Framework | [learn.microsoft.com/azure/cloud-adoption-framework](https://learn.microsoft.com/azure/cloud-adoption-framework/) |
| Microsoft Learning AZ-305 Labs | [Lab Case Studies](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/) |
| Microsoft Learning AZ-305 Source | [GitHub Repository](https://github.com/MicrosoftLearning/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions) |

---

## Progress Tracker

| Module | Status | Knowledge Check Score | Labs Completed |
|--------|--------|----------------------|----------------|
| 1 - Identity, Governance & Monitoring | Not Started | ___% | ___ / 4 |
| 2 - Data Storage Solutions | Not Started | ___% | ___ / 4 |
| 3 - Business Continuity & HA | Not Started | ___% | ___ / 3 |
| 4 - Infrastructure & Compute | Not Started | ___% | ___ / 3 |
| 5 - Networking & Migrations | Not Started | ___% | ___ / 3 |
| **Practice Assessment** | Not Taken | ___% | |
| **Practice Assessment** | Not Taken | ___% | |
| **Exam Date** | _____________ | | |

> **Practice Assessment:** [Take the free Microsoft practice assessment](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15) after completing all modules.
