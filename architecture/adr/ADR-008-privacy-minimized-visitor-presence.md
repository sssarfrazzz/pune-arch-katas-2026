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

- Continuous named location tracking: available only through a future privacy-governed decision with documented necessity, proportionality, and approval.
- Raw MAC-address capture: rejected explicitly.
- No presence measurement: rejected because visitor-minutes and queues are source capabilities.

## Consequences

- A DPIA, identifier rotation, retention, guardian handling, and accessibility alternatives are required.
- Low-count and stale-data publication policies are required.
- Presence design cannot silently expand into biometric identity.

## Related Requirements

FR-015; FR-016; FR-031; FR-037; FR-050; SEC-012; COM-003; CON-005; CON-006.
