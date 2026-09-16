# ADR-006: COTS Authority and Reconciliation

## Status

Proposed

## Date

2026-09-15

## Context

Ticketing, payment, identity, HRMS, payroll, ERP, procurement, inventory, EAM, and clinical systems already own commodity records.

## Decision

Keep external systems authoritative for declared records. Integrate through versioned anti-corruption adapters with least privilege, idempotent delivery, durable inbox/outbox handling, dead letters, owned conflict resolution, and reconciliation.

## Alternatives Considered

- Replace enterprise systems: rejected as an explicit non-goal.
- Shared database integration: rejected because it bypasses contract, authority, and isolation controls.
- Last-write-wins conflict handling: rejected because it can overwrite confirmed authority.

## Consequences

- Each field requires an authority map and contract owner.
- External outages require explicit fallback and reconciliation.
- Detailed contracts, timeouts, and retries remain OI-005.

## Related Requirements

BR-006; FR-004; FR-005; FR-034; COM-004; CON-001; CON-002.

## Related Risks

[RISK-003](../../06-delivery/risk-register.md), [RISK-013](../../06-delivery/risk-register.md).

## Related Tests

[VER-004 and VER-005](../../06-delivery/verification-plan.md): contract, idempotency, conflict, and financial reconciliation.
