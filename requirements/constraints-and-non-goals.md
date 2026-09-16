# Constraints and Non-Goals

| Field | Value |
|---|---|
| Document ID | REQ-009 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |

| ID | Constraint | Verification | Observable evidence | Design |
| --- | --- | --- | --- | --- |
| CON-001 | The platform MUST NOT replace COTS HRMS, payroll, ERP, procurement, inventory, EAM, tax, or general-ledger engines. | Inspection | system authority review, owner Estate IT administrator, trigger design approval | [Integrations](../specifications/integrations-and-contracts.md) |
| CON-002 | The platform MUST NOT implement a custom public ticketing, marketing-site, or sales-channel engine where an existing offering fits. | Inspection | solution-scope review, owner Product owner, trigger design approval | [System Specification](../specifications/system-specification.md) |
| CON-003 | The platform MUST NOT control certified ride, containment, fire, or life-support systems. | Security Review; Inspection | interface and privilege review, owner Safety and Compliance lead, trigger safety acceptance | [Architecture Overview](../architecture/architecture-overview.md) |
| CON-004 | AI MUST NOT diagnose, prescribe, authorize treatment, or make clinical welfare decisions. | System Test; Inspection | prohibited-action report, owner Veterinarian, trigger pilot readiness | [AI Governance](../specifications/ai-governance.md) |
| CON-005 | The platform MUST NOT perform unapproved biometric identification, raw MAC-address capture, or continuous visitor or employee location tracking. | Security Review | data-flow and configuration review, owner Privacy and Safeguarding lead, trigger privacy acceptance | [Data Specification](../specifications/data-and-retention.md) |
| CON-006 | Child profiling, association, messaging, and rewards MUST remain disabled without verified guardian control and consent. | Security Review; System Test | child-flow review, owner Privacy and Safeguarding lead, trigger commercial release | [Visitor Specification](../specifications/visitor-commerce-and-engagement.md) |

These constraints are release gates. Exceptions require a superseding change to the canonical source and, where architectural, a new or superseding ADR.