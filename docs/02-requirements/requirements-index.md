# Requirements Index

| Field | Value |
|---|---|
| Document ID | REQ-001 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

## Requirement Sets

| Range | Scope | Artifact |
|---|---|---|
| BR-001 to BR-007 | Business outcomes | [Business Requirements](business-requirements.md) |
| FR-001 to FR-008 | Platform foundation | [Platform Core](functional/platform-core.md) |
| FR-009 to FR-022 | Operations intelligence | [Operations Intelligence](functional/operations-intelligence.md) |
| FR-023 to FR-029 | Autonomous actuation | [Autonomous Actuation](functional/autonomous-actuation.md) |
| FR-030 to FR-037 | Commercial engagement | [Commercial Engagement](functional/commercial-engagement.md) |
| NFR-001 to NFR-011 | Quality attributes and capacity | [Non-Functional Requirements](non-functional-requirements.md) |
| SEC-001 to SEC-012 | Security and privacy | [Security, Privacy, and Compliance](security-privacy-compliance.md) |
| COM-001 to COM-007 | Compliance | [Security, Privacy, and Compliance](security-privacy-compliance.md) |
| CON-001 to CON-008 | Constraints and exclusions | [Constraints and Non-Goals](constraints-and-non-goals.md) |

## Requirement Contract

Every requirement in this baseline:

- uses one stable uppercase identifier and one `MUST` or `MUST NOT` obligation;
- links to an upstream business need or explicit source boundary;
- identifies a permitted verification method and planned observable evidence;
- maps through the [Traceability Matrix](../06-delivery/traceability-matrix.md) to specifications, proposed ADRs, components, risks, and verification scenarios.

No requirement is approved or implemented. All evidence remains `TBD` under [OI-015](../00-governance/assumptions-and-open-items.md).

## Source Conflict

FR-032 preserves the source instruction that every itinerary include every ride and enclosure. Its feasibility conflicts with time, accessibility, availability, and queue constraints. The requirement is blocked by [OI-009](../00-governance/assumptions-and-open-items.md) and MUST NOT drive implementation until resolved.
