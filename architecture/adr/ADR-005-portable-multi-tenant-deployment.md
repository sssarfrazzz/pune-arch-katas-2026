# ADR-005: Portable Multi-Tenant Deployment

## Status

Proposed

## Date

2026-09-15

## Context

One product must support Zoo, Rides, and Combined editions across shared SaaS, dedicated hosted, and self-hosted profiles.

## Decision

Use one domain contract, policy schema, audit model, upgrade path, and conformance suite. Express editions and topology differences through tenant entitlement, policy, and deployment configuration rather than code forks.

## Alternatives Considered

- Edition-specific forks: rejected because they fragment controls and upgrades.
- Shared SaaS only: rejected because dedicated and self-hosted profiles are source requirements.
- Separate self-hosted product: rejected because conformance must remain common.

## Consequences

- Tenant identity must propagate across every technical boundary.
- Cross-tenant access is a release-blocking failure.
- Deployment administration selects certification and responsibility controls according to the jurisdiction and contract.

## Related Requirements

BR-004; FR-006; NFR-005; NFR-006; COM-003.
