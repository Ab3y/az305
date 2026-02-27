# Lesson 3: Governance

**Duration:** 60 minutes | **Domain Weight:** Part of 25-30%

---

## Learning Objectives

- Recommend a structure for management groups, subscriptions, and resource groups
- Recommend a strategy for resource tagging
- Recommend a solution for managing compliance (Azure Policy, Deployment Stacks)
- Recommend a solution for identity governance (PIM, access reviews, entitlement management)

---

## 1. Management Hierarchy Design

### The Four Levels

```
Tenant Root Group
  └── Management Groups (organizational structure)
        └── Subscriptions (billing/access boundary)
              └── Resource Groups (lifecycle container)
                    └── Resources
```

### Management Group Design Pattern (Azure Landing Zones)

```
Root Management Group
  ├── Platform
  │     ├── Connectivity (hub networking, DNS, ExpressRoute)
  │     ├── Identity (domain controllers, Entra Connect)
  │     └── Management (Log Analytics, Automation)
  ├── Landing Zones
  │     ├── Corp (internal apps, no public inbound)
  │     ├── Online (external-facing apps)
  │     └── SAP (specialized workloads)
  ├── Sandbox (experimentation, relaxed policies)
  └── Decommissioned (retired workloads, strict deny policies)
```

### When to Split Subscriptions

| Reason | Example |
|--------|---------|
| **Billing boundary** | Separate cost centers for departments |
| **Access boundary** | Dev team cannot touch production |
| **Scale limits** | Approaching subscription resource limits |
| **Compliance** | Regulated workloads require isolation |
| **Environment isolation** | Dev / Test / Prod separation |

### Resource Group Design

| Pattern | Group By | When |
|---------|----------|------|
| **Lifecycle** | Resources deployed/deleted together | Most common, recommended |
| **Application** | All resources for one app | Microservices teams |
| **Resource type** | All VMs, all databases | Shared platform teams |
| **Environment** | Dev, test, prod | Small organizations |

**Key Rule:** A resource can only belong to one resource group. Resource groups are a logical container, NOT a security boundary (use RBAC for security).

---

## 2. Resource Tagging

### Tagging Strategy

| Tag Category | Example Tags | Purpose |
|-------------|-------------|---------|
| **Business** | `CostCenter`, `BusinessUnit`, `Owner` | Chargeback, accountability |
| **Technical** | `Environment`, `Application`, `Tier` | Automation, filtering |
| **Compliance** | `DataClassification`, `Compliance` | Regulatory requirements |
| **Operations** | `SLA`, `MaintenanceWindow`, `DR-Priority` | Operations and DR planning |

### Tag Enforcement Methods

| Method | Effect | Use Case |
|--------|--------|----------|
| Azure Policy: `require` | Deny creation without tag | Mandatory tags (CostCenter, Owner) |
| Azure Policy: `inherit` | Copy tag from resource group using Modify effect | Consistent tagging without user burden |
| Azure Policy: `audit` | Flag non-compliant resources | Soft enforcement during rollout |
| ARM/Bicep template defaults | Apply in template | IaC-deployed resources |

### Tag Inheritance

Tags do NOT automatically inherit from subscription → resource group → resource. You must use **Azure Policy with Modify effect** to copy tags from parent scopes.

```
Policy: "Inherit CostCenter tag from resource group"
  Effect: Modify
  Action: addOrReplace tag on resource with value from resource group
  Result: New resources automatically get parent's CostCenter tag
```

---

## 3. Azure Policy

### Policy Fundamentals

| Concept | Description |
|---------|-------------|
| **Policy definition** | Single rule (e.g., "require HTTPS on storage") |
| **Initiative (policy set)** | Group of related policies (e.g., CIS Benchmark) |
| **Assignment** | Apply a policy/initiative to a scope |
| **Exemption** | Exclude a specific resource/scope from a policy |
| **Remediation** | Fix existing non-compliant resources |

### Policy Effects (Order of Evaluation)

| Effect | Behavior | When to Use |
|--------|----------|------------|
| **Disabled** | Policy not evaluated | Testing, temporary bypass |
| **Append** | Add fields to request | Add required properties |
| **Modify** | Change properties on existing resources | Tag inheritance, enable features |
| **Deny** | Block the request | Hard guardrails (no public IPs, required encryption) |
| **Audit** | Log non-compliance, allow creation | Soft enforcement, awareness |
| **AuditIfNotExists** | Audit if related resource missing | Check for diagnostic settings |
| **DeployIfNotExists (DINE)** | Auto-deploy related resource | Auto-enable monitoring, backups |
| **Manual** | Requires manual attestation | Compliance processes |

### Policy Assignment Strategy

| Scope Level | Policy Type | Effect | Example |
|-------------|-------------|--------|---------|
| Root Management Group | Security baselines | **Deny** | No public IPs, require encryption |
| Platform MG | Platform operations | **DINE** | Deploy diagnostic settings, enable Defender |
| Landing Zone MG | Application governance | **Audit → Deny** | Allowed SKUs, required tags |
| Subscription | Environment-specific | **Deny** | Allowed regions, resource types |
| Sandbox MG | Relaxed | **Audit only** | Security policies only (not cost) |

### Initiatives vs. Individual Policies

| Use | Type |
|-----|------|
| Single specific requirement | Policy definition |
| Compliance framework (CIS, NIST, PCI) | Initiative |
| Custom organizational standards | Custom initiative |

**Exam Tip:** If the question mentions "compliance framework" or "regulatory standard," the answer is an initiative, not individual policies.

