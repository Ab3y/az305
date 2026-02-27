# Lesson 2: Application Architecture

**Duration:** 60 minutes | **Domain Weight:** Part of 30-35%

---

## Learning Objectives

- Recommend a messaging architecture
- Recommend a caching solution
- Recommend an API integration solution
- Recommend a configuration management solution

---

## 1. Messaging Services

### The Three Messaging Services

| Service | Pattern | Delivery | Best For |
|---------|---------|----------|----------|
| **Service Bus** | Message broker (queue/topic) | At-least-once, FIFO, sessions | Commands, transactions, workflows |
| **Event Grid** | Event routing (pub/sub) | At-least-once, push | React to resource events, webhooks |
| **Event Hubs** | Event streaming | Partitioned consumer | Telemetry, log ingestion, big data |

### Decision Tree

```
Is it a command (action to perform)?
  ├── YES ──> Azure Service Bus
  └── NO
        Is it a discrete event (something happened)?
          ├── YES ──> Azure Event Grid
          └── NO
                Is it high-volume streaming data?
                  └── YES ──> Azure Event Hubs
```

### Service Bus Deep Dive

| Feature | Queue | Topic |
|---------|-------|-------|
| Pattern | Point-to-point | Publish-subscribe |
| Receivers | One consumer per message | Multiple subscriptions |
| Use case | Task distribution, commands | Fan-out notifications |
| Ordering | FIFO (sessions) | Per-subscription FIFO |
| Dead-letter | Yes | Yes |

| Tier | Feature | Exam Use Case |
|------|---------|-------------|
| **Basic** | Queues only | Simple messaging |
| **Standard** | Queues + Topics | Pub/sub patterns |
| **Premium** | Dedicated capacity, VNet | Enterprise, predictable performance |

**Key Features for Exam:**
- **Sessions:** Guarantee FIFO ordering and message grouping
- **Dead-letter queue:** Handle poison messages
- **Duplicate detection:** Prevent processing same message twice
- **Scheduled delivery:** Send messages for future processing
- **Transactions:** Atomic operations across messages

### Event Grid Deep Dive

| Component | Description |
|-----------|-------------|
| **Event source** | Azure service emitting events (Storage, Resource Group, etc.) |
| **Topic** | Endpoint that receives events |
| **Event subscription** | Route events to handler with optional filtering |
| **Event handler** | Destination (Function, Logic App, webhook, queue) |

**Common Event Sources:**
- Blob Storage (blob created, deleted)
- Resource Groups (resource created, deleted, updated)
- Azure subscriptions (policy changes)
- Container Registry (image pushed)
- IoT Hub (device telemetry)

### Event Hubs Deep Dive

| Feature | Description |
|---------|-------------|
| Throughput | Millions of events per second |
| Retention | 1-90 days (or unlimited with capture) |
| Partitions | 1-32 (Standard), up to 2000 (Dedicated) |
| Consumer groups | Independent readers of the same stream |
| Capture | Auto-archive to Blob Storage / ADLS Gen2 |

| Tier | Throughput | Exam Use Case |
|------|-----------|-------------|
| **Basic** | 1 consumer group | Dev/test |
| **Standard** | 20 consumer groups | Production |
| **Premium** | Processing Units | Isolation, VNet |
| **Dedicated** | Capacity Units | Extreme scale |

---

## 2. Azure Cache for Redis

### Use Cases

| Pattern | Description | Exam Keyword |
|---------|-------------|-------------|
| **Data cache** | Cache database query results | "Reduce database load" |
| **Session store** | Store user session state | "Stateless web tier" |
| **Content cache** | Cache static content | "Reduce latency for repeated reads" |
| **Distributed lock** | Coordinate across instances | "Resource contention" |
| **Message broker** | Pub/sub messaging (lightweight) | "Simple pub/sub" |

### Tier Selection

| Tier | Clustering | Geo-Replication | VNet | Best For |
|------|-----------|----------------|------|----------|
| **Basic** | No | No | No | Dev/test |
| **Standard** | No | No | No | Simple caching |
| **Premium** | Yes | Passive | Yes | Enterprise, persistence |
| **Enterprise** | Yes | Active-active | Yes | Mission-critical, Redis modules |

### Caching Patterns

| Pattern | How | When |
|---------|-----|------|
| **Cache-aside** | App reads cache; on miss, reads DB and populates cache | Most common, read-heavy |
| **Write-through** | Write to cache + DB simultaneously | Consistency critical |
| **Write-behind** | Write to cache, async flush to DB | Write-heavy, eventual consistency OK |

---

## 3. Azure API Management (APIM)

### Core Capabilities

| Feature | Description |
|---------|-------------|
| **API gateway** | Single entry point for all APIs |
| **Developer portal** | Self-service API documentation and testing |
| **Policies** | Transform requests/responses (rate limiting, caching, auth) |
| **Products** | Group APIs with access policies |
| **Subscriptions** | API keys for access control |

### Tier Selection

