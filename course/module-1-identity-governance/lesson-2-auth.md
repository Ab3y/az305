# Lesson 2: Authentication and Authorization

**Duration:** 75 minutes | **Domain Weight:** Part of 25-30%

---

## Learning Objectives

- Recommend an authentication solution (Entra ID, B2B, B2C, federation)
- Recommend an identity management solution (Entra ID vs. hybrid)
- Recommend a solution for authorizing access to Azure resources (RBAC, custom roles)
- Recommend a solution for authorizing access to on-premises resources (Entra Connect, pass-through auth)
- Recommend a solution to manage secrets, certificates, and keys (Key Vault)

---

## 1. Microsoft Entra ID Authentication

### Identity Scenarios

| Scenario | Solution | Key Feature |
|----------|----------|-------------|
| Cloud-only users | Microsoft Entra ID | MFA, Conditional Access, passwordless |
| Hybrid with on-premises AD | Entra Connect Sync or Cloud Sync | Password hash sync, pass-through auth |
| External partners | Entra External ID (B2B) | Partners use own credentials |
| Consumer-facing apps | Entra External ID | Social logins, custom branding (replaces B2C for new projects since May 2025) |

### Authentication Methods (Strongest to Weakest)

| Method | Security Level | User Experience |
|--------|---------------|-----------------|
| FIDO2 security keys | Highest | Phishing-resistant, hardware key |
| Windows Hello for Business | Highest | Biometric or PIN, device-bound |
| Microsoft Authenticator (passwordless) | High | Phone-based, number matching |
| Certificate-based auth | High | Smart card / certificate |
| MFA (phone + password) | Medium | Two-step verification |
| Password only | Low | **Never acceptable for production** |

### Conditional Access Policies

Conditional Access is the Zero Trust policy engine. It evaluates signals and enforces access decisions.

```
Signals (IF):                    Decision (THEN):
  ├── User/Group                   ├── Allow (with MFA, device compliance)
  ├── Application                  ├── Block
  ├── Location (named/IP)          └── Session controls (sign-in frequency,
  ├── Device state                     app enforced restrictions)
  ├── Risk level (Identity Protection)
  └── Client app type
```

**Conditional Access Policy Matrix (Exam Pattern)**

| User Type | MFA Required | Device Compliance | Location | Session Limit |
|-----------|-------------|-------------------|----------|--------------|
| Admins | Always | Required | Named locations only | 1 hour |
| Employees | Risk-based | Required | Any | 8 hours |
| B2B Guests | Always | Not enforced | Named locations only | 4 hours |
| Service accounts | N/A | N/A | N/A | Managed identity preferred |

---

## 2. Hybrid Identity

### Entra Cloud Sync vs. Connect Sync

| Feature | Cloud Sync | Connect Sync v2 |
|---------|------------|-----------------|
| **Management** | Cloud-based portal | On-premises server |
| **Agent** | Lightweight provisioning agent | Full application install |
| **Multi-forest disconnected** | Yes | Limited |
| **Device sync** | No | Yes |
| **Pass-through auth** | No | Yes |
| **Group writeback** | Limited | Yes |
| **AD FS federation** | No | Yes |
| **Large groups (50K+)** | Yes | Yes |
| **Recommended for** | New deployments (simple) | Complex scenarios |

### Decision Tree

```
Need device sync or pass-through auth?
  ├── YES ──> Entra Connect Sync v2
  └── NO
        Need multi-forest disconnected topology?
          ├── YES ──> Entra Cloud Sync
          └── NO ──> Entra Cloud Sync (simpler, cloud-managed)
```

### Password Sync Options

| Method | Passwords in Cloud? | On-Premises Dependency | Best For |
|--------|--------------------|-----------------------|----------|
| Password Hash Sync (PHS) | Hash of hash | None after sync | Most scenarios (recommended) |
| Pass-Through Auth (PTA) | No | Auth agent on-premises | Compliance: passwords never leave on-prem |
| Federation (AD FS) | No | AD FS farm | Legacy apps, smart cards, third-party MFA |

