# Delivery Roadmap

| Field | Value |
|---|---|
| Document ID | DEL-004 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

Dates are not invented. Phase scheduling is TBD (Product owner), triggered after baseline approval under OI-001.

| Phase | Scope | Entry gate | Exit gate | Key risks |
|---|---|---|---|---|
| 0. Baseline governance | Approve needs, requirements, terminology, ADRs, risk ownership, verification, and open items | Canonical source available | No unresolved source conflict except explicitly blocked scope; decision owners recorded | RISK-014, RISK-015 |
| 1. Product 1 foundation | Tenant, identity, Unit ID, edge evidence, integration foundation, local coordinator | Phase 0 accepted | Core security, contract, identity, and offline design gates approved | RISK-003, RISK-004, RISK-006 |
| 2. Estate operations pilot | Welfare/intervention, workforce, admission, presence, queues, maintenance, local dashboard | Representative estate and approved DPIA | VER-001 to VER-004, VER-006 to VER-008 evidence meets thresholds | RISK-004, RISK-005, RISK-007, RISK-008 |
| 3. Economics and governed AI | Unit economics, reconciliation, recommendations, commercial capabilities | Finance policies and AI capability records approved | VER-005 and VER-009 pass; no blocked FR-032 dependency | RISK-009, RISK-010, RISK-013, RISK-014 |
| 4. Scale and portable deployment | 15,000 visitors/day, 1x/3x/10x evidence, shared/dedicated/self-hosted conformance | Representative load profiles and responsibilities approved | VER-011 and restore/isolation gates pass | RISK-006, RISK-011, RISK-015 |
| 5. Product 2 controlled pilot | One certified asset/action/route/payload class with human mission supervision | Product 1 maturity evidence, three-path connectivity, jurisdiction approval | VER-010 and VER-012 pass with external certification evidence | RISK-001, RISK-002, RISK-012 |
| 6. Product 2 expansion | Additional certified classes, estates, routes, and payloads | Prior class operational evidence accepted | Each expansion repeats certification, conformance, and operations gates | RISK-001, RISK-002, RISK-012 |

## Promotion Rules

1. A failed safety, welfare, privacy, tenant-isolation, financial-integrity, or certification gate blocks promotion.
2. A High residual risk blocks affected release scope unless the authorized owner records acceptance.
3. Planned architecture cannot be declared implemented without repository evidence and a C4 update.
4. Product 2 cannot use Product 1 commercial pressure to bypass certification or maturity gates.
5. Every phase exit updates traceability and the evidence register.
