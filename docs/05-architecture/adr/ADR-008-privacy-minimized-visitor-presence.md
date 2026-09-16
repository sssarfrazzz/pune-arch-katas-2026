# ADR-008: Privacy-Minimized Visitor Presence

## Status

Proposed

## Date

2026-09-15

## Context

The platform needs visitor-minutes and queue estimates without covert surveillance or unnecessary movement trails.

## Decision

Collect minimum pseudonymous entry, occupancy, exit, and duration evidence through approved RFID or counters at the edge. Publish aggregate queue status only; keep biometric identification disabled behind separate legal and approval gates.

## Alternatives Considered

- Continuous named location tracking: rejected as disproportionate and outside scope.
- Raw MAC-address capture: rejected explicitly.
- No presence measurement: rejected because visitor-minutes and queues are source capabilities.

## Consequences

- A DPIA, identifier rotation, retention, guardian handling, and accessibility alternatives are required.
- Low-count and stale-data publication policies are required.
- Presence design cannot silently expand into biometric identity.

## Related Requirements

FR-015; FR-016; FR-031; FR-037; SEC-012; COM-003; CON-005; CON-006.

## Related Risks

[RISK-008](../../06-delivery/risk-register.md), [RISK-014](../../06-delivery/risk-register.md).

## Related Tests

[VER-007 and VER-008](../../06-delivery/verification-plan.md): minimization, aggregation, consent, guardian, and privacy review.