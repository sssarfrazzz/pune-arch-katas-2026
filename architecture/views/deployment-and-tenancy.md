# Deployment and Tenancy View

| Field | Value |
|---|---|
| Document ID | ARCH-009 |
| Status | Draft |
| Date | 2026-09-16 |
| Implementation | Planned |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

## Profiles

| Profile | Management plane | Tenant data plane | Estate edge |
|---|---|---|---|
| Shared SaaS | Vendor shared | Logically isolated shared services and tenant-partitioned data | Operator estate |
| Dedicated hosted | Vendor shared or dedicated | Dedicated subscription/account and data services | Operator estate |
| Self-hosted | Vendor or customer managed | Customer private cloud under common product contracts | Customer estate |

Zoo, Rides, and Combined editions are entitlement and policy bundles rather than forks.

## Isolation Envelope

Tenant identity is mandatory in API, event, storage, cache, log, metric, secret, backup, device-command, and support-session boundaries. Missing or inconsistent tenant scope is rejected and audited.

## Portability Contract

All profiles use the same domain contracts, policy schema, audit model, upgrade path, and conformance suite. The architecture intentionally does not prescribe a cloud provider. Deployment adapters map provider-specific compute, identity, key management, storage, messaging, observability, backup, and recovery services to this portability contract and must pass the common conformance suite.

## Responsibility Boundary

| Capability | Shared SaaS | Dedicated hosted | Self-hosted |
|---|---|---|---|
| Product software and contract | Vendor operates and supports | Vendor operates and supports | Vendor supplies and supports the product; customer operates the hosting platform under a signed responsibility schedule |
| Tenant data operation | Vendor | Vendor | Customer/vendor boundary defined by contract |
| Estate edge operation | Operator | Operator | Customer |
| Assurance evidence | Shared responsibility | Shared responsibility | Boundary defined by contract |

Deployment administration selects sovereignty, FedRAMP, residency, cross-border, and responsibility controls according to the selected jurisdiction and contract.

Requirements: BR-004, FR-006, NFR-005, NFR-006, COM-003.
