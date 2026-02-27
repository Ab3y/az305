# Module 4 Knowledge Check: Infrastructure & Compute Solutions

**Target Score:** 80%+ before moving to Module 5

---

## Instructions

Choose the BEST answer for each scenario. This is the heaviest exam domain — make sure you understand the trade-offs.

---

### Q1. Compute Selection

A company wants to deploy a web application that processes variable traffic. During peak hours, it handles 1000 requests/second; at night, it drops to near zero. The team has no container or Kubernetes experience. They want to minimize cost and management. What should you recommend?

- A. Azure Virtual Machines with VMSS
- B. Azure App Service (Standard plan)
- C. Azure Container Apps (Consumption plan)
- D. Azure App Service (Premium v3 plan)

<details>
<summary>Show Answer</summary>

**Correct: C**

Container Apps with Consumption plan scales to zero (no cost when idle), auto-scales on HTTP traffic, and requires no K8s expertise. Minimizes both cost and management for variable workloads.

- **A is wrong:** VMSS requires managing VMs and doesn't scale to zero.
- **B is wrong:** Standard App Service plan charges 24/7 even with no traffic.
- **D is wrong:** Premium v3 is even more expensive and doesn't scale to zero.
</details>

---

### Q2. Functions Hosting

A company has an Azure Function that processes messages from a Service Bus queue. The processing takes 15 minutes per message. The Function must access resources in a VNet. What hosting plan should you recommend?

- A. Consumption plan
- B. Flex Consumption plan
- C. Premium plan
- D. Free tier App Service plan

<details>
<summary>Show Answer</summary>

**Correct: C**

Premium plan supports unlimited execution time (no timeout), VNet integration, and pre-warmed instances. Required for long-running + VNet scenarios.

- **A is wrong:** Consumption plan has a maximum 10-minute timeout, which can't handle 15-minute processing.
- **B is wrong:** Flex Consumption supports VNet and long execution but Premium is the established recommendation for guaranteed VNet + long-running.
- **D is wrong:** Free tier doesn't support Functions Premium capabilities.
</details>

---

### Q3. Messaging Service Selection

An IoT platform ingests telemetry from 100,000 sensors sending data every second. The data needs to be processed in near-real-time and archived to Azure Data Lake. What messaging service should you use?

- A. Azure Service Bus
- B. Azure Event Grid
- C. Azure Event Hubs
- D. Azure Queue Storage

<details>
<summary>Show Answer</summary>

**Correct: C**

Event Hubs handles millions of events per second with partitioned consumers, Capture (auto-archive to ADLS), and Kafka compatibility. Purpose-built for high-volume telemetry ingestion.

- **A is wrong:** Service Bus is for commands and workflows, not high-volume telemetry. Lower throughput ceiling.
- **B is wrong:** Event Grid is for discrete events (resource changes), not continuous telemetry streams.
- **D is wrong:** Queue Storage has limited throughput and lacks streaming features like partitions and capture.
</details>

---

### Q4. Service Bus vs. Event Grid

An application needs to notify multiple downstream services when a new order is placed. Each service should receive the notification independently. Messages must support dead-lettering for failed deliveries. What should you recommend?

- A. Azure Service Bus Queue
- B. Azure Service Bus Topic with subscriptions
- C. Azure Event Grid
- D. Azure Event Hubs

<details>
<summary>Show Answer</summary>

**Correct: B**

Service Bus Topics support pub/sub with multiple subscriptions (each service gets its own copy), dead-letter queues for failed messages, and reliable delivery guarantees.

- **A is wrong:** Queues are point-to-point — only one consumer gets each message, not fan-out.
- **C is wrong:** Event Grid supports pub/sub but has limited dead-letter capabilities compared to Service Bus and is better for events, not commands.
- **D is wrong:** Event Hubs is for streaming, not pub/sub command patterns.
</details>

---

### Q5. API Management

A company is exposing internal APIs to external partners. They need rate limiting, OAuth 2.0 token validation, and the ability to publish API documentation for partners. The APIs are deployed in a VNet and must not be directly accessible from the internet. What should you recommend?

- A. APIM Consumption tier
- B. APIM Developer tier
- C. APIM Standard tier
- D. APIM Premium tier with internal VNet mode

<details>
<summary>Show Answer</summary>

**Correct: D**

Premium tier supports internal VNet deployment (APIs not directly internet-accessible), rate limiting, JWT validation policies, and a developer portal for partner documentation.

- **A is wrong:** Consumption tier doesn't support VNet integration.
- **B is wrong:** Developer tier supports external VNet only, not internal mode. Also no SLA.
- **C is wrong:** Standard tier doesn't support VNet integration.
</details>

---

### Q6. Caching Strategy

A web application reads product catalog data from Azure SQL Database. The same data is read millions of times but updated only hourly. Response latency must be under 5ms. What should you recommend?

- A. Increase SQL Database tier to Business Critical
- B. Azure Cache for Redis with cache-aside pattern
- C. Cosmos DB with session consistency
- D. Azure CDN

<details>
<summary>Show Answer</summary>

**Correct: B**

