# ADR-013: Contextual Access and Privileged Elevation

## Status

Proposed

## Date

2026-09-15

## Context

Role tiers alone cannot safely separate welfare, payroll, finance, fleet, tenant, shift, purpose, and support responsibilities.

## Decision

Combine baseline tiers with tenant, estate, unit, domain, shift, purpose, data-class, and time attributes in a versioned machine-readable policy. Require approved, scoped, reason-coded, time-boxed, and audited elevation for privileged or sensitive access.

## Alternatives Considered

- Role-only access control: rejected because tiers are not blanket grants.
- Standing administrator access: rejected because platform administration does not imply sensitive-data authority.
- Shared support accounts: rejected because attribution and expiry are required.

## Consequences

- Policy decision provenance and quarterly domain-owner review are required.
- Emergency access can be granted without becoming permanent.
- Identity-provider claim mappings remain OI-005.

## Related Requirements

FR-022; SEC-001 to SEC-005; NFR-005.

## Related Risks

[RISK-006](../../06-delivery/risk-register.md), [RISK-008](../../06-delivery/risk-register.md).

## Related Tests

[VER-008](../../06-delivery/verification-plan.md): contextual authorization, separation of duties, elevation, expiry, review, and isolation.
