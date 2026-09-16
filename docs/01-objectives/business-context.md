# Business Context

| Field | Value |
|---|---|
| Document ID | OBJ-001 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

## Business Needs

| ID | Need | Observable outcome | Downstream requirements |
|---|---|---|---|
| BN-001 | Improve animal-welfare visibility and intervention. | Coverage for 200+ animals and 55 enclosures; outcome thresholds are [OI-003](../00-governance/assumptions-and-open-items.md). | [BR-002](../02-requirements/business-requirements.md), [FR-009](../02-requirements/functional/operations-intelligence.md) |
| BN-002 | Increase visitor capacity and improve experience visibility. | At least 15,000 visitors/day within three years; start date is [OI-002](../00-governance/assumptions-and-open-items.md). | [BR-001](../02-requirements/business-requirements.md), [FR-015](../02-requirements/functional/operations-intelligence.md) |
| BN-003 | Continue critical estate operations despite unreliable connectivity. | Critical functions operate through 72 hours of cloud isolation. | [BR-003](../02-requirements/business-requirements.md), [NFR-001](../02-requirements/non-functional-requirements.md) |
| BN-004 | Offer one configurable product across estate types and deployment profiles. | Zoo, Rides, and Combined editions use entitlements and policy rather than code forks. | [BR-004](../02-requirements/business-requirements.md), [FR-006](../02-requirements/functional/platform-core.md) |
| BN-005 | Improve workforce coordination and field execution. | Constraint-aware plans, verified coverage, rapid substitution, and offline operation; timing target is [OI-004](../00-governance/assumptions-and-open-items.md). | [BR-005](../02-requirements/business-requirements.md), [FR-012](../02-requirements/functional/operations-intelligence.md) |
| BN-006 | Integrate operational and financial control without replacing systems of record. | Reconciled records, no duplicate revenue, and balanced journal batches. | [BR-006](../02-requirements/business-requirements.md), [FR-004](../02-requirements/functional/platform-core.md) |
| BN-007 | Reduce repetitive physical work through governed autonomy. | Product 2 activates only after Product 1 maturity and applicable certification. | [BR-007](../02-requirements/business-requirements.md), [FR-023](../02-requirements/functional/autonomous-actuation.md) |

## Stakeholder Outcomes

| Stakeholder group | Required outcome |
|---|---|
| Visitors and guardians | Safe, accessible, privacy-preserving admission, queue, entitlement, and engagement experiences. |
| Animal-care and veterinary teams | Timely evidence and escalation without transferring clinical authority to AI or machines. |
| Estate operations | Qualified coverage, offline procedures, explainable re-planning, and safer-state defaults. |
| Finance and administration | Auditable unit economics synchronized with authoritative enterprise systems. |
| Governance bodies | Purpose-limited access, immutable evidence, and jurisdiction-specific compliance. |
| Technology teams | Portable tenancy, resilient edge operation, least privilege, and controlled lifecycle management. |
