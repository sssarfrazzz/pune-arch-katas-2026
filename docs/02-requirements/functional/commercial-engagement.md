# Commercial Engagement Requirements

| Field | Value |
|---|---|
| Document ID | REQ-006 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../../solution-overview-15thSept.md) |

| ID | Requirement | Upstream | Verification | Observable evidence | Design / risk |
|---|---|---|---|---|---|
| FR-030 | Unit Credits, Visitor Coins, and Pass Tokens MUST use separate ledgers, policies, expiry rules, reconciliation, and financial treatment. | BN-006 | Integration Test; Inspection | TBD: ledger isolation and reconciliation report, owner Finance controller, trigger commercial release | [Visitor Specification](../../04-specifications/visitor-commerce-and-engagement.md); RISK-013 |
| FR-031 | Child-facing loyalty, personalization, messaging, and rewards MUST require verified guardian control and consent. | BN-002 | Security Review; System Test | TBD: guardian and consent flow report, owner Privacy and Safeguarding lead, trigger commercial release | [Visitor Specification](../../04-specifications/visitor-commerce-and-engagement.md); RISK-008 |
| FR-032 | Every route-assistant itinerary MUST include all rides and enclosures. | BN-002 | System Test | TBD: feasible acceptance criteria, owner Product owner, trigger resolution of OI-009 | [OI-009](../../00-governance/assumptions-and-open-items.md); RISK-014 |
| FR-033 | Welfare-sensitive, child-facing, and public AI-generated content MUST receive the applicable keeper, welfare, safeguarding, and marketing approvals before publication. | BN-001 | System Test; Inspection | TBD: publication approval audit, owner Marketing and engagement manager, trigger commercial release | [AI Governance](../../04-specifications/ai-governance.md); RISK-010 |
| FR-034 | Merchandise transactions MUST use authoritative commerce, payment, inventory, and fulfilment providers. | BN-006 | Integration Test | TBD: provider authority and reconciliation report, owner Procurement officer, trigger commercial release | [Integrations](../../04-specifications/integrations-and-contracts.md); RISK-003 |
| FR-035 | On-estate advertising MUST be labeled, brand-safe, frequency-limited, and subordinate to operational, accessibility, queue, and emergency content. | BN-002 | Inspection; System Test | TBD: content-priority and policy report, owner Marketing and engagement manager, trigger commercial release | [Visitor Specification](../../04-specifications/visitor-commerce-and-engagement.md); RISK-010 |
| FR-036 | Revenue from passes, tokens, packages, merchandise, advertising, sponsorship, and virtual experiences MUST be reconciled before attribution to Operational Units. | BN-006 | Integration Test | TBD: source-to-unit reconciliation report, owner Finance controller, trigger finance acceptance | [Unit Economics](../../04-specifications/operational-unit-and-economics.md); RISK-009 |
| FR-037 | Commercial offers MUST provide equivalent access for visitors who use accessibility alternatives, decline tracking, or do not join loyalty programs. | BN-002 | System Test; Inspection | TBD: accessibility and fairness review, owner Privacy and Safeguarding lead, trigger commercial release | [Visitor Specification](../../04-specifications/visitor-commerce-and-engagement.md); RISK-008 |

FR-032 is blocked and MUST NOT drive design or delivery until [OI-009](../../00-governance/assumptions-and-open-items.md) is resolved.
