# ADR-011: Unit Credit Economics

## Status

Proposed

## Date

2026-09-15

## Context

The estate needs one auditable engagement and attribution model across rides and enclosures without making the platform a general ledger.

## Decision

Calculate Unit Credits from validated visitor-minutes and effective Unit Credit weights. Value standalone credits through an effective price and allocate package revenue once in proportion to eligible credits. Compare attributed revenue with effective operating, maintenance, and CAPEX costs.

## Alternatives Considered

- Attribute all revenue at admission: rejected because it does not represent unit engagement.
- Use raw visit counts: rejected because duration is part of the source model.
- Let AI set prices or weights autonomously: rejected because finance governance retains authority.

## Consequences

- Finance policy versions, effective dates, late-event recalculation, and reconciliation are mandatory.
- Low contribution cannot automatically close a unit.
- Detailed weight, price, CAPEX, zero-denominator, and profitability policy remains OI-008.

## Related Requirements

FR-017 to FR-019; FR-030; FR-036; NFR-009; NFR-010.

## Related Risks

[RISK-009](../../06-delivery/risk-register.md), [RISK-013](../../06-delivery/risk-register.md).

## Related Tests

[VER-005](../../06-delivery/verification-plan.md): formulas, allocation once, effective dates, reconciliation, and balanced posting.
