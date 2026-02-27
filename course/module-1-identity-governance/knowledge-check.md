# Module 1 Knowledge Check: Identity, Governance & Monitoring

**Target Score:** 80%+ before moving to Module 2

---

## Instructions

Choose the BEST answer for each scenario. Focus on understanding WHY each answer is correct — the exam tests design decision-making.

---

### Q1. Logging Architecture

Contoso Ltd. operates 50+ Azure subscriptions across multiple business units. They need centralized log collection with 90-day retention for compliance, cost-efficient storage for older logs, and the ability to query across all subscriptions. What should you recommend?

- A. One Log Analytics workspace per subscription with cross-workspace queries
- B. A single centralized Log Analytics workspace with resource-context RBAC
- C. Azure Monitor Logs with dedicated cluster and customer-managed keys
- D. Multiple Log Analytics workspaces federated with Azure Data Explorer

<details>
<summary>Show Answer</summary>

**Correct: B**

A single centralized workspace with resource-context RBAC provides unified querying, cost efficiency (bulk ingestion pricing via commitment tiers), and granular access control based on Azure resource permissions. This is the recommended pattern for multi-subscription enterprises.

- **A is wrong:** Multiple workspaces increase cost and complexity. Cross-workspace queries have limits and are slower.
- **C is wrong:** Dedicated clusters require 500GB+/day commitment — overkill unless you need CMK or higher performance.
- **D is wrong:** ADX federation adds complexity; only justified for petabyte-scale analytics.
</details>

---

### Q2. Log Routing

Wingtip Toys needs to route Azure Activity Logs to their SIEM system (Splunk), retain logs in Azure for 7 years for compliance, and enable near-real-time alerting. Which architecture should you recommend?

- A. Diagnostic settings to Event Hub (SIEM) + Storage Account (archive) + Log Analytics (alerting)
- B. Diagnostic settings to Log Analytics only with 7-year retention
- C. Azure Monitor Agent to Log Analytics with export rules to Storage
- D. Direct API integration from SIEM to Azure Activity Log

<details>
<summary>Show Answer</summary>

**Correct: A**

The fan-out pattern using diagnostic settings to multiple destinations: Event Hub for real-time SIEM streaming, Storage Account for cost-effective 7-year archive, Log Analytics for alerting and investigation.

- **B is wrong:** Log Analytics interactive retention max is 730 days (2 years). Archive tier extends to 12 years, but Storage Account is more cost-effective for 7-year retention.
- **C is wrong:** Azure Monitor Agent is for VMs, not Activity Logs. Export rules go to Storage, not Log Analytics.
- **D is wrong:** Polling APIs is inefficient and doesn't meet real-time requirements.
</details>

---

### Q3. Application Performance

Fabrikam runs microservices on AKS. They require distributed tracing, auto-scaling based on custom metrics, and cost control. What should you recommend?

- A. Application Insights with workspace-based mode, sampling enabled, and custom metrics for KEDA
- B. Application Insights with classic mode and Prometheus integration
- C. Azure Monitor for Containers with built-in Application Insights
- D. Third-party APM tool with OpenTelemetry export

<details>
<summary>Show Answer</summary>

**Correct: A**

Workspace-based Application Insights is the modern standard — unified querying, sampling reduces costs, and custom metrics can drive KEDA autoscaling.

- **B is wrong:** Classic mode is deprecated. Prometheus doesn't provide distributed tracing.
- **C is wrong:** Azure Monitor for Containers provides infrastructure metrics, not application-level traces.
- **D is wrong:** Third-party tools add cost and complexity when native options meet requirements.
</details>

---

### Q4. External Partner Access

Contoso needs to give 500 consultants (external users) access to specific Azure resources. Consultants should use their own corporate credentials, access must be reviewable quarterly, and least privilege is mandatory. What should you recommend?

- A. Microsoft Entra B2B with access packages and access reviews
- B. Microsoft Entra B2C with custom policies
- C. Sync external users to Microsoft Entra ID with Entra Connect
- D. Create cloud-only accounts for each consultant

<details>
<summary>Show Answer</summary>

**Correct: A**

B2B collaboration with Entitlement Management (access packages) and access reviews is the enterprise pattern for external partner access. Users keep their own credentials, access is time-bound and reviewable.

- **B is wrong:** B2C / External ID is for consumer-facing apps, not business partner collaboration.
- **C is wrong:** Syncing external users violates identity sovereignty and complicates management.
- **D is wrong:** Cloud-only accounts create credential sprawl and don't support quarterly reviews natively.
</details>

---

### Q5. Managed Identity

Wingtip Toys runs an e-commerce app on Azure App Service that needs to access Azure SQL Database, Azure Storage, and Azure Key Vault. The solution must have zero secrets in application code and support automatic credential rotation. What should you recommend?

- A. User-assigned managed identity for all services
- B. System-assigned managed identity for each App Service instance
- C. Service principal with certificate authentication stored in Key Vault
- D. Microsoft Entra application with client secret rotated monthly

<details>
<summary>Show Answer</summary>

**Correct: A**

User-assigned managed identity provides zero-secret authentication, automatic credential management, and can be shared across deployment slots and resources.

- **B is wrong:** System-assigned identities work but create access management overhead with multiple instances (each gets a unique identity).
- **C is wrong:** Service principals with certificates still require certificate management — managed identity eliminates this.
- **D is wrong:** Client secrets require rotation management and risk exposure.
</details>

---

### Q6. Key Vault Design

Fabrikam's financial services application must store database connection strings, API keys, and SSL certificates. They require FIPS 140-2 Level 3 compliance, automatic secret rotation, and private network access only. What should you recommend?