### Azure Blueprints → Deployment Stacks

Blueprints are **deprecated (July 2026)**. The replacement is **Deployment Stacks**:

| Feature | Blueprints (deprecated) | Deployment Stacks |
|---------|------------------------|-------------------|
| Scope | Subscription | Management group, subscription, or resource group |
| Deny settings | Blueprint lock | Deny settings on stack |
| Template support | ARM only | Bicep and ARM |
| Versioning | Built-in | Git-based |
| Status | Deprecated July 2026 | GA, actively developed |

---

## 4. Compliance Management

### Microsoft Defender for Cloud

| Feature | Purpose |
|---------|---------|
| **Secure Score** | Overall security posture (0-100%) |
| **Regulatory compliance dashboard** | Map controls to standards (CIS, NIST, PCI-DSS) |
| **Recommendations** | Prioritized security improvements |
| **Cloud Security Posture Management (CSPM)** | Free tier for basic posture |
| **Cloud Workload Protection (CWP)** | Paid plans for specific resource types |

### Compliance Dashboard Flow

```
Azure Policy (initiatives) ──> Defender for Cloud ──> Regulatory Compliance Dashboard
                                     │
                                     v
                              Standards: CIS, NIST 800-53, PCI-DSS, ISO 27001
                                     │
                                     v
                              Controls mapped to policy results
                              (compliant / non-compliant / exempt)
```

---

## 5. Identity Governance

### Privileged Identity Management (PIM)

PIM provides just-in-time (JIT) privileged access:

| Feature | Purpose |
|---------|---------|
| **Eligible assignments** | User CAN activate the role (not active by default) |
| **Time-bound activation** | Role active for 1-8 hours only |
| **Approval workflow** | Require approval before activation |
| **MFA on activation** | Force re-authentication |
| **Justification** | Require reason for activation |
| **Audit trail** | Full log of who activated what, when, and why |

### PIM Configuration Pattern

```
Role: Contributor (Production Subscription)
  ├── Assignment type: Eligible (not permanent)
  ├── Duration: Maximum 4 hours per activation
  ├── Approval: Required (Security team)
  ├── MFA: Required on activation
  ├── Justification: Required
  └── Notification: Email to subscription owner
```

### Access Reviews

| Setting | Recommendation |
|---------|---------------|
| **Frequency** | Quarterly for guests, semi-annual for employees |
| **Reviewers** | Resource owners or managers |
| **Auto-apply** | Remove access if not reviewed |
| **Scope** | Groups, application assignments, Azure roles |

### Entitlement Management

For lifecycle management of access packages:

```
Access Package: "Project Alpha Resources"
  ├── Catalog: IT Department
  ├── Resources:
  │     ├── Azure Resource Group (Contributor)
  │     ├── SharePoint Site (Member)
  │     └── Teams Channel (Member)
  ├── Request Policy:
  │     ├── Who: Users from Contoso.com
  │     ├── Approval: 2-stage (manager → resource owner)
  │     └── Duration: 180 days
  ├── Lifecycle:
  │     ├── Renewable: Yes (with re-approval)
  │     ├── Access review: Every 90 days
  │     └── Auto-removal: On expiry
  └── Separation of duties: Cannot hold "Finance" and "Audit" packages
```

### Identity Governance Decision Matrix

| Scenario | Solution |
|----------|---------|
| Admins need temporary elevated access | PIM (eligible assignments) |
| Review if guests still need access | Access reviews |
| External partners need scoped, time-limited access | Entitlement management (access packages) |
| Prevent permanent Owner assignments | PIM with time-bound activation |
| Automate user onboarding/offboarding | Lifecycle workflows |

---

## 6. Summary Decision Matrix

| Exam Keyword | Answer |
|-------------|--------|
| "Management group" + "multiple subscriptions" | Policy at management group scope |
| "Tag enforcement" | Azure Policy with Deny effect |
| "Tag inheritance" | Azure Policy with Modify effect |
| "CIS Benchmark" / "compliance framework" | Policy initiative + Defender for Cloud |
| "Just-in-time admin access" | PIM with eligible assignments |
| "Quarterly guest review" | Access reviews |
| "Time-limited partner access" | Entitlement management (access packages) |
| "Prevent accidental deletion" | Resource locks (not governance, but often tested) |
| "Blueprints replacement" | Deployment Stacks |
| "Environment standardization" | Deployment Stacks + Policy |

---

## Next Steps

- **Lab:** Deploy [azure-policy-initiative.bicep](../../infra/azure-policy-initiative.bicep)
- **Practice:** Run [Configure-PolicyInitiative.ps1](../../scripts/powershell/Configure-PolicyInitiative.ps1)
- **Practice:** Run [Enable-EntraPIM.ps1](../../scripts/powershell/Enable-EntraPIM.ps1)
- **Knowledge Check:** [Module 1 Knowledge Check](knowledge-check.md)

---

## References

- [Management Groups](https://learn.microsoft.com/azure/governance/management-groups/overview)
- [Azure Policy Overview](https://learn.microsoft.com/azure/governance/policy/overview)
- [Deployment Stacks](https://learn.microsoft.com/azure/azure-resource-manager/bicep/deployment-stacks)
- [PIM Overview](https://learn.microsoft.com/entra/id-governance/privileged-identity-management/pim-configure)
- [Access Reviews](https://learn.microsoft.com/entra/id-governance/access-reviews-overview)
- [Azure Landing Zones](https://learn.microsoft.com/azure/cloud-adoption-framework/ready/landing-zone/)
