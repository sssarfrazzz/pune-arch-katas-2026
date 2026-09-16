# Traceability Matrix

| Field | Value |
|---|---|
| Document ID | DEL-005 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

This matrix provides the bidirectional baseline chain `Business Need -> Requirement -> Design -> ADR -> Planned Component -> Verification -> Risk -> Evidence`. Requirement definitions link back to this artifact through the Requirements Index and their downstream columns.

| Business need | Requirements | Design/specification | ADR | Planned component | Verification | Risk | Evidence |
|---|---|---|---|---|---|---|---|
| BN-001 | BR-002 | [Domain Model](../04-specifications/domain-model.md) | ADR-015 | Animal and Welfare | VER-001 | RISK-007 | EV-001 TBD |
| BN-001 | FR-003, FR-009, FR-010 | [System Specification](../04-specifications/system-specification.md) | ADR-015 | Animal and Welfare; Intervention | VER-001 | RISK-007 | EV-001 TBD |
| BN-001 | FR-011 | [System Specification](../04-specifications/system-specification.md) | ADR-002, ADR-004 | Intervention | VER-002 | RISK-007 | EV-002 TBD |
| BN-001 | FR-020, FR-021, FR-022, FR-033 | [AI Governance](../04-specifications/ai-governance.md) | ADR-004 | AI Governance; Identity and Policy | VER-009 | RISK-010 | EV-009 TBD |
| BN-001 | NFR-007, NFR-008 | [Edge and Connectivity](../05-architecture/views/edge-and-connectivity.md) | ADR-001, ADR-009 | Edge Telemetry | VER-011 | RISK-011 | EV-011 TBD |
| BN-001 | COM-005, CON-004 | [Data and Retention](../04-specifications/data-and-retention.md) | ADR-004, ADR-015 | Animal and Welfare | VER-001 | RISK-007 | EV-001 TBD |
| BN-002 | BR-001 | [System Specification](../04-specifications/system-specification.md) | ADR-002 | Admission and Presence | VER-011 | RISK-011 | EV-011 TBD |
| BN-002 | FR-015, FR-016 | [Visitor Specification](../04-specifications/visitor-commerce-and-engagement.md) | ADR-008 | Admission and Presence | VER-007 | RISK-008 | EV-007 TBD |
| BN-002 | FR-030, FR-031, FR-034, FR-035, FR-036, FR-037 | [Visitor Specification](../04-specifications/visitor-commerce-and-engagement.md) | ADR-006, ADR-008, ADR-011 | Visitor Engagement; Unit Economics | VER-005, VER-007 | RISK-008, RISK-009, RISK-013 | EV-005/EV-007 TBD |
| BN-002 | FR-032 | [Visitor Specification](../04-specifications/visitor-commerce-and-engagement.md) | None pending OI-009 | Route Assistant | VER-007 blocked | RISK-014 | No evidence permitted until resolved |
| BN-002 | SEC-012, COM-003, COM-007, CON-005, CON-006 | [Data and Retention](../04-specifications/data-and-retention.md) | ADR-008 | Identity and Policy; Visitor Presence | VER-007, VER-008, VER-012 | RISK-008 | EV-007/EV-008/EV-012 TBD |
| BN-003 | BR-003 | [Workforce and Offline Operations](../04-specifications/workforce-and-offline-operations.md) | ADR-001, ADR-002 | Edge Telemetry; Workforce Planning | VER-003 | RISK-004 | EV-003 TBD |
| BN-003 | FR-007, FR-008, FR-014 | [Data and Retention](../04-specifications/data-and-retention.md) | ADR-002, ADR-009, ADR-010 | Edge Telemetry; Workforce Planning | VER-003 | RISK-004 | EV-003 TBD |
| BN-003 | NFR-001, NFR-002, NFR-003, NFR-004, SEC-009 | [Edge and Connectivity](../05-architecture/views/edge-and-connectivity.md) | ADR-001, ADR-002, ADR-009 | Local Coordinator; Edge Telemetry | VER-002, VER-003 | RISK-004 | EV-002/EV-003 TBD |
| BN-004 | BR-004, FR-006, NFR-005, NFR-006 | [Deployment and Tenancy](../05-architecture/views/deployment-and-tenancy.md) | ADR-003, ADR-005 | Tenant and Entitlement | VER-008, VER-011 | RISK-006, RISK-015 | EV-008/EV-011 TBD |
| BN-004 | SEC-001, SEC-002, SEC-003, SEC-004, SEC-005 | [Identity and Policy](../04-specifications/identity-access-and-policy.md) | ADR-005, ADR-013 | Identity and Policy | VER-008 | RISK-006 | EV-008 TBD |
| BN-004 | SEC-006, SEC-007, SEC-010, SEC-011 | [Security and Trust](../05-architecture/views/security-and-trust.md) | ADR-013, ADR-014 | Identity and Policy; Fleet Management | VER-008 | RISK-002, RISK-006 | EV-008 TBD |
| BN-004 | COM-001, COM-002 | [Quality Gates](quality-gates-and-evidence.md) | ADR-005, ADR-013 | Governance and Assurance | VER-008, VER-012 | RISK-006 | EV-008/EV-012 TBD |
| BN-005 | BR-005, FR-012, FR-013 | [Workforce and Offline Operations](../04-specifications/workforce-and-offline-operations.md) | ADR-010 | Workforce Planning | VER-006 | RISK-005 | EV-006 TBD |
| BN-006 | BR-006, FR-004, FR-005 | [Integrations and Contracts](../04-specifications/integrations-and-contracts.md) | ADR-006 | Integration and Reconciliation | VER-004 | RISK-003 | EV-004 TBD |
| BN-006 | FR-001, FR-002 | [Operational Unit and Economics](../04-specifications/operational-unit-and-economics.md) | ADR-007 | Operational Unit | VER-005 | RISK-009 | EV-005 TBD |
| BN-006 | FR-017, FR-018, FR-019, NFR-009, NFR-010 | [Operational Unit and Economics](../04-specifications/operational-unit-and-economics.md) | ADR-011 | Unit Economics | VER-005 | RISK-009 | EV-005 TBD |
| BN-006 | COM-004, CON-001, CON-002 | [Integrations and Contracts](../04-specifications/integrations-and-contracts.md) | ADR-006 | Integration and Reconciliation | VER-004 | RISK-003 | EV-004 TBD |
| BN-007 | BR-007, FR-028 | [Autonomous Missions](../04-specifications/autonomous-missions-and-safety.md) | ADR-012, ADR-016 | Autonomous Fleet | VER-010, VER-012 | RISK-001 | EV-010/EV-012 TBD |
| BN-007 | FR-023, FR-024, FR-025, FR-026, FR-027, FR-029 | [Autonomous Missions](../04-specifications/autonomous-missions-and-safety.md) | ADR-012 | Autonomous Fleet | VER-010 | RISK-002, RISK-012 | EV-010 TBD |
| BN-007 | NFR-011, SEC-008 | [Robotics and Drone Safety](../05-architecture/views/robotics-and-drone-safety.md) | ADR-001, ADR-012, ADR-014 | Autonomous Fleet; Edge Telemetry | VER-010 | RISK-001, RISK-002 | EV-010 TBD |
| BN-007 | COM-006, CON-003, CON-007, CON-008 | [Robotics and Drone Safety](../05-architecture/views/robotics-and-drone-safety.md) | ADR-012, ADR-016 | Autonomous Fleet; Independent Safety Boundary | VER-010, VER-012 | RISK-001, RISK-002 | EV-010/EV-012 TBD |

## Coverage Rule

The matrix MUST be updated in the same change as any requirement, ADR, component, verification scenario, risk, or evidence status. Evidence IDs resolve through [Quality Gates and Evidence](quality-gates-and-evidence.md).