- A. Key Vault Premium with Private Link, Event Grid for rotation, purge protection enabled
- B. Key Vault Standard with VNet service endpoints and manual rotation
- C. Azure App Configuration with Key Vault references
- D. Key Vault Premium with access policies and public endpoint

<details>
<summary>Show Answer</summary>

**Correct: A**

Key Vault Premium provides HSM-backed keys (FIPS 140-2 Level 3). Private Link ensures private network access. Event Grid triggers automatic rotation. Purge protection is required for financial compliance.

- **B is wrong:** Standard tier doesn't provide FIPS 140-2 Level 3 (software-protected only). Service endpoints don't provide private IPs. Manual rotation doesn't meet requirements.
- **C is wrong:** App Configuration stores configuration, not secrets. Key Vault references are good practice but don't address the core requirements.
- **D is wrong:** Public endpoint violates "private network access only."
</details>

---

### Q7. RBAC Design

A company has three Azure subscriptions: Dev, Test, and Prod. The security team must be able to manage role assignments across all subscriptions but should have no other permissions. What should you recommend?

- A. Assign User Access Administrator role at the management group scope containing all three subscriptions
- B. Assign Owner role at each subscription scope
- C. Assign Contributor role at the management group scope
- D. Create a custom role with all permissions at each subscription

<details>
<summary>Show Answer</summary>

**Correct: A**

User Access Administrator grants only the ability to manage role assignments. Assigning at management group scope covers all subscriptions with a single assignment. This follows least privilege.

- **B is wrong:** Owner has full permissions — violates least privilege.
- **C is wrong:** Contributor cannot manage role assignments.
- **D is wrong:** Unnecessary complexity; a built-in role meets the requirement.
</details>

---

### Q8. Policy Design

An organization must ensure that all new Azure resources are created only in East US and West US regions, and all resources must have a `CostCenter` tag. Non-compliant existing resources should be flagged but not deleted. What should you recommend?

- A. Two Azure policies: `Deny` effect for allowed regions, `Audit` effect for the tag requirement on existing resources with `Deny` for new resources
- B. A single Azure Policy initiative with `Deny` effect for both policies
- C. Azure Blueprints with region and tag constraints
- D. Management group with subscription-level region restrictions

<details>
<summary>Show Answer</summary>

**Correct: A**

Two separate policies address different requirements: Deny for regions (block new resources in wrong regions), and a combination approach for tags (Audit existing, Deny new). This enforces going forward while giving time to remediate existing resources.

- **B is wrong:** Deny on existing resources without tags would block updates to those resources.
- **C is wrong:** Blueprints are deprecated (July 2026).
- **D is wrong:** Management groups don't inherently restrict regions.
</details>

---

### Q9. PIM Configuration

A company's database administrators need occasional Contributor access to the production subscription. Access should require approval, be time-limited, and create an audit trail. What should you recommend?

- A. PIM with eligible assignment, 4-hour maximum activation, approval required, justification required
- B. Permanent Contributor role with conditional access policy
- C. Just-in-time VM access through Defender for Cloud
- D. Custom RBAC role with time-based conditions

<details>
<summary>Show Answer</summary>

**Correct: A**

PIM with eligible assignments provides just-in-time access with all required controls: approval workflow, time-bound activation, justification, and full audit trail.

- **B is wrong:** Permanent role doesn't meet "occasional" or "time-limited" requirements. Conditional access controls authentication, not role activation.
- **C is wrong:** JIT VM access is for network ports (NSG), not RBAC.
- **D is wrong:** Custom RBAC roles don't support time-based activation natively.
</details>

---

### Q10. Hybrid Identity

A company is migrating to Azure. They have three disconnected AD forests, cannot allow password hashes in the cloud, and need seamless SSO. What should you recommend?

- A. Entra Connect Sync v2 with pass-through authentication and seamless SSO
- B. Entra Cloud Sync with password hash sync
- C. AD FS federation with each forest
- D. Entra Cloud Sync with pass-through authentication

<details>
<summary>Show Answer</summary>

**Correct: A**

Entra Connect Sync v2 supports pass-through authentication (passwords never leave on-premises) and seamless SSO. It can be configured for multiple forests.

- **B is wrong:** Cloud Sync doesn't support pass-through authentication. PHS puts password hashes in the cloud.
- **C is wrong:** AD FS adds significant infrastructure complexity. Only use for legacy requirements.
- **D is wrong:** Cloud Sync does not support pass-through authentication.
</details>

---

## Scoring

| Score | Next Step |
|-------|----------|
| 9-10 / 10 (90-100%) | Excellent! Move to Module 2 |
| 8 / 10 (80%) | Good. Review missed questions, then move to Module 2 |
| 6-7 / 10 (60-70%) | Review the relevant lessons before proceeding |
| Below 6 / 10 (<60%) | Re-study the full module before retaking |

---

## Continue Learning

- **MS Learn Path:** [Design identity, governance, and monitor solutions](https://learn.microsoft.com/training/paths/design-identity-governance-monitor-solutions/)
- **Case Studies:** [Governance](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/01-Governance.html) | [Authentication](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/06-Authentication.html) | [Logging](https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/Instructions/CaseStudy/07-Access.html)
- **Practice Assessment:** [Official AZ-305 practice questions](https://learn.microsoft.com/credentials/certifications/exams/az-305/practice/assessment?assessment-type=practice&assessmentId=15)
- **Next:** [Module 2 — Data Storage Solutions](../module-2-data-storage/overview.md)
