# Platform Core Requirements

| Field | Value |
|---|---|
| Document ID | REQ-003 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../../solution-overview-15thSept.md) |

| ID | Requirement | Upstream | Verification | Observable evidence | Design / risk |
|---|---|---|---|---|---|
| FR-001 | Every ride and enclosure MUST have one immutable Operational Unit ID that survives renaming, refurbishment, device replacement, operator change, animal movement, and temporary shutdown. | BN-006 | System Test | TBD: identity lifecycle report, owner Product owner, trigger first release candidate | [Unit Economics](../../04-specifications/operational-unit-and-economics.md); RISK-009 |
| FR-002 | Operational evidence MUST be time-linked to the applicable Operational Unit ID. | BN-006 | Integration Test | TBD: evidence-linkage report, owner Product owner, trigger pilot readiness | [Domain Model](../../04-specifications/domain-model.md); RISK-009 |
| FR-003 | Animal and population identities MUST remain independent of enclosure and monitoring-device identities. | BN-001 | System Test | TBD: movement and device-replacement report, owner Animal-care supervisor, trigger pilot readiness | [Domain Model](../../04-specifications/domain-model.md); RISK-007 |
| FR-004 | Every integrated field MUST have one declared authoritative system. | BN-006 | Inspection | TBD: field authority registry, owner Estate IT administrator, trigger contract approval | [Integrations](../../04-specifications/integrations-and-contracts.md); RISK-003 |
| FR-005 | Integration conflicts MUST enter an owned resolution queue without overwriting confirmed state. | BN-006 | Integration Test | TBD: conflict replay report, owner Estate IT administrator, trigger integration acceptance | [Integrations](../../04-specifications/integrations-and-contracts.md); RISK-003 |
| FR-006 | Edition and deployment variation MUST be implemented through tenant entitlement and policy configuration. | BN-004 | System Test | TBD: configuration conformance report, owner Product owner, trigger first release candidate | [Tenancy View](../../05-architecture/views/deployment-and-tenancy.md); RISK-006 |
| FR-007 | Edge data MUST progress through policy-governed Bronze, Silver, and Gold stages before cloud promotion. | BN-003 | Integration Test | TBD: promotion and rejection records, owner Data and insight analyst, trigger pilot readiness | [Data and Retention](../../04-specifications/data-and-retention.md); RISK-004 |
| FR-008 | Routine telemetry MUST synchronize to the cloud no later than four hours after collection when a cloud route is available. | BN-003 | System Test | TBD: synchronization latency report, owner Estate IT administrator, trigger pilot readiness | [Edge View](../../05-architecture/views/edge-and-connectivity.md); RISK-004 |

All risk links resolve through the [Risk Register](../../06-delivery/risk-register.md), and all verification identifiers resolve through the [Traceability Matrix](../../06-delivery/traceability-matrix.md).