Redis provides sub-millisecond latency for cached data. Cache-aside pattern: check cache first → on miss, read from SQL → populate cache. Hourly updates can invalidate/refresh the cache.

- **A is wrong:** Upgrading SQL tier reduces query latency but can't match Redis sub-ms performance for repeated reads.
- **C is wrong:** Cosmos DB is a database, not a caching layer — adds complexity without solving the caching need.
- **D is wrong:** CDN caches static content at edge locations, not dynamic database query results.
</details>

---

### Q7. Migration Strategy

A company has a legacy .NET Framework 4.5 application running on IIS with a SQL Server 2016 backend. They have a 2-month deadline, no developer resources for code changes, and the database uses SQL Agent jobs and CLR assemblies. What migration strategy and target should you recommend?

- A. Rehost: VMs for app + SQL Server on Azure VM
- B. Refactor: App Service + Azure SQL Database
- C. Rehost: VMs for app + SQL Managed Instance
- D. Rearchitect: Container Apps + Cosmos DB

<details>
<summary>Show Answer</summary>

**Correct: C**

The app is lift-and-shifted to a VM (no code changes needed). SQL Server migrates to SQL Managed Instance because it supports SQL Agent jobs and CLR (Azure SQL Database does not). This is a PaaS upgrade for the database while keeping the app as-is.

- **A is wrong:** SQL Server on VM works but misses the opportunity to use managed PaaS for the database.
- **B is wrong:** Azure SQL Database doesn't support SQL Agent or CLR. .NET Framework 4.5 on App Service may have compatibility issues.
- **D is wrong:** Rearchitecting violates the "no code changes" and 2-month deadline constraints.
</details>

---

### Q8. Azure Migrate

A company wants to migrate 200 VMware VMs to Azure. They need to assess readiness, right-size VMs, estimate costs, and understand dependencies between servers before migrating. What tools should they use?

- A. Azure Site Recovery only
- B. Azure Migrate with discovery, assessment, and dependency analysis
- C. Azure Data Box
- D. Azure Resource Mover

<details>
<summary>Show Answer</summary>

**Correct: B**

Azure Migrate provides the complete discovery-assess-migrate workflow: automatic discovery of VMware VMs, readiness assessment, right-sizing recommendations, cost estimates, and dependency mapping (agent-based or agentless).

- **A is wrong:** ASR handles replication/failover but doesn't provide assessment, right-sizing, or dependency analysis.
- **C is wrong:** Data Box is for offline data transfer, not VM migration.
- **D is wrong:** Resource Mover moves existing Azure resources between regions, not on-premises to Azure.
</details>

---

### Q9. App Configuration

A development team deploys the same application to dev, staging, and production environments. They need to manage environment-specific configuration centrally, toggle features without redeployment, and keep secrets secure. What should you recommend?

- A. App Service application settings per environment
- B. Azure App Configuration with labels + feature flags + Key Vault references
- C. Environment variables in Docker containers
- D. Azure Key Vault only

<details>
<summary>Show Answer</summary>

**Correct: B**

App Configuration with labels (dev/staging/prod) provides centralized config per environment. Feature flags enable toggling without redeployment. Key Vault references securely pull secrets through App Configuration.

- **A is wrong:** App Service settings are per-instance, not centralized. No feature flag support.
- **C is wrong:** Docker environment variables are per-container, not centralized. No feature flags.
- **D is wrong:** Key Vault stores secrets but isn't designed for general configuration or feature flags.
</details>

---

### Q10. Container Orchestration

A company is deploying a microservices application with 15 services. The team has strong Kubernetes expertise and needs custom operators, a service mesh (Istio), and fine-grained control over pod networking with Azure CNI. What should you recommend?

- A. Azure Container Apps
- B. Azure Kubernetes Service (AKS)
- C. Azure Container Instances
- D. Azure App Service with containers

<details>
<summary>Show Answer</summary>

**Correct: B**

AKS provides full Kubernetes control: custom operators, CRDs, Istio service mesh, Azure CNI networking, and granular pod configuration. Required when teams need Kubernetes-level customization.

- **A is wrong:** Container Apps is opinionated and doesn't support custom operators, arbitrary service meshes, or Azure CNI.
- **C is wrong:** ACI runs individual containers, not orchestrated microservices with service mesh.
- **D is wrong:** App Service supports containers but not custom operators, Istio, or K8s-level networking.
</details>

---

## Scoring

| Score | Next Step |
|-------|----------|
| 9-10 / 10 (90-100%) | Excellent! Move to Module 5 |
| 8 / 10 (80%) | Good. Review missed questions, then move to Module 5 |
| 6-7 / 10 (60-70%) | Review the relevant lessons before proceeding |
| Below 6 / 10 (<60%) | Re-study the full module before retaking |

---

## Continue Learning

- **MS Learn Path:** [Design infrastructure solutions](https://learn.microsoft.com/training/paths/design-infranstructure-solutions/)
- **Case Studies:** [Compute](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/02-Compute.html) | [App Architecture](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/05-Apparchitecture.html)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Next:** [Module 5 — Network Solutions](../module-5-networking/overview.md)
