# ADR-014: Signed Supply Chain and Device Lifecycle

## Status

Proposed

## Date

2026-09-16

## Context

Cloud, edge, model, device, and OEM releases can introduce unsafe or compromised artifacts across remote estates.

## Decision

Track components in SBOMs, produce immutable provenance, sign release artifacts, verify compatibility, deploy in stages, stop on health failure, support rollback, and manage device identities from attested provisioning through revocation and decommissioning.

## Alternatives Considered

- Unsigned over-the-air updates: rejected due to substitution and tampering risk.
- Immediate estate-wide rollout: rejected because it increases blast radius.
- Manual long-lived credentials: rejected because rotation and revocation are required.

## Consequences

- Build, model, firmware, and OEM supply chains share release controls.
- Device quarantine and rollback are operational capabilities.
- Tool selection is provider-neutral but must emit CycloneDX or SPDX SBOMs, in-toto-compatible provenance, and verifiable signatures; support offline verification at the estate edge; protect signing keys in managed hardware-backed key storage; publish revocation state; and export evidence for the common conformance suite.

## Related Requirements

SEC-006; SEC-007; SEC-009; SEC-011.
