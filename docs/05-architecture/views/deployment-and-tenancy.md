# Deployment and Tenancy View

| Field | Value |
|---|---|
| Document ID | ARCH-009 |
| Status | Draft |
| Date | 2026-09-15 |
| Implementation | Planned |
| Source | [Solution Overview](../../../solution-overview-15thSept.md) |

## Profiles

| Profile | Management plane | Tenant data plane | Estate edge |
|---|---|---|---|
| Shared SaaS | Vendor shared | Logically isolated shared services and tenant-partitioned data | Operator estate |
| Dedicated hosted | Vendor shared or dedicated | Dedicated subscription/account and data services | Operator estate |
| Self-hosted | Vendor or customer managed | Customer private cloud under common product contracts | Customer estate |

Zoo, Rides, and Combined editions are entitlement and policy bundles rather than forks.

## Isolation Envelope

Tenant identity is mandatory in API, event, storage, cache, log, metric, secret, backup, fleet, and support-session boundaries. Missing or inconsistent tenant scope is rejected and audited.

## Portability Contract

All profiles use the same domain contracts, policy schema, audit model, upgrade path, and conformance suite. Provider-specific infrastructure details remain TBD because no platform or cloud provider is selected in the source.

## Responsibility Boundary

| Capability | Shared SaaS | Dedicated hosted | Self-hosted |
|---|---|---|---|
| Product software and contract | Vendor | Vendor | Vendor/customer agreement TBD |
| Tenant data operation | Vendor | Vendor | Customer/vendor boundary OI-013 |
| Estate edge operation | Operator | Operator | Customer |
| Assurance evidence | Shared responsibility | Shared responsibility | Boundary OI-013 |

Sovereignty, FedRAMP, residency, cross-border support, and self-hosted responsibilities remain [OI-013](../../00-governance/assumptions-and-open-items.md).

Requirements: BR-004, FR-006, NFR-005, NFR-006, COM-003.
