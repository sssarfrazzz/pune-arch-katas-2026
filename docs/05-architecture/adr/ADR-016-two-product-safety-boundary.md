# ADR-016: Two-Product Safety Boundary

## Status

Proposed

## Date

2026-09-15

## Context

Operations intelligence and physical actuation have different maturity, certification, liability, and failure consequences but share evidence and approval workflows.

## Decision

Deliver Product 1 and Product 2 on a shared evidence, policy, identity, approval, and audit foundation while keeping Product 2 separately entitled, certified, and activation-gated. Product 2 receives approved mission requests and returns status and evidence; it gains no safety-system control authority.

## Alternatives Considered

- Combine physical actuation into Product 1 by default: rejected because certification and operational risk differ.
- Build unrelated products: rejected because evidence, policy, identity, and audit must remain coherent.
- Activate Product 2 before Product 1 maturity: rejected by the source boundary.

## Consequences

- Product 1 can deliver value before robotics certification.
- Product 2 requires independent commercial, safety, support, and conformance gates.
- Shared contracts must not collapse the safety boundary.

## Related Requirements

BR-007; FR-028; COM-006; CON-007; CON-008.

## Related Risks

[RISK-001](../../06-delivery/risk-register.md), [RISK-002](../../06-delivery/risk-register.md).

## Related Tests

[VER-010 and VER-012](../../06-delivery/verification-plan.md): activation gate, boundary inspection, certification evidence, and operational readiness.