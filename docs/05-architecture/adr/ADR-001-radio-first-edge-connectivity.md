# ADR-001: Radio-First Edge Connectivity

## Status

Proposed

## Date

2026-09-15

## Context

The estate is large and has patchy Wi-Fi. Product 1 requires low-cost sensing coverage; Product 2 requires resilient command, alert, and visibility paths.

## Decision

Use private LoRaWAN with two overlapping receiver hubs for Product 1. Require a third geographically diverse hub or equivalently independent route before Product 2 activation.

## Alternatives Considered

- Extend Wi-Fi across the estate: rejected as the default because the source identifies patchy coverage and cost constraints.
- Use cellular for every device: not selected; cost, coverage, and power evidence is absent.
- Use one hub: rejected because it creates a visibility failure point.

## Consequences

- Positive: broad low-power coverage and local operation.
- Negative: duty-cycle, congestion, survey, power, and backhaul evidence are required.
- Product 2 remains blocked until diverse-route evidence exists.

## Related Requirements

BR-003; NFR-001; NFR-011; SEC-009.

## Related Risks

[RISK-004](../../06-delivery/risk-register.md), [RISK-001](../../06-delivery/risk-register.md).

## Related Tests

[VER-003 and VER-010](../../06-delivery/verification-plan.md): 72-hour isolation, hub loss, coverage, replay, and Product 2 route diversity.
