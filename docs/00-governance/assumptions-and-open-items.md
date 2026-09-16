# Assumptions and Open Items

| Field | Value |
|---|---|
| Document ID | GOV-003 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

No item in this register represents an approval. Each `TBD` names an accountable source role and a date that triggers resolution or escalation.

| ID | Type | Description | Owner | Trigger date | Affected artifacts |
|---|---|---|---|---|---|
| OI-001 | Governance | Baseline approval and named artifact approvers are TBD. | Product owner | 2026-09-30 | All artifacts |
| OI-002 | Objective | The three-year visitor target start date and platform attribution are TBD. | Estate executive | 2026-09-30 | OKRs, BR-001 |
| OI-003 | Metric | Welfare intervention, incident, access-safety, and cost targets are TBD. | Animal-care supervisor | 2026-09-30 | OKRs, BR-002 |
| OI-004 | Metric and policy | Workforce coverage targets, substitution targets, and constraint precedence are TBD. | Workforce planner | 2026-09-30 | OKRs, BR-005, FR-012 |
| OI-005 | Integration | Owners, schemas, timeouts, retry limits, and field-level authority maps are TBD. | Estate IT administrator | 2026-10-15 | Integration specification, ADR-006 |
| OI-006 | AI | Capability thresholds, judge tolerance, budgets, schedules, and named owners are TBD. | Product owner | 2026-10-15 | AI specification, ADR-004 |
| OI-007 | Capacity | Sensor counts, gate bursts, storage sizing, RTO, RPO, and fleet-pilot capacity are TBD. | Estate IT administrator | 2026-10-15 | NFRs, architecture views |
| OI-008 | Finance | Unit Credit weights, pricing, allocation, CAPEX, late-event, and profitability policies are TBD. | Finance controller | 2026-09-30 | Economics specification, ADR-011 |
| OI-009 | Conflict | Requiring every itinerary to include every ride and enclosure conflicts with visit duration, accessibility, availability, and queue constraints. | Product owner | 2026-09-30 | Commercial requirements |
| OI-010 | Privacy | RFID DPIA, identifier rotation, retention, guardian handling, alternatives, and movement-trail controls are TBD. | Privacy and Safeguarding lead | 2026-09-30 | SEC requirements, ADR-008 |
| OI-011 | Welfare | Population-welfare aggregation rules require species-specific veterinary approval. | Veterinarian | 2026-09-30 | Operations specification |
| OI-012 | Robotics | Estate and jurisdiction certification, aviation, route, payload, insurance, and operator constraints are TBD. | Safety and Compliance lead | 2026-10-31 | Product 2 requirements, ADR-012 |
| OI-013 | Deployment | FedRAMP, sovereign-cloud, residency, cross-border support, and self-hosted responsibility boundaries are TBD. | Privacy and Safeguarding lead | 2026-10-31 | Tenancy architecture |
| OI-014 | Evolution | Numeric modular-monolith extraction triggers and roadmap are TBD. | Product owner | 2026-10-31 | ADR-003, delivery roadmap |
| OI-015 | Evidence | All verification and certification evidence is TBD because no implementation or executed tests exist. | Product owner | At first implementation release candidate | Verification and evidence records |

## Working Assumptions

| ID | Assumption | Validation owner | Trigger date |
|---|---|---|---|
| ASM-001 | Product 1 precedes Product 2 activation. | Product owner | Before Product 2 planning |
| ASM-002 | External systems remain authoritative for the records identified in the source. | Estate IT administrator | Before contract approval |
| ASM-003 | Architecture documents describe a planned system because no implementation exists. | Product owner | At first code baseline |
