# Requirements Index

| Field | Value |
|---|---|
| Document ID | REQ-001 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |

This requirements baseline establishes Product 1. Product 2 remains the planned evolution in section 8 of the canonical source, with its requirements defined when administration activates that phase.

## Requirement Sets

| Range | Scope | Artifact |
|---|---|---|
| BR-001 to BR-006 | Business outcomes | [Business Requirements](business-requirements.md) |
| FR-001 to FR-008; FR-049 | Platform foundation | [Platform Core](functional/platform-core.md) |
| FR-009 to FR-022; FR-047, FR-048 | Operations intelligence | [Operations Intelligence](functional/operations-intelligence.md) |
| FR-030 to FR-037; FR-050 | Commercial engagement | [Commercial Engagement](functional/commercial-engagement.md) |
| NFR-001 to NFR-010; NFR-012 | Quality attributes, capacity, and device connectivity interfaces | [Non-Functional Requirements](non-functional-requirements.md) |
| SEC-001 to SEC-007; SEC-009 to SEC-012 | Security and privacy | [Security, Privacy, and Compliance](security-privacy-compliance.md) |
| COM-001 to COM-005; COM-007 | Compliance | [Security, Privacy, and Compliance](security-privacy-compliance.md) |
| CON-001 to CON-006 | Constraints and safeguards | [Constraints and Non-Goals](constraints-and-non-goals.md) |

## Requirement Contract

Every requirement in this baseline:

- uses one stable uppercase identifier and one `MUST` or `MUST NOT` obligation;
- derives from the canonical Solution Overview or an explicit source boundary;
- identifies a permitted verification method and planned observable evidence;
- links to applicable specifications, proposed ADRs, and architecture components.

The active baseline contains 74 planned requirements. Implementation and verification evidence are produced during delivery.

## Round 1 itinerary decision

FR-032 requires the route assistant to keep every ride and enclosure visible, mark each as included or skipped, explain every skip, and let the visitor select any skipped available unit for itinerary recalculation. Deterministic closure, safety, capacity, and entitlement restrictions remain authoritative.
