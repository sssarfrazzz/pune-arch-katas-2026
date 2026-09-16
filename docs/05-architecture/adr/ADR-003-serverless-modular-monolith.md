# ADR-003: Serverless Modular Monolith

## Status

Proposed

## Date

2026-09-15

## Context

The product begins at single/few-estate scale and prioritizes low idle cost, maintainability, and operational simplicity while preserving future decomposition.

## Decision

Use serverless cloud services around one modular-monolith product boundary with explicit domain modules. Extract a module only after a measured scaling or independent-deployment trigger is approved.

## Alternatives Considered

- Microservices from inception: rejected due to operational and coordination overhead without evidenced scale.
- Traditional always-on monolith: not selected because the source favors serverless cost behavior.
- Separate product codebases: rejected because editions are entitlement and policy bundles.

## Consequences

- Module boundaries and contracts must be enforced inside one deployment boundary.
- Database contention and coupling require monitoring.
- Numeric extraction triggers and roadmap remain OI-014.

## Related Requirements

BR-004; FR-006; NFR-006.

## Related Risks

[RISK-006](../../06-delivery/risk-register.md), [RISK-015](../../06-delivery/risk-register.md).

## Related Tests

[VER-011](../../06-delivery/verification-plan.md): deployment-profile conformance, coupling inspection, and scaling trigger review.
