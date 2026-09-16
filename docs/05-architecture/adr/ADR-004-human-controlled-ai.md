# ADR-004: Human-Controlled AI

## Status

Proposed

## Date

2026-09-15

## Context

AI can prioritize and explain evidence, but safety, welfare, finance, legal, and public decisions require accountable authority.

## Decision

Use AI only for governed findings and recommendations. Apply deterministic policy before execution, require authorized human approval for consequential action, and limit autonomous software action to a declared low-risk reversible catalog.

## Alternatives Considered

- Unrestricted AI agency: rejected because it removes accountable safety and professional authority.
- No AI: rejected because prioritization, forecasting, and content assistance provide stated value.
- AI as sole release judge: rejected because shared-model bias and disagreement require independent controls.

## Consequences

- Every capability requires evaluation, provenance, fallback, rollback, drift monitoring, and audit.
- Human review capacity and professional-domain policy are operational dependencies.
- AI outages do not stop deterministic critical workflows.

## Related Requirements

FR-020 to FR-022; FR-033; CON-004.

## Related Risks

[RISK-010](../../06-delivery/risk-register.md), [RISK-007](../../06-delivery/risk-register.md).

## Related Tests

[VER-009](../../06-delivery/verification-plan.md): evaluation gates, adversarial input, human approval, fallback, drift, and rollback.
