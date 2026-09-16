# Non-Functional Requirements

| Field | Value |
|---|---|
| Document ID | REQ-007 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |

| ID | Requirement | Verification | Observable evidence | Design |
| --- | --- | --- | --- | --- |
| NFR-001 | Approved critical alerting, animal-care, admission, device, workforce, and dashboard functions MUST operate for 72 continuous hours without cloud connectivity. | Operational Drill | 72-hour drill record, owner Estate IT administrator, trigger pilot readiness | [Edge View](../architecture/views/edge-and-connectivity.md) |
| NFR-002 | A valid critical local observation MUST raise an edge alert within 10 seconds. | Simulation | timestamp trace, owner Safety and Compliance lead, trigger pilot readiness | [Edge View](../architecture/views/edge-and-connectivity.md) |
| NFR-003 | Responsible central staff MUST receive a valid critical alert within 60 seconds when cloud connectivity is available. | System Test | end-to-end trace, owner Safety and Compliance lead, trigger pilot readiness | [Architecture Overview](../architecture/architecture-overview.md) |
| NFR-004 | Routine telemetry MUST reach the cloud within four hours when a cloud route is available. | Metric Validation | latency percentile report, owner Estate IT administrator, trigger pilot readiness | [Data View](../architecture/views/data-and-integration.md) |
| NFR-005 | The platform MUST permit zero unauthorized cross-tenant reads, writes, events, logs, cache hits, metrics, secrets, backups, device commands, or support sessions. | Security Review | isolation test and review report, owner Estate IT administrator, trigger every release | [Security View](../architecture/views/security-and-trust.md) |
| NFR-006 | Shared, dedicated, and self-hosted deployments MUST pass the same functional, security, backup, restore, offline, and AI conformance suites. | System Test; Operational Drill | topology conformance report, owner Product owner, trigger every release | [Tenancy View](../architecture/views/deployment-and-tenancy.md) |
| NFR-007 | A baseline estate edge MUST process 50 to 100 derived vision events per second while raw media remains local. | System Test; Metric Validation | edge throughput and egress report, owner Estate IT administrator, trigger capacity acceptance | [Edge View](../architecture/views/edge-and-connectivity.md) |
| NFR-008 | A 3x estate edge MUST process 150 to 300 derived vision events per second. | System Test; Metric Validation | 3x load report, owner Estate IT administrator, trigger scale gate | [Edge View](../architecture/views/edge-and-connectivity.md) |
| NFR-009 | Financial attribution and reconciliation MUST produce no duplicate revenue. | Integration Test | duplicate-event report, owner Finance controller, trigger finance acceptance | [Unit Economics](../specifications/operational-unit-and-economics.md) |
| NFR-010 | Every journal batch MUST balance to zero before authoritative posting. | Integration Test; Inspection | rejected and accepted batch evidence, owner Finance controller, trigger finance acceptance | [Unit Economics](../specifications/operational-unit-and-economics.md) |
| NFR-012 | Provisioned estate devices and gateways MUST expose MQTT, directly or through MQTT-SN bridged at a radio hub or gateway, as the application-layer publish/subscribe interface for telemetry and command traffic, regardless of the underlying radio transport selected in ADR-001. | Integration Test; Inspection | MQTT/MQTT-SN protocol and bridge conformance report, owner Estate IT administrator, trigger integration acceptance | [Edge View](../architecture/views/edge-and-connectivity.md) [ADR-001](../architecture/adr/ADR-001-radio-first-edge-connectivity.md) |
