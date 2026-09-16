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
- Module extraction is considered only when measured scale, reliability, security isolation, or team ownership justifies it.

## Related Requirements

BR-004; FR-006; NFR-006.
