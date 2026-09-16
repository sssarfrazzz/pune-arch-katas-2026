# Operational Unit and Economics Specification

| Field | Value |
|---|---|
| Document ID | SPEC-003 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |
| Requirements | FR-001, FR-002, FR-017 to FR-019, FR-030, FR-036, FR-047, NFR-009, NFR-010 |

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

If no eligible Unit Credits exist, the period is reported as not attributable rather than forced to zero-value allocation.

Unit contribution is attributed revenue minus governed Operations Cost, Maintenance Cost, and CAPEX allocation. Reports MUST include utilization, downtime, data completeness, input-policy versions, and reconciliation status, satisfying the unit- and zone-level operational reporting required by FR-047.

## Rules

1. Only an Operational Unit earns Unit Credits; a Cost Pool does not.
2. Inputs are effective-dated and apply only within their validity period.
3. The same visitor-minute cannot earn standalone and package revenue simultaneously.
4. Late evidence triggers governed recalculation and reconciliation.
5. Low contribution can trigger review but cannot automatically close a unit.
6. Unit Credits, Visitor Coins, and Pass Tokens cannot be silently converted.
7. The general ledger retains posting authority, and journal batches must balance to zero before posting.

## Decision Inputs

Investment, sustainment, refurbishment, pause, and retirement decisions use a gated multi-criteria review and do not collapse all factors into one financial score.

1. The applicable welfare, safety, legal, heritage, accessibility, conservation, and contractual owner records each mandatory constraint as pass, conditional, or fail. A fail blocks an economics-only pause or retirement decision.
2. Finance presents five-year cost and revenue outlook, current contribution, demand/utilization, downtime, maintenance backlog, capital need, data completeness, and sensitivity ranges without overriding mandatory constraints.
3. The Estate executive records sustain, invest, refurbish, pause, or retire, the evidence considered, dissent or conditions, review date, and concurrences from each applicable mandatory-constraint owner.
4. A material change in welfare, safety, legal duty, cost, demand, or evidence quality reopens the decision.

## Verification

Verification covers identity continuity, formulas, effective dating, duplicate handling, allocation-once behavior, and balanced batches. Evidence is produced during delivery.
