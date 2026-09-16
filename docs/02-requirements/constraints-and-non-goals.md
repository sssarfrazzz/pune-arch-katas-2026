# Constraints and Non-Goals

| Field | Value |
|---|---|
| Document ID | REQ-009 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

| ID | Constraint | Verification | Observable evidence | Design / risk |
|---|---|---|---|---|
| CON-001 | The platform MUST NOT replace COTS HRMS, payroll, ERP, procurement, inventory, EAM, tax, or general-ledger engines. | Inspection | TBD: system authority review, owner Estate IT administrator, trigger design approval | [Integrations](../04-specifications/integrations-and-contracts.md); RISK-003 |
| CON-002 | The platform MUST NOT implement a custom public ticketing, marketing-site, or sales-channel engine where an existing offering fits. | Inspection | TBD: solution-scope review, owner Product owner, trigger design approval | [System Specification](../04-specifications/system-specification.md); RISK-003 |
| CON-003 | The platform MUST NOT control certified ride, containment, fire, or life-support systems. | Security Review; Inspection | TBD: interface and privilege review, owner Safety and Compliance lead, trigger safety acceptance | [Architecture Overview](../05-architecture/architecture-overview.md); RISK-002 |
| CON-004 | AI, robots, and drones MUST NOT diagnose, prescribe, authorize treatment, or make clinical welfare decisions. | System Test; Inspection | TBD: prohibited-action report, owner Veterinarian, trigger pilot readiness | [AI Governance](../04-specifications/ai-governance.md); RISK-007 |
| CON-005 | The platform MUST NOT perform unapproved biometric identification, raw MAC-address capture, or continuous visitor or employee location tracking. | Security Review | TBD: data-flow and configuration review, owner Privacy and Safeguarding lead, trigger privacy acceptance | [Data Specification](../04-specifications/data-and-retention.md); RISK-008 |
| CON-006 | Child profiling, association, messaging, and rewards MUST remain disabled without verified guardian control and consent. | Security Review; System Test | TBD: child-flow review, owner Privacy and Safeguarding lead, trigger commercial release | [Visitor Specification](../04-specifications/visitor-commerce-and-engagement.md); RISK-008 |
| CON-007 | Product 2 MUST NOT receive write or control access to independent safety systems. | Security Review; Integration Test | TBD: network and interface evidence, owner Safety and Compliance lead, trigger Product 2 certification | [Robotics View](../05-architecture/views/robotics-and-drone-safety.md); RISK-002 |
| CON-008 | Product 2 MUST NOT activate before Product 1 maturity, proven approval workflows, and applicable certification. | Inspection | TBD: activation gate record, owner Product owner, trigger Product 2 pilot | [Delivery Roadmap](../06-delivery/delivery-roadmap.md); RISK-001 |

These constraints are release gates. Exceptions require a superseding change to the canonical source and, where architectural, a new or superseding ADR.