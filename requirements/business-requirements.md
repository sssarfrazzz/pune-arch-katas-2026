# Business Requirements

| Field | Value |
|---|---|
| Document ID | REQ-002 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |

| ID | Requirement | Verification | Observable evidence | Design |
| --- | --- | --- | --- | --- |
| BR-001 | The platform MUST support estate admission and operations for at least 15,000 visitors per day within the source-defined three-year period. | System Test; Metric Validation | dated peak-load and admission report, owner Product owner, trigger first release candidate | [System Specification](../specifications/system-specification.md) |
| BR-002 | The platform MUST provide telemetry-backed welfare deviation and intervention visibility for at least 200 animals across 55 enclosures. | System Test; Metric Validation | coverage and intervention report, owner Animal-care supervisor, trigger pilot readiness | [Domain Model](../specifications/domain-model.md) |
| BR-003 | The platform MUST keep approved critical estate workflows operational during 72 continuous hours of cloud isolation. | Operational Drill | isolation and replay record, owner Estate IT administrator, trigger pilot readiness | [Workforce and Offline Operations](../specifications/workforce-and-offline-operations.md) |
| BR-004 | The platform MUST provide Zoo, Rides, and Combined editions through entitlement and policy configuration without code forks. | System Test; Inspection | cross-edition conformance report, owner Product owner, trigger first release candidate | [Deployment and Tenancy](../architecture/views/deployment-and-tenancy.md) |
| BR-005 | The platform MUST enforce qualification, certification, working-time, rest, staffing-ratio, and unit-availability constraints in operational plans. | System Test; Simulation | planning constraint report, owner Workforce planner, trigger pilot readiness | [Workforce and Offline Operations](../specifications/workforce-and-offline-operations.md) |
| BR-006 | The platform MUST coordinate enterprise operations while preserving each external system's declared record authority. | Integration Test; Inspection | authority and reconciliation report, owner Estate IT administrator, trigger integration acceptance | [Integrations and Contracts](../specifications/integrations-and-contracts.md) |
