# Platform Core Requirements

| Field | Value |
|---|---|
| Document ID | REQ-003 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

| ID | Requirement | Verification | Observable evidence | Design |
| --- | --- | --- | --- | --- |
| FR-001 | Every ride and enclosure MUST have one immutable Operational Unit ID that survives renaming, refurbishment, device replacement, operator change, animal movement, and temporary shutdown. | System Test | identity lifecycle report, owner Product owner, trigger first release candidate | [Unit Economics](../../specifications/operational-unit-and-economics.md) |
| FR-002 | Operational evidence MUST be time-linked to the applicable Operational Unit ID. | Integration Test | evidence-linkage report, owner Product owner, trigger pilot readiness | [Domain Model](../../specifications/domain-model.md) |
| FR-003 | Animal and population identities MUST remain independent of enclosure and monitoring-device identities. | System Test | movement and device-replacement report, owner Animal-care supervisor, trigger pilot readiness | [Domain Model](../../specifications/domain-model.md) |
| FR-004 | Every integrated field MUST have one declared authoritative system. | Inspection | field authority registry, owner Estate IT administrator, trigger contract approval | [Integrations](../../specifications/integrations-and-contracts.md) |
| FR-005 | Integration conflicts MUST enter an owned resolution queue without overwriting confirmed state. | Integration Test | conflict replay report, owner Estate IT administrator, trigger integration acceptance | [Integrations](../../specifications/integrations-and-contracts.md) |
| FR-006 | Edition and deployment variation MUST be implemented through tenant entitlement and policy configuration. | System Test | configuration conformance report, owner Product owner, trigger first release candidate | [Tenancy View](../../architecture/views/deployment-and-tenancy.md) |
| FR-007 | Edge data MUST progress through policy-governed Bronze, Silver, and Gold stages before cloud promotion. | Integration Test | promotion and rejection records, owner Data and insight analyst, trigger pilot readiness | [Data and Retention](../../specifications/data-and-retention.md) |
| FR-008 | Routine telemetry MUST synchronize to the cloud no later than four hours after collection when a cloud route is available. | System Test | synchronization latency report, owner Estate IT administrator, trigger pilot readiness | [Edge View](../../architecture/views/edge-and-connectivity.md) |
| FR-049 | The platform MUST record a population count for each managed population or shared enclosure and flag a discrepancy against the last confirmed count as a governed welfare-evidence category. | System Test; Inspection | population-count discrepancy report, owner Animal-care supervisor, trigger pilot readiness | [Domain Model](../../specifications/domain-model.md) [ADR-015](../../architecture/adr/ADR-015-independent-animal-population-identity.md) |
