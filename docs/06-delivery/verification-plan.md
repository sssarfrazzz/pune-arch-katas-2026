# Verification Plan

| Field | Value |
|---|---|
| Document ID | DEL-003 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

All scenarios are planned. No executed evidence exists.

| ID | Scope | Methods | Required observations | Owner | Evidence |
|---|---|---|---|---|---|
| VER-001 | Animal/population identity, welfare visibility, intervention lifecycle | System Test; Simulation; Inspection | History survives movement/device change; threshold creates owned intervention; clinical authority and approved aggregation hold | Veterinarian | EV-001 TBD at pilot readiness |
| VER-002 | Critical alert timing and safer state | Simulation; Metric Validation | Valid alert <=10 seconds locally; central <=60 seconds when connected; stale/missing critical state cannot present availability | Safety and Compliance lead | EV-002 TBD at pilot readiness |
| VER-003 | Edge isolation, storage, synchronization, and replay | Operational Drill; System Test | Approved functions operate 72 hours; routine sync <=4 hours when route exists; duplicates/late data handled; critical evidence preserved | Estate IT administrator | EV-003 TBD at pilot readiness |
| VER-004 | Integration contracts and authority | Integration Test; Inspection | Identity, version, schema, timeout/retry, idempotency, dead letters, authority, conflict queue, and reconciliation conform | Estate IT administrator | EV-004 TBD at integration acceptance |
| VER-005 | Unit identity and financial integrity | Unit Test; Integration Test; Inspection | Unit continuity, formulas, effective dates, allocate once, no duplicate revenue, balanced batch, ledger separation | Finance controller | EV-005 TBD at finance acceptance |
| VER-006 | Workforce planning and offline execution | System Test; Simulation; Operational Drill | Constraints enforced; substitutions/escalation correct; every re-plan versioned; handover and offline replay succeed | Workforce planner | EV-006 TBD at pilot readiness |
| VER-007 | Admission, presence, queues, commerce, children, accessibility | System Test; Security Review; Inspection | Anti-replay, minimization, aggregate queues, guardian controls, separate values, equivalent access, approval gates | Privacy and Safeguarding lead | EV-007 TBD at commercial release; FR-032 blocked by OI-009 |
| VER-008 | Identity, tenant isolation, privacy, secrets, certificates, supply chain | Security Review; Integration Test; Operational Drill | Contextual deny/allow, elevation expiry, no standing access, zero cross-tenant access, secret/certificate lifecycle, signed update rollback | Estate IT administrator | EV-008 TBD at every release candidate |
| VER-009 | AI governance and decision control | System Test; Security Review; Metric Validation | Complete evidence package, deterministic gates, adversarial defense, human approval, judge calibration, drift disable, fallback/rollback | Product owner | EV-009 TBD at each AI release gate |
| VER-010 | Autonomous mission and physical safety | Simulation; Security Review; Operational Drill; Inspection | Certification gate, signed mission, catalog restriction, interlocks, hub loss, lost authority, abort, quarantine, custody, prohibited action | Safety and Compliance lead | EV-010 TBD before Product 2 activation |
| VER-011 | Capacity, portability, and modularity | System Test; Metric Validation; Inspection | 15,000 daily admission target, 1x/3x edge throughput, common topology conformance, monitored extraction triggers | Product owner | EV-011 TBD at scale gate; target start date OI-002 |
| VER-012 | Operational and release readiness | Operational Drill; Inspection | Monitoring, incident, backup/restore, recovery, support, training, rollback, unresolved-risk, and evidence gates pass | Operations supervisor | EV-012 TBD before production release |

## Requirement Allocation

| Scenario | Requirements |
|---|---|
| VER-001 | BR-002; FR-003; FR-009; FR-010; COM-005; CON-004 |
| VER-002 | FR-011; NFR-002; NFR-003 |
| VER-003 | BR-003; FR-007; FR-008; FR-014; NFR-001; NFR-004; SEC-009 |
| VER-004 | BR-006; FR-004; FR-005; FR-034; COM-004; CON-001; CON-002 |
| VER-005 | FR-001; FR-002; FR-017 to FR-019; FR-030; FR-036; NFR-009; NFR-010 |
| VER-006 | BR-005; FR-012; FR-013 |
| VER-007 | BR-001; FR-015; FR-016; FR-031 to FR-037; SEC-012; COM-003; CON-005; CON-006 |
| VER-008 | BR-004; FR-006; FR-022; NFR-005; NFR-006; SEC-001 to SEC-007; SEC-010; SEC-011; COM-001; COM-002; CON-003 |
| VER-009 | FR-020; FR-021; FR-033; CON-004 |
| VER-010 | BR-007; FR-023 to FR-029; NFR-011; SEC-008; SEC-011; COM-006; CON-003; CON-007; CON-008 |
| VER-011 | BR-001; BR-004; NFR-006 to NFR-008 |
| VER-012 | COM-007 and all release-applicable requirements |