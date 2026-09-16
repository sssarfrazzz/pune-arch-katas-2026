# Bounded Context Map

| Field | Value |
|---|---|
| Document ID | ES-004 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

```mermaid
flowchart TB
    Telemetry[Edge Telemetry] -->|validated evidence| Unit[Operational Unit]
    Unit --> Intervention[Intervention]
    Animal[Animal and Population] -->|welfare context| Intervention
    Workforce[Workforce Planning] -->|assignments| Intervention
    Admission[Admission] --> Presence[Visitor Presence]
    Presence -->|validated visitor-minutes| Economics[Unit Economics]
    Unit --> Economics
    AI[AI Governance] -->|recommendations only| Intervention
    AI --> Workforce
    Policy[Identity and Policy] --> Unit
    Policy --> Workforce
    Policy --> AI
    Policy --> Fleet[Autonomous Fleet]
    Integration[Integration and Reconciliation] --> Workforce
    Integration --> Economics
    Integration --> Admission
    Entitlement[Tenant and Entitlement] --> Policy
    Entitlement --> Integration
    Engagement[Visitor Engagement] --> Admission
    Engagement --> Economics
    Intervention -->|approved physical request| Fleet
    Fleet -->|status and evidence| Telemetry
```

## Relationships

| Upstream | Downstream | Relationship | Contract status |
|---|---|---|---|
| Edge Telemetry | Operational Unit | Published language: validated evidence | Planned; schema TBD under OI-005 |
| Operational Unit | Intervention | Customer-supplier: scoped unit state | Planned |
| Animal and Population | Intervention | Conformist only for imported clinical facts; local observations remain local authority | Planned |
| Workforce Planning | Intervention | Customer-supplier: qualified assignment | Planned |
| Visitor Presence | Unit Economics | Published language: validated visitor-minute | Planned |
| AI Governance | Operational contexts | Advisory recommendation; no direct consequential mutation | Planned |
| Integration and Reconciliation | External systems | Anti-corruption adapters preserve declared authority | Planned |
| Autonomous Fleet | Independent safety systems | Read-only status with separate safety authority | Planned |

No context is implemented. Boundary ownership must be confirmed before detailed design; owner is TBD (Product owner), trigger date 2026-09-30.
