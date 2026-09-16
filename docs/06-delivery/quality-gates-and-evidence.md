# Quality Gates and Evidence

| Field | Value |
|---|---|
| Document ID | DEL-006 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

## Gates

| Gate | Criterion | Blocking condition | Owner | Current result |
|---|---|---|---|---|
| QG-001 Source and governance | Canonical source, valid status, owners, conflicts, and change impact are recorded. | Invalid status, hidden conflict, or invented approval/evidence. | Product owner | Draft; OI-001 open |
| QG-002 Requirements | IDs are unique, obligations are atomic/testable, and verification/evidence is identified. | Orphan, duplicate, non-testable obligation, or missing evidence plan. | Product owner | Draft documentation check passed; approval TBD |
| QG-003 Architecture | C1-C4 agree; planned work is labeled; ADRs are decided; integrations are complete. | Planned architecture represented as implemented, unresolved safety conflict, or required ADR not accepted. | Architecture owner TBD, 2026-09-30 | Blocked: ADRs Proposed; implementation absent |
| QG-004 Security and privacy | Tenant isolation, least privilege, DPIA, secrets, certificates, and supply chain pass. | Any unauthorized cross-tenant access or unresolved High exposure. | Privacy and Safeguarding lead | EV-008 TBD |
| QG-005 Offline and resilience | 72-hour operation, alert timing, replay, restore, and hub-loss scenarios pass. | Critical function unavailable or evidence lost/corrupted. | Estate IT administrator | EV-002/EV-003 TBD |
| QG-006 Financial integrity | Effective dating, allocation once, duplicate prevention, reconciliation, and balanced batches pass. | Duplicate attribution or non-zero journal batch. | Finance controller | EV-005 TBD |
| QG-007 AI assurance | Deterministic gates, quality, adversarial, privacy, fairness, fallback, rollback, and human approval pass. | Safety assertion failure, unavailable evidence, or AI-only consequential approval. | Product owner | EV-009 TBD |
| QG-008 Product 2 certification | Maturity, jurisdiction, mission, interlock, route, payload, operator, and emergency evidence pass. | Missing certification, unsafe lost-link behavior, or safety-system write path. | Safety and Compliance lead | Blocked: Product 2 Planned; EV-010 TBD |
| QG-009 Operational readiness | Monitoring, incident, recovery, support, training, ownership, and runbooks pass. | Missing critical owner, drill, rollback, or accepted residual risk. | Operations supervisor | EV-012 TBD |

## Evidence Register

| Evidence ID | Scenario | Required artifact | Owner | Status | Trigger |
|---|---|---|---|---|---|
| EV-001 | VER-001 | Welfare identity/intervention report and approval | Veterinarian | TBD | Pilot readiness |
| EV-002 | VER-002 | Alert latency and safer-state traces | Safety and Compliance lead | TBD | Pilot readiness |
| EV-003 | VER-003 | 72-hour isolation, storage, replay, and recovery record | Estate IT administrator | TBD | Pilot readiness |
| EV-004 | VER-004 | Contract conformance and reconciliation report | Estate IT administrator | TBD | Integration acceptance |
| EV-005 | VER-005 | Unit identity and finance calculation/reconciliation report | Finance controller | TBD | Finance acceptance |
| EV-006 | VER-006 | Workforce constraint and re-plan report | Workforce planner | TBD | Pilot readiness |
| EV-007 | VER-007 | Admission, privacy, guardian, accessibility, and engagement report | Privacy and Safeguarding lead | TBD | Commercial release |
| EV-008 | VER-008 | Security, privacy, isolation, identity, and supply-chain review | Estate IT administrator | TBD | Every release candidate |
| EV-009 | VER-009 | AI evaluation, approval, drift, fallback, and rollback report | Product owner | TBD | Each AI release gate |
| EV-010 | VER-010 | Product 2 certification and mission safety evidence | Safety and Compliance lead | TBD | Before Product 2 activation |
| EV-011 | VER-011 | Capacity and topology conformance report | Product owner | TBD | Scale gate |
| EV-012 | VER-012 | Operational readiness review and drill package | Operations supervisor | TBD | Before production release |

No row can move from `TBD` based on planned design or unexecuted tests. Evidence must identify version, environment, data provenance, expected and observed results, timestamps, reviewer, defects, and disposition.
