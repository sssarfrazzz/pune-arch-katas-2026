# Operations Intelligence Requirements

| Field | Value |
|---|---|
| Document ID | REQ-004 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../../solution-overview-15thSept.md) |

| ID | Requirement | Upstream | Verification | Observable evidence | Design / risk |
|---|---|---|---|---|---|
| FR-009 | A governed threshold breach MUST create an intervention with an owner and response target. | BN-001 | System Test | TBD: threshold-to-intervention records, owner Animal-care supervisor, trigger pilot readiness | [System Specification](../../04-specifications/system-specification.md); RISK-007 |
| FR-010 | Deviations MUST follow the governed Level 1, escalation, Level 2, recovery, and verification lifecycle. | BN-001 | Simulation | TBD: lifecycle scenario report, owner Safety and Compliance lead, trigger pilot readiness | [System Specification](../../04-specifications/system-specification.md); RISK-007 |
| FR-011 | Missing or expired inspection, certification, or critical evidence MUST prevent presentation of an affected ride as available. | BN-003 | System Test | TBD: safer-state scenario report, owner Safety and Compliance lead, trigger pilot readiness | [System Specification](../../04-specifications/system-specification.md); RISK-005 |
| FR-012 | Operational plans MUST evaluate role qualification, certification, working-time, rest, staffing ratio, task duration, unit availability, and equipment availability. | BN-005 | Simulation | TBD: plan constraint report, owner Workforce planner, trigger pilot readiness | [Workforce Specification](../../04-specifications/workforce-and-offline-operations.md); RISK-005 |
| FR-013 | Every re-plan MUST create a new plan version with an explained difference from the prior version. | BN-005 | System Test | TBD: version and diff records, owner Workforce planner, trigger pilot readiness | [Workforce Specification](../../04-specifications/workforce-and-offline-operations.md); RISK-005 |
| FR-014 | Offline execution records MUST synchronize idempotently after connectivity returns. | BN-003 | Integration Test | TBD: replay and duplicate-suppression report, owner Estate IT administrator, trigger pilot readiness | [Workforce Specification](../../04-specifications/workforce-and-offline-operations.md); RISK-004 |
| FR-015 | Visitor-presence collection MUST be limited to the minimum pseudonymous entry, occupancy, exit, and duration evidence required for each unit. | BN-002 | Security Review | TBD: DPIA and data-flow inspection, owner Privacy and Safeguarding lead, trigger design approval | [Visitor Specification](../../04-specifications/visitor-commerce-and-engagement.md); RISK-008 |
| FR-016 | Queue status MUST be published only as an aggregate derived from validated presence and capacity evidence. | BN-002 | System Test | TBD: aggregation and suppression report, owner Product owner, trigger pilot readiness | [Visitor Specification](../../04-specifications/visitor-commerce-and-engagement.md); RISK-008 |
| FR-017 | Every unit MUST have effective-dated Operations Cost, Maintenance Cost, and CAPEX allocations. | BN-006 | Integration Test | TBD: effective-date and reconciliation report, owner Finance controller, trigger finance acceptance | [Unit Economics](../../04-specifications/operational-unit-and-economics.md); RISK-009 |
| FR-018 | Unit Credits MUST equal validated visitor-minutes multiplied by the unit's effective Unit Credit weight for the calculation period. | BN-006 | Unit Test; Metric Validation | TBD: calculation examples and reconciliation report, owner Finance controller, trigger finance acceptance | [Unit Economics](../../04-specifications/operational-unit-and-economics.md); RISK-009 |
| FR-019 | Package revenue MUST be allocated once in proportion to eligible Unit Credits within the governed allocation window. | BN-006 | Unit Test; Integration Test | TBD: duplicate and allocation report, owner Finance controller, trigger finance acceptance | [Unit Economics](../../04-specifications/operational-unit-and-economics.md); RISK-009 |
| FR-020 | Every AI recommendation MUST record source evidence and freshness, applicable rule, model, provider, prompt and policy versions, confidence, uncertainty, material factors, alternatives, and rationale. | BN-001 | Inspection; System Test | TBD: recommendation completeness report, owner Product owner, trigger AI release gate | [AI Governance](../../04-specifications/ai-governance.md); RISK-010 |
| FR-021 | A staff correction to an AI output MUST retain the correction reason without changing historical evidence. | BN-001 | System Test | TBD: correction audit report, owner Product owner, trigger AI release gate | [AI Governance](../../04-specifications/ai-governance.md); RISK-010 |
| FR-022 | Every consequential action MUST require approval by an authorized human in the applicable professional domain. | BN-001 | Security Review; System Test | TBD: denied and approved action report, owner Safety and Compliance lead, trigger pilot readiness | [Identity and Policy](../../04-specifications/identity-access-and-policy.md); RISK-002 |

Risk and verification mappings are maintained in the [Traceability Matrix](../../06-delivery/traceability-matrix.md).
