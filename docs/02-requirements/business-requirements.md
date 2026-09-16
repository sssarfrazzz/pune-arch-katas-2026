# Business Requirements

| Field | Value |
|---|---|
| Document ID | REQ-002 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

| ID | Requirement | Upstream | Verification | Observable evidence | Downstream / risk |
|---|---|---|---|---|---|
| BR-001 | The platform MUST support estate admission and operations for at least 15,000 visitors per day within the source-defined three-year period. | [BN-002](../01-objectives/business-context.md) | System Test; Metric Validation | TBD: dated peak-load and admission report, owner Product owner, trigger first release candidate | [System Specification](../04-specifications/system-specification.md); [RISK-011](../06-delivery/risk-register.md) |
| BR-002 | The platform MUST provide telemetry-backed welfare deviation and intervention visibility for at least 200 animals across 55 enclosures. | [BN-001](../01-objectives/business-context.md) | System Test; Metric Validation | TBD: coverage and intervention report, owner Animal-care supervisor, trigger pilot readiness | [Domain Model](../04-specifications/domain-model.md); [RISK-007](../06-delivery/risk-register.md) |
| BR-003 | The platform MUST keep approved critical estate workflows operational during 72 continuous hours of cloud isolation. | [BN-003](../01-objectives/business-context.md) | Operational Drill | TBD: isolation and replay record, owner Estate IT administrator, trigger pilot readiness | [Workforce and Offline Operations](../04-specifications/workforce-and-offline-operations.md); [RISK-004](../06-delivery/risk-register.md) |
| BR-004 | The platform MUST provide Zoo, Rides, and Combined editions through entitlement and policy configuration without code forks. | [BN-004](../01-objectives/business-context.md) | System Test; Inspection | TBD: cross-edition conformance report, owner Product owner, trigger first release candidate | [Deployment and Tenancy](../05-architecture/views/deployment-and-tenancy.md); [RISK-006](../06-delivery/risk-register.md) |
| BR-005 | The platform MUST enforce qualification, certification, working-time, rest, staffing-ratio, and unit-availability constraints in operational plans. | [BN-005](../01-objectives/business-context.md) | System Test; Simulation | TBD: planning constraint report, owner Workforce planner, trigger pilot readiness | [Workforce and Offline Operations](../04-specifications/workforce-and-offline-operations.md); [RISK-005](../06-delivery/risk-register.md) |
| BR-006 | The platform MUST coordinate enterprise operations while preserving each external system's declared record authority. | [BN-006](../01-objectives/business-context.md) | Integration Test; Inspection | TBD: authority and reconciliation report, owner Estate IT administrator, trigger integration acceptance | [Integrations and Contracts](../04-specifications/integrations-and-contracts.md); [RISK-003](../06-delivery/risk-register.md) |
| BR-007 | The platform MUST prevent Product 2 activation until Product 1 maturity evidence and applicable hardware, route, payload, action-class, and jurisdiction certifications exist. | [BN-007](../01-objectives/business-context.md) | Inspection; Operational Drill | TBD: activation gate and certification pack, owner Safety and Compliance lead, trigger Product 2 pilot | [Autonomous Missions and Safety](../04-specifications/autonomous-missions-and-safety.md); [RISK-001](../06-delivery/risk-register.md) |