**Exam Tip:** PHS is Microsoft's recommended default. PTA only when compliance mandates passwords never leave on-premises. Federation only for legacy requirements.

---

## 3. External Identity (B2B and External ID)

### B2B vs. External ID (formerly B2C)

| Feature | B2B Collaboration | External ID (Consumer) |
|---------|-------------------|----------------------|
| **Target users** | Partners, vendors, consultants | Customers, consumers |
| **Credential source** | Partner's own identity provider | Social accounts, email, local |
| **Directory** | Guest objects in your tenant | Separate external tenant |
| **Access management** | Access packages, access reviews | Custom user flows |
| **Branding** | Your tenant branding | Fully customizable |
| **Licensing** | Free (up to 50K MAU) | Per-authentication pricing |

### Entitlement Management (Access Packages)

For B2B scenarios, access packages automate the lifecycle:

```
Access Package:
  ├── Resources: Resource Group (Reader), SharePoint Site, Teams Channel
  ├── Policies:
  │     ├── Who can request: External org "Contoso"
  │     ├── Approval: Manager + Resource Owner
  │     ├── Duration: 90 days (renewable)
  │     └── Access review: Quarterly
  └── Assignment: Automatic removal when expired
```

**Exam Keywords:**
- "External partners access Azure resources" → B2B + access packages
- "Quarterly review of guest access" → Access reviews
- "Consumer sign-up with social accounts" → External ID

---

## 4. Azure RBAC (Role-Based Access Control)

### RBAC Fundamentals

```
Security Principal  +  Role Definition  +  Scope  =  Role Assignment
(who)                   (what)              (where)
```

### Scope Hierarchy

```
Management Group ──> Subscription ──> Resource Group ──> Resource
     │                    │                  │               │
     └── Inherited ───────┘── Inherited ─────┘── Inherited ──┘
```

Role assignments at a higher scope are inherited by all child scopes.

### Built-in vs. Custom Roles

| Role Type | When to Use | Example |
|-----------|------------|---------|
| **Built-in** | Standard permissions exist | Reader, Contributor, Owner |
| **Custom** | Need specific combination | "VM Restart Operator" (only restart, no delete) |

### Key Built-in Roles (Exam Favorites)

| Role | Permissions | Exam Scenario |
|------|------------|---------------|
| **Owner** | Full access + assign roles | Subscription administrators |
| **Contributor** | Full access, cannot assign roles | DevOps teams |
| **Reader** | View only | Auditors, monitoring teams |
| **User Access Administrator** | Manage role assignments only | Security team |
| **Key Vault Secrets Officer** | Manage secrets | Application teams (Key Vault RBAC) |
| **Storage Blob Data Contributor** | Read/write blob data | Applications via managed identity |

### Deny Assignments

- Override role assignments (explicit deny)
- Currently only created by Azure Blueprints/Deployment Stacks (not manually)
- Different from NotActions (which exclude actions from a role, not deny them)

**Critical Distinction:**
- `NotActions` = actions excluded from the role (others can grant them)
- `Deny assignment` = actions blocked regardless of other role assignments

---

## 5. Managed Identities

### System-Assigned vs. User-Assigned

| Feature | System-Assigned | User-Assigned |
|---------|----------------|---------------|
| **Lifecycle** | Tied to resource (deleted with it) | Independent (you manage lifecycle) |
| **Sharing** | One identity per resource | One identity across many resources |
| **Pre-provisioning** | Created with resource | Created before resource |
| **Use case** | Simple, single-resource access | Shared access, deployment slots |
| **RBAC management** | More role assignments needed | Fewer assignments (shared) |

### Decision Flow

```
App needs to access Azure resource?
  │
  Does the resource support managed identity?
  ├── YES ──> Multiple resources need same access?
  │            ├── YES ──> User-assigned managed identity
  │            └── NO  ──> System-assigned (simpler) or User-assigned
  │
  └── NO  ──> Workload identity federation (no secrets)
              or Key Vault with service principal (last resort)
```

