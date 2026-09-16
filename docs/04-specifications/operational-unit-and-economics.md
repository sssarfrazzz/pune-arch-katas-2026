# Operational Unit and Economics Specification

| Field | Value |
|---|---|
| Document ID | SPEC-003 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |
| Requirements | FR-001, FR-002, FR-017 to FR-019, FR-030, FR-036, NFR-009, NFR-010 |

## Operational Unit

An Operational Unit represents one ride or enclosure as a stable operational and management-accounting boundary. It is not a legal entity, payroll ledger, general ledger, animal identity, or device identity.

| Attribute group | Required values |
|---|---|
| Identity | Unit ID, type, estate, location, lifecycle state |
| Relationships | Devices, assets, current animals/populations, responsible plan assignments, authoritative enterprise references |
| Operations | Availability, inspections, tasks, incidents, data freshness, confidence |
| Commercial | Public profile, capacity, campaign/package eligibility, attribution profile |
| Finance | Effective Operations Cost, Maintenance Cost, CAPEX allocation, credit weight, pricing/allocation version |

## Calculations

For unit $u$ and period $t$, validated visitor-minutes are $M_{u,t}$ and the effective Unit Credit weight is $X_{u,t}$:

$$
C_{u,t}=M_{u,t}\times X_{u,t}
$$

For standalone pricing with governed price per credit $P_t$:

$$
R_{u,t}=C_{u,t}\times P_t
$$

For package revenue $R^{pkg}_t$ and eligible units $E_t$:

$$
R^{alloc}_{u,t}=R^{pkg}_t\times\frac{C_{u,t}}{\sum_{v\in E_t}C_{v,t}}
$$

The zero-credit denominator behavior is TBD (Finance controller, trigger 2026-09-30) under OI-008.

Unit contribution is attributed revenue minus governed Operations Cost, Maintenance Cost, and CAPEX allocation. Reports MUST include utilization, downtime, data completeness, input-policy versions, and reconciliation status.

## Rules

1. Only an Operational Unit earns Unit Credits; a Cost Pool does not.
2. Inputs are effective-dated and cannot be applied outside their validity period.
3. The same visitor-minute cannot earn standalone and package revenue simultaneously.
4. Late evidence triggers governed recalculation and reconciliation; policy is OI-008.
5. Low contribution can trigger review but cannot automatically close a unit.
6. Unit Credits, Visitor Coins, and Pass Tokens cannot be silently converted.
7. Journal batches remain outside the platform's general-ledger authority and must balance to zero before posting.

## Decision Inputs

Investment, sustainment, refurbishment, pause, and retirement decisions combine contribution with welfare, safety, heritage, conservation, accessibility, contract, and strategy evidence. The approved weighting framework is TBD (Finance controller, trigger 2026-09-30).

## Verification

VER-005 validates identity continuity, formulas, effective dating, duplicate handling, allocation-once behavior, and balanced batches. Evidence remains TBD under OI-015 and is indexed in [Quality Gates](../06-delivery/quality-gates-and-evidence.md).
