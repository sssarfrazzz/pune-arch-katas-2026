# ADR-007: Immutable Operational Unit Identity

## Status

Proposed

## Date

2026-09-15

## Context

Operational, workforce, maintenance, visitor, capital, and financial evidence needs one stable boundary across physical and naming changes.

## Decision

Assign every ride and enclosure one immutable Operational Unit ID retained across device replacement, refurbishment, renaming, operator change, animal movement, and temporary shutdown.

## Alternatives Considered

- Use device ID: rejected because devices are replaceable.
- Use display name: rejected because names change and are not unique.
- Use animal identity for enclosures: rejected because animals move and retain independent histories.

## Consequences

- Mappings to devices, assets, animals, people, and external records are effective-dated relationships.
- Historical reporting remains stable.
- Unit identity does not create legal or ledger authority.

## Related Requirements

FR-001; FR-002; FR-017; FR-018; FR-047.
