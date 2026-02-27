# Lesson 1: Compute Solutions

**Duration:** 60 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a solution for compute (VMs, App Service, Container Apps, AKS, Functions)
- Specify components of a compute solution based on requirements
- Recommend a solution for containers and serverless computing

---

## 1. Compute Service Decision Tree

This is the **most important decision framework** for AZ-305 exam questions.

```
Need OS-level access or custom software?
  ├── YES ──> Azure Virtual Machines
  └── NO
        Is it event-driven / short-lived?
          ├── YES ──> Azure Functions (serverless)
          └── NO
                Is it a containerized workload?
                  ├── YES ──> Need Kubernetes-level orchestration?
                  │            ├── YES ──> Azure Kubernetes Service (AKS)
                  │            └── NO  ──> Azure Container Apps
                  └── NO ──> Azure App Service (web apps, APIs)
```

### Compute Service Comparison

| Service | Model | Scaling | OS Access | Best For |
|---------|-------|---------|-----------|----------|
| **Virtual Machines** | IaaS | Manual/VMSS | Full | Legacy, custom software |
| **App Service** | PaaS | Auto-scale rules | No | Web apps, REST APIs |
| **Container Apps** | Serverless containers | KEDA/HTTP auto-scale | No | Microservices, event-driven containers |
| **AKS** | Managed K8s | Cluster/pod autoscaler | Node-level | Complex orchestration, K8s expertise |
| **Azure Functions** | FaaS | Consumption (auto) | No | Event-driven, glue logic |
| **Azure Container Instances** | CaaS | None (per-container) | No | Burst, batch, sidecar |
| **Azure Batch** | Managed HPC | Pool auto-scale | Node-level | Parallel/HPC workloads |

---

## 2. Virtual Machines

### VM Size Categories

| Category | Prefix | Use Case |
|----------|--------|----------|
| General purpose | B, D | Balanced CPU/memory, dev/test, web servers |
| Compute optimized | F | CPU-intensive (batch, gaming, analytics) |
| Memory optimized | E, M | Databases, in-memory analytics |
| Storage optimized | L | Big data, SQL/NoSQL databases |
| GPU | N | ML training, rendering, video |
| HPC | H | High-performance compute |

### VM Scaling Options

| Feature | What | When |
|---------|------|------|
| **Vertical scaling** | Change VM size | Need more CPU/RAM (requires restart) |
| **VMSS (Uniform)** | Identical VM pool | Web tier, auto-scale by metrics |
| **VMSS (Flexible)** | Mixed VM sizes | High availability, different SKUs |

### Exam Keyword Mapping

| Exam Phrase | Service |
|-------------|---------|
| "Requires OS-level access" | VM |
| "Install custom device drivers" | VM (GPU if needed) |
| "Lift and shift without changes" | VM |
| "Run third-party licensed software" | VM |

---

## 3. Azure App Service

### Key Features

| Feature | Details |
|---------|---------|
| Languages | .NET, Java, Node.js, Python, PHP, Ruby |
| Deployment | Git, CI/CD, ZIP, Docker container |
| Scaling | Auto-scale (rule-based or automatic) |
| SSL/Custom domain | Built-in, App Service managed certificates (free) |
| Deployment slots | Staging with swap (Standard+ tiers) |

### Plan Tiers

| Tier | Key Feature | Exam Use Case |
|------|-------------|-------------|
| **Free / Shared** | No SLA, shared infra | Dev/test only |
| **Basic** | Dedicated compute, no auto-scale | Simple production |
| **Standard** | Auto-scale, deployment slots | Standard production |
| **Premium v3** | Enhanced compute, VNet integration, zone redundancy | High-performance, private networking |
| **Isolated v2** | ASE (App Service Environment), dedicated VNet | Full network isolation, compliance |

### Exam Decision Points

| Requirement | Tier |
|-------------|------|
| "VNet integration" | Premium v3 or Isolated |
| "Complete network isolation" | Isolated v2 (ASE) |
| "Zone-redundant" | Premium v3 |
| "Deployment slots for blue-green" | Standard+ |

---

## 4. Azure Container Apps

### When to Use Container Apps

- Microservices without K8s management overhead
- HTTP APIs and background workers
- Event-driven processing (KEDA scalers)
- Jobs (scheduled or event-driven batch)

### Key Features

| Feature | Details |
|---------|---------|
| Container runtime | Any Linux container |
| Scaling | HTTP-based, KEDA event triggers, scheduled |
| Scale to zero | Yes (Consumption plan) |
| Built-in | Dapr, service discovery, traffic splitting |
| Revisions | Multiple versions with traffic control |
| Networking | Internal (VNet) or external |

