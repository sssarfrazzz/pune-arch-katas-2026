# ADR-012: Certified Autonomous Missions

## Status

Proposed

## Date

2026-09-15

## Context

Product 2 introduces physical consequences, hostile-command risk, lost connectivity, and jurisdiction-specific machinery and aviation obligations.

## Decision

Execute only signed missions compiled from a certified action catalog and bound to tenant, estate, asset, Unit ID, route, payload, authority, time window, expiry, and abort behavior. Use independent on-asset safety interlocks and local safe-state behavior.

## Alternatives Considered

- Open-ended natural-language missions: rejected because behavior is not bounded or certifiable.
- Cloud-dependent control: rejected because emergency control and lost-link behavior must remain local.
- Platform control of certified safety systems: rejected as an explicit boundary.

## Consequences

- Every hardware, route, payload, action, and operator model needs certification before activation.
- Fleet identity, signing, map/geofence distribution, evidence, quarantine, and emergency drills are required.
- Product 2 remains planned under OI-012.

## Related Requirements

BR-007; FR-023 to FR-029; NFR-011; SEC-008; COM-006; CON-007; CON-008.

## Related Risks

[RISK-001](../../06-delivery/risk-register.md), [RISK-002](../../06-delivery/risk-register.md), [RISK-012](../../06-delivery/risk-register.md).

## Related Tests

[VER-010](../../06-delivery/verification-plan.md): mission validation, interlocks, lost link, abort, quarantine, custody, and prohibited actions.
