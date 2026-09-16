# Non-Functional Requirements

| Field | Value |
|---|---|
| Document ID | REQ-007 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

| ID | Requirement | Upstream | Verification | Observable evidence | Design / risk |
|---|---|---|---|---|---|
| NFR-001 | Approved critical alerting, animal-care, admission, device, workforce, and dashboard functions MUST operate for 72 continuous hours without cloud connectivity. | BN-003 | Operational Drill | TBD: 72-hour drill record, owner Estate IT administrator, trigger pilot readiness | [Edge View](../05-architecture/views/edge-and-connectivity.md); RISK-004 |
| NFR-002 | A valid critical local observation MUST raise an edge alert within 10 seconds. | BN-003 | Simulation | TBD: timestamp trace, owner Safety and Compliance lead, trigger pilot readiness | [Edge View](../05-architecture/views/edge-and-connectivity.md); RISK-004 |
| NFR-003 | Responsible central staff MUST receive a valid critical alert within 60 seconds when cloud connectivity is available. | BN-003 | System Test | TBD: end-to-end trace, owner Safety and Compliance lead, trigger pilot readiness | [Architecture Overview](../05-architecture/architecture-overview.md); RISK-004 |
| NFR-004 | Routine telemetry MUST reach the cloud within four hours when a cloud route is available. | BN-003 | Metric Validation | TBD: latency percentile report, owner Estate IT administrator, trigger pilot readiness | [Data View](../05-architecture/views/data-and-integration.md); RISK-004 |
| NFR-005 | The platform MUST permit zero unauthorized cross-tenant reads, writes, events, logs, cache hits, metrics, secrets, backups, fleet commands, or support sessions. | BN-004 | Security Review | TBD: isolation test and review report, owner Estate IT administrator, trigger every release | [Security View](../05-architecture/views/security-and-trust.md); RISK-006 |
| NFR-006 | Shared, dedicated, and self-hosted deployments MUST pass the same functional, security, backup, restore, offline, and AI conformance suites. | BN-004 | System Test; Operational Drill | TBD: topology conformance report, owner Product owner, trigger every release | [Tenancy View](../05-architecture/views/deployment-and-tenancy.md); RISK-006 |
| NFR-007 | A baseline estate edge MUST process 50 to 100 derived vision events per second while raw media remains local. | BN-001 | System Test; Metric Validation | TBD: edge throughput and egress report, owner Estate IT administrator, trigger capacity acceptance | [Edge View](../05-architecture/views/edge-and-connectivity.md); RISK-011 |
| NFR-008 | A 3x estate edge MUST process 150 to 300 derived vision events per second. | BN-001 | System Test; Metric Validation | TBD: 3x load report, owner Estate IT administrator, trigger scale gate | [Edge View](../05-architecture/views/edge-and-connectivity.md); RISK-011 |
| NFR-009 | Financial attribution and reconciliation MUST produce no duplicate revenue. | BN-006 | Integration Test | TBD: duplicate-event report, owner Finance controller, trigger finance acceptance | [Unit Economics](../04-specifications/operational-unit-and-economics.md); RISK-009 |
| NFR-010 | Every journal batch MUST balance to zero before authoritative posting. | BN-006 | Integration Test; Inspection | TBD: rejected and accepted batch evidence, owner Finance controller, trigger finance acceptance | [Unit Economics](../04-specifications/operational-unit-and-economics.md); RISK-009 |
| NFR-011 | Loss of one Product 2 receiver hub MUST reduce capacity without removing command, alert, or visibility coverage. | BN-007 | Simulation; Operational Drill | TBD: hub-loss coverage report, owner Safety and Compliance lead, trigger Product 2 certification | [Robotics View](../05-architecture/views/robotics-and-drone-safety.md); RISK-001 |