### Container Apps vs. AKS

| Factor | Container Apps | AKS |
|--------|---------------|-----|
| K8s knowledge required | No | Yes |
| Scale to zero | Yes | No (minimum 1 node) |
| Management overhead | Low | High |
| Customization | Limited (opinionated) | Full K8s control |
| Cost for variable workloads | Lower (consumption) | Higher (always running nodes) |
| Exam keyword | "Serverless containers" | "Kubernetes orchestration" |

---

## 5. Azure Kubernetes Service (AKS)

### When to Use AKS

- Team has Kubernetes expertise
- Need custom operators, CRDs, service mesh
- Complex multi-container orchestration
- Compliance requires specific K8s configurations

### Key AKS Concepts for Exam

| Concept | What | Exam Relevance |
|---------|------|---------------|
| **Node pools** | Groups of VMs running pods | System pool (required) + user pools |
| **Cluster autoscaler** | Adds/removes nodes | Based on pending pod demand |
| **HPA** (Horizontal Pod Autoscaler) | Adds/removes pods | Based on CPU/memory metrics |
| **KEDA** | Event-driven pod scaling | Based on queue length, etc. |
| **Azure CNI** | Native VNet IP per pod | Enterprise networking |
| **Kubenet** | Route-based, NAT | Simpler, fewer IPs needed |

### AKS Security

| Feature | Purpose |
|---------|---------|
| Microsoft Entra integration | RBAC with Azure AD identities |
| Workload identity | Pods authenticate with managed identity |
| Network policies | Pod-to-pod traffic filtering |
| Private cluster | API server not publicly accessible |
| Azure Policy for AKS | Enforce container standards |

---

## 6. Azure Functions

### Hosting Plans

| Plan | Scaling | Timeout | VNet | Cold Start |
|------|---------|---------|------|-----------|
| **Consumption** | Auto (0→many) | 5 min (default, max 10) | Limited | Yes |
| **Flex Consumption** | Auto (0→many) | Unlimited | Yes | Reduced (always-ready) |
| **Premium** | Pre-warmed instances | Unlimited | Yes | No (always warm) |
| **Dedicated (App Service)** | Manual / auto-scale | Unlimited | Yes | No |

### Trigger Types

| Trigger | Use Case |
|---------|----------|
| HTTP | REST API, webhooks |
| Timer | Scheduled tasks (CRON) |
| Queue (Storage) | Async message processing |
| Service Bus | Reliable message processing |
| Event Grid | React to Azure resource events |
| Cosmos DB change feed | Process document changes |
| Blob | Process uploaded files |

### Exam Keyword Mapping

| Exam Phrase | Plan |
|-------------|------|
| "Minimize cost, sporadic usage" | Consumption |
| "No cold start, VNet" | Premium |
| "Long-running processing" | Premium or Dedicated |
| "Scale to zero, event-driven" | Consumption or Flex Consumption |

---

## 7. Compute Decision Summary

| Exam Scenario | Service |
|---------------|---------|
| Lift-and-shift legacy Windows app | VM (or App Service if .NET web app) |
| Web app with deployment slots | App Service (Standard+) |
| Microservices, no K8s expertise | Container Apps |
| Complex K8s with custom operators | AKS |
| Timer-triggered cleanup job | Azure Functions (Consumption) |
| Event-driven with VNet, no cold start | Azure Functions (Premium) |
| Parallel batch processing | Azure Batch |
| Quick container burst (CI/CD agent) | Azure Container Instances |
| Complete network isolation | App Service Isolated (ASE) or Private AKS |
| GPU workloads | VM (N-series) or AKS with GPU node pool |

---

## Next Steps

- **Lab:** Deploy [container-apps-environment.bicep](../../infra/container-apps-environment.bicep)
- **Lab:** Deploy [aks-cluster.bicep](../../infra/aks-cluster.bicep)
- **Continue:** [Lesson 2 — Application Architecture](lesson-2-app-architecture.md)

---

## References

- [Compute Decision Tree](https://learn.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree)
- [App Service Overview](https://learn.microsoft.com/azure/app-service/overview)
- [Container Apps Overview](https://learn.microsoft.com/azure/container-apps/overview)
- [AKS Overview](https://learn.microsoft.com/azure/aks/intro-kubernetes)
- [Azure Functions Overview](https://learn.microsoft.com/azure/azure-functions/functions-overview)
