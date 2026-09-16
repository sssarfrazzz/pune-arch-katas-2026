# ADR-015: Independent Animal and Population Identity

## Status

Proposed

## Date

2026-09-15

## Context

Animals and managed populations move between enclosures, change groups, and outlive monitoring devices. Welfare history must remain continuous.

## Decision

Represent each individual animal and managed population with an identity independent of Operational Unit and Device IDs. Link enclosure, device, and population relationships with effective dates.

## Alternatives Considered

- Use enclosure identity as animal identity: rejected because movement would fragment history.
- Use monitoring-device identity: rejected because devices are replaceable.
- Aggregate all welfare at enclosure level: rejected because species and individual authority differ.

## Consequences

- Welfare timelines survive movement and equipment replacement.
- Population aggregation needs species-specific veterinary policy.
- Domain subjects never authenticate or receive permissions.

## Related Requirements

BR-002; FR-003; COM-005; CON-004.

## Related Risks

[RISK-007](../../06-delivery/risk-register.md).

## Related Tests

[VER-001](../../06-delivery/verification-plan.md): movement, device replacement, subject history, and approved aggregation behavior.
