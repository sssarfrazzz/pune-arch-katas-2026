# ADR-013: Contextual Access and Privileged Elevation

## Status

Proposed

## Date

2026-09-16

## Context

Role tiers alone cannot safely separate welfare, payroll, finance, device administration, tenant, shift, purpose, and support responsibilities.

## Decision

Combine baseline tiers with tenant, estate, unit, domain, shift, purpose, data-class, and time attributes in a versioned machine-readable policy. Require approved, scoped, reason-coded, time-boxed, and audited elevation for privileged or sensitive access.

## Alternatives Considered

- Role-only access control: rejected because tiers are not blanket grants.
- Standing administrator access: rejected because platform administration does not imply sensitive-data authority.
- Shared support accounts: rejected because attribution and expiry are required.

## Consequences

- Policy decision provenance and quarterly domain-owner review are required.
- Emergency access can be granted without becoming permanent.
- Identity-provider claim mappings are configured in the adapter during implementation.

## Related Requirements

FR-022; SEC-001 to SEC-005; NFR-005.
