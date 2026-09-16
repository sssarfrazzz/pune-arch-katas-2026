# ADR-009: Local Medallion Data Plane

## Status

Proposed

## Date

2026-09-15

## Context

The estate must preserve evidence during WAN loss while limiting cloud transfer to validated, purposeful data.

## Decision

Maintain Bronze, Silver, and Gold data stages at the estate edge. Promote data only after source trust, schema, quality, freshness, tenant, purpose, and minimization controls pass.

## Alternatives Considered

- Send all raw data to cloud: rejected due to connectivity, cost, and privacy constraints.
- Store only processed aggregates: rejected because replay and audit require source evidence.
- Use ungoverned local files: rejected because provenance and quality gates would be inconsistent.

## Consequences

- Edge storage, lineage, policy versions, and replay are first-class capabilities.
- Raw vision media remains local by default.
- Retention and storage-pressure thresholds remain OI-007 and OI-010.

## Related Requirements

FR-007; FR-008; FR-015; NFR-004; SEC-009; COM-003.

## Related Risks

[RISK-004](../../06-delivery/risk-register.md), [RISK-008](../../06-delivery/risk-register.md), [RISK-011](../../06-delivery/risk-register.md).

## Related Tests

[VER-003 and VER-007](../../06-delivery/verification-plan.md): promotion, retention, isolation, replay, and privacy minimization.