| Tier | VNet | Multi-region | Self-hosted | Best For |
|------|------|-------------|-------------|----------|
| **Consumption** | No | No | No | Serverless, pay-per-call |
| **Developer** | Yes (external only) | No | Yes | Dev/test |
| **Basic** | No | No | No | Entry production |
| **Standard** | No | No | Yes | Standard production |
| **Premium** | Yes (internal + external) | Yes | Yes | Enterprise, VNet integration |

### Key Policies for Exam

| Policy | Purpose | Exam Keyword |
|--------|---------|-------------|
| `rate-limit` | Throttle calls per subscription | "Prevent abuse" |
| `quota` | Limit total calls per period | "Monthly usage cap" |
| `validate-jwt` | Validate OAuth 2.0 tokens | "Secure API with Azure AD" |
| `cache-lookup/cache-store` | Cache API responses | "Reduce backend load" |
| `cors` | Enable cross-origin requests | "SPA calling API" |
| `ip-filter` | Restrict by IP address | "Whitelist IPs" |
| `set-backend-service` | Route to different backends | "Versioning, blue-green" |
| `rewrite-uri` | Transform URL paths | "Backend URL mapping" |

### APIM + Azure AD Integration

```
Client ──> Azure AD (get token) ──> APIM (validate-jwt) ──> Backend API
```

---

## 4. Azure App Configuration

### What It Does

Centralized configuration management separate from application code.

| Feature | Description |
|---------|-------------|
| Key-value store | Hierarchical, labeled configuration |
| Feature flags | Enable/disable features without redeployment |
| Key Vault references | Pull secrets from Key Vault through App Configuration |
| Snapshots | Point-in-time configuration snapshots |
| Events | Event Grid integration for config changes |

### App Configuration vs. Key Vault

| Factor | App Configuration | Key Vault |
|--------|-------------------|-----------|
| Data type | Non-sensitive configuration | Secrets, certificates, keys |
| Access model | Read-heavy, fast | Cryptographic operations |
| Versioning | Labels and snapshots | Secret versions |
| Use together | Yes — reference Key Vault secrets from App Config |

### Feature Flags Pattern

```
App Configuration
  ├── Feature: "NewCheckoutFlow"
  │     ├── Enabled: true
  │     └── Filter: 10% of users (percentage rollout)
  ├── Feature: "DarkMode"
  │     ├── Enabled: true
  │     └── Filter: Users in "beta-testers" group
  └── Feature: "MaintenanceMode"
        └── Enabled: false
```

---

## 5. Microservices Architecture Patterns

### Key Patterns for AZ-305

| Pattern | Implementation | Exam Keyword |
|---------|---------------|-------------|
| **API Gateway** | APIM | Single entry point, cross-cutting concerns |
| **Service discovery** | Container Apps built-in | "Services find each other" |
| **Event-driven** | Service Bus / Event Grid | Loosely coupled services |
| **CQRS** | Separate read/write models | "Optimize reads and writes separately" |
| **Saga** | Service Bus with orchestrator | "Distributed transactions" |
| **Sidecar** | Dapr in Container Apps | "Cross-cutting concerns per service" |
| **Circuit breaker** | APIM retry policy / app code | "Prevent cascade failures" |

### Dapr Integration (Container Apps)

| Building Block | Purpose |
|----------------|---------|
| Service invocation | Service-to-service calls with mTLS |
| State management | Pluggable state stores |
| Pub/sub | Event-driven messaging |
| Bindings | Input/output connectors |
| Secrets | Centralized secret management |

---

## 6. Summary Decision Matrix

| Scenario | Service |
|----------|---------|
| Reliable message delivery, FIFO | Service Bus (with sessions) |
| React to Azure resource events | Event Grid |
| High-volume telemetry ingestion | Event Hubs |
| Reduce database read load | Azure Cache for Redis |
| Stateless web tier (session store) | Azure Cache for Redis |
| Centralize API access + rate limiting | API Management |
| Complete API network isolation | APIM Premium (internal VNet) |
| Feature flags without redeployment | App Configuration |
| Centralized config + secrets | App Configuration + Key Vault |
| Distributed transactions across services | Saga pattern with Service Bus |

---

## Next Steps

- **Lab:** Deploy [apim-with-backends.bicep](../../infra/apim-with-backends.bicep)
- **Explore:** [API Architecture diagram](../../images/api-architecture.mmd)
- **Continue:** [Lesson 3 — Migrations](lesson-3-migrations.md)

---

## References

- [Service Bus Overview](https://learn.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Event Grid Overview](https://learn.microsoft.com/azure/event-grid/overview)
- [Event Hubs Overview](https://learn.microsoft.com/azure/event-hubs/event-hubs-about)
- [Redis Cache Overview](https://learn.microsoft.com/azure/azure-cache-for-redis/cache-overview)
- [API Management Overview](https://learn.microsoft.com/azure/api-management/api-management-key-concepts)
- [App Configuration Overview](https://learn.microsoft.com/azure/azure-app-configuration/overview)