### Common Managed Identity Scenarios

| Source | Target | Role Assignment |
|--------|--------|----------------|
| App Service | Azure SQL | No role needed — use Entra auth directly |
| App Service | Key Vault | Key Vault Secrets User |
| App Service | Storage | Storage Blob Data Contributor |
| App Service | Service Bus | Azure Service Bus Data Sender/Receiver |
| Container Apps | Cosmos DB | Cosmos DB Built-in Data Contributor |
| Functions | Event Hub | Azure Event Hubs Data Receiver |

**Non-Negotiable Rule:** If managed identity is available, use it. Never store secrets in code, config files, or environment variables.

---

## 6. Azure Key Vault

### Key Vault Tiers

| Feature | Standard | Premium |
|---------|----------|---------|
| Secrets, keys, certificates | Yes | Yes |
| HSM-backed keys | Software-protected | **FIPS 140-2 Level 3** |
| Price | Lower | Higher |
| Use case | Most scenarios | Financial, government, compliance |

### Access Model Decision

| Model | When to Use |
|-------|------------|
| **Azure RBAC** (recommended) | New deployments, unified management with other Azure resources |
| **Vault access policy** | Legacy, per-vault granularity |

### Key Vault Design Patterns

| Pattern | Implementation |
|---------|---------------|
| **Soft delete** | Always enabled (prevents accidental deletion, 7-90 day recovery) |
| **Purge protection** | Enable for compliance (prevents permanent deletion during retention) |
| **Private Link** | Private endpoint for network isolation |
| **Secret rotation** | Event Grid trigger on secret near-expiry → Function rotates → updates Key Vault |
| **Backup** | Key Vault backup for individual keys/secrets (same geo only) |

### Secret Rotation Architecture

```
Key Vault ──(near expiry event)──> Event Grid ──> Azure Function
                                                       │
                                                       v
                                                 Rotate secret
                                                 (e.g., SQL password)
                                                       │
                                                       v
                                                 Update Key Vault
                                                 with new secret
```

**Exam Keywords:**
- "FIPS 140-2 Level 3" → Key Vault Premium
- "No secrets in code" → Managed identity
- "Secret rotation" → Event Grid + Function
- "Purge protection" → Compliance requirement
- "Private network only" → Private Link endpoint

---

## Summary: Authentication & Authorization Decision Matrix

| Question Type | Answer Pattern |
|--------------|---------------|
| "External partners need access" | B2B + access packages + access reviews |
| "Consumer-facing application" | Entra External ID |
| "Hybrid identity, simple setup" | Entra Cloud Sync |
| "Hybrid, need device sync" | Entra Connect Sync v2 |
| "No secrets in application code" | Managed identity (user-assigned) |
| "FIPS 140-2 Level 3" | Key Vault Premium |
| "Least privilege custom permissions" | Custom RBAC role |
| "Multiple subscriptions, same access" | Role assignment at management group scope |

---

## Next Steps

- **Lab:** Deploy [custom-rbac-role.bicep](../../infra/custom-rbac-role.bicep) and test assignments
- **Lab:** Deploy [keyvault-with-private-link.bicep](../../infra/keyvault-with-private-link.bicep) with managed identity
- **Practice:** Run [create-rbac-assignments.sh](../../scripts/az-cli/create-rbac-assignments.sh)
- **Continue:** [Lesson 3 — Governance](lesson-3-governance.md)

---

## References

- [Entra ID Overview](https://learn.microsoft.com/entra/fundamentals/whatis)
- [Conditional Access](https://learn.microsoft.com/entra/identity/conditional-access/overview)
- [B2B Collaboration](https://learn.microsoft.com/entra/external-id/what-is-b2b)
- [Azure RBAC](https://learn.microsoft.com/azure/role-based-access-control/overview)
- [Managed Identities](https://learn.microsoft.com/entra/identity/managed-identities-azure-resources/overview)
- [Key Vault Best Practices](https://learn.microsoft.com/azure/key-vault/general/best-practices)
