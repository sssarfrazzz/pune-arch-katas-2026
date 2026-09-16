# Commercial Engagement Requirements

| Field | Value |
|---|---|
| Document ID | REQ-006 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

| ID | Requirement | Verification | Observable evidence | Design |
| --- | --- | --- | --- | --- |
| FR-030 | Unit Credits, Visitor Coins, and Pass Tokens MUST use separate ledgers, policies, expiry rules, reconciliation, and financial treatment. | Integration Test; Inspection | ledger isolation and reconciliation report, owner Finance controller, trigger commercial release | [Visitor Specification](../../specifications/visitor-commerce-and-engagement.md) |
| FR-031 | Child-facing loyalty, personalization, messaging, and rewards MUST require verified guardian control and consent. | Security Review; System Test | guardian and consent flow report, owner Privacy and Safeguarding lead, trigger commercial release | [Visitor Specification](../../specifications/visitor-commerce-and-engagement.md) |
| FR-032 | The route assistant MUST return a complete ride-and-enclosure catalogue in which every unit is marked included or skipped, every skipped unit has a displayed reason, and every skipped available unit exposes a visitor action that recalculates the itinerary unless a deterministic closure, safety, capacity, or entitlement rule makes it unavailable. | System Test | full-catalogue inclusion/skip classification, reason, visitor-selection, and recalculation report, owner Product owner, trigger route-assistant release | [Visitor Specification](../../specifications/visitor-commerce-and-engagement.md) |
| FR-033 | Welfare-sensitive, child-facing, and public AI-generated content MUST receive the applicable keeper, welfare, safeguarding, and marketing approvals before publication. | System Test; Inspection | publication approval audit, owner Marketing and engagement manager, trigger commercial release | [AI Governance](../../specifications/ai-governance.md) |
| FR-034 | Merchandise transactions MUST use authoritative commerce, payment, inventory, and fulfilment providers. | Integration Test | provider authority and reconciliation report, owner Procurement officer, trigger commercial release | [Integrations](../../specifications/integrations-and-contracts.md) |
| FR-035 | On-estate advertising MUST be labeled, brand-safe, frequency-limited, and subordinate to operational, accessibility, queue, and emergency content. | Inspection; System Test | content-priority and policy report, owner Marketing and engagement manager, trigger commercial release | [Visitor Specification](../../specifications/visitor-commerce-and-engagement.md) |
| FR-036 | Revenue from passes, tokens, packages, merchandise, advertising, sponsorship, and virtual experiences MUST be reconciled before attribution to Operational Units. | Integration Test | source-to-unit reconciliation report, owner Finance controller, trigger finance acceptance | [Unit Economics](../../specifications/operational-unit-and-economics.md) |
| FR-037 | Commercial offers MUST provide equivalent access for visitors who use accessibility alternatives, decline tracking, or do not join loyalty programs. | System Test; Inspection | accessibility and fairness review, owner Privacy and Safeguarding lead, trigger commercial release | [Visitor Specification](../../specifications/visitor-commerce-and-engagement.md) |
| FR-050 | The platform MUST treat a Family or Group Pass as one ticketing purchase that admits multiple people, and MUST count every individual admitted under an individual ticket or a Family or Group Pass as one visitor for occupancy, visitor-minute, and admission-evidence purposes. | Integration Test; Inspection | family/group pass per-person admission and counting report, owner Product owner, trigger commercial release | [Visitor Specification](../../specifications/visitor-commerce-and-engagement.md) |
