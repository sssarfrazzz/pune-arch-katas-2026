# ADR-014: Signed Supply Chain and Fleet Lifecycle

## Status

Proposed

## Date

2026-09-15

## Context

Cloud, edge, model, device, robot, drone, and OEM releases can introduce unsafe or compromised artifacts across remote estates.

## Decision

Track components in SBOMs, produce immutable provenance, sign release artifacts, verify compatibility, deploy in stages, stop on health failure, support rollback, and prohibit fleet updates during active missions. Manage identities from attested provisioning through revocation and decommissioning.

## Alternatives Considered

- Unsigned over-the-air updates: rejected due to substitution and tampering risk.
- Fleet-wide immediate rollout: rejected because it increases blast radius.
- Manual long-lived credentials: rejected because rotation and revocation are required.

## Consequences

- Build, model, firmware, and OEM supply chains share release controls.
- Quarantine and rollback are operational capabilities.
- Tooling/provider selection is TBD because implementation has not begun.

## Related Requirements

SEC-006; SEC-007; SEC-008; SEC-011; FR-025 to FR-027.

## Related Risks

[RISK-002](../../06-delivery/risk-register.md), [RISK-006](../../06-delivery/risk-register.md).

## Related Tests

[VER-008 and VER-010](../../06-delivery/verification-plan.md): identity lifecycle, artifact verification, staged update, rollback, quarantine, and active-mission exclusion.
