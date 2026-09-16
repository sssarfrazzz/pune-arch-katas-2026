# Policies, Aggregates, and Read Models

| Field | Value |
|---|---|
| Document ID | ES-003 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

| Context | Aggregate | Policy | Read model |
|---|---|---|---|
| Operational Unit | Operational Unit | Identity is immutable; lifecycle decisions remain human governed. | Unit Health and Contribution |
| Animal and Population | Animal; Managed Population | Welfare identity survives movement and device change; clinical authority remains human. | Welfare Timeline |
| Edge Telemetry | Device; Gateway; Evidence Batch | Trust signed sources; quarantine anomalies; promote Bronze to Silver to Gold. | Data Freshness and Coverage |
| Intervention | Intervention | Use Level 1, escalation, Level 2, recovery, and verification; default to safer state. | Intervention Queue |
| Workforce Planning | Operational Plan; Shift | Enforce qualification, rest, staffing, duration, and availability; version every re-plan. | Coverage and Plan Diff |
| Admission | Admission Evidence | Validate entitlement with anti-replay and offline authority. | Gate Status |
| Visitor Presence | Unit Presence Window | Minimize identifiers and publish only aggregate queue information. | Queue and Occupancy |
| Unit Economics | Unit Cost Profile; Credit Ledger; Allocation | Effective-date inputs, allocate package revenue once, and never credit Cost Pools. | Unit Contribution |
| AI Governance | AI Capability; Recommendation; Evaluation Result | Deterministic gates precede execution; human approval governs consequential action. | Capability Assurance |
| Integration | Authority Registry; Resolution Case | One authority per field; idempotent inbox/outbox; no silent overwrite. | Reconciliation Status |
| Identity and Policy | Policy Set; Elevation Session | Contextual least privilege; time-bound elevation; quarterly review. | Access Review |
| Autonomous Fleet | Fleet Asset; Signed Mission | Certified catalog only; independent interlocks; safe state on lost authority. | Fleet Health and Mission Status |
| Visitor Engagement | Coin Ledger; Pass Token Ledger; Content Approval | Guardian and consent gates; separate ledgers; human publication approval. | Visitor Balance and Content Queue |
| Tenant and Entitlement | Tenant; Edition Entitlement | Configuration and policy determine edition and deployment behavior. | Tenant Configuration |

## Cross-Aggregate Rules

1. An Operational Unit links evidence but does not absorb animal identity or external authoritative records.
2. A recommendation does not mutate an Operational Plan, Intervention, financial ledger, or Mission without the applicable policy and approval.
3. Independent safety-system status is read-only and cannot be made subordinate to platform state.
4. Reconciliation creates compensating or resolution work; it does not rewrite confirmed history.
5. Read models can combine contexts for decisions but do not become systems of record.

Implementation boundaries remain planned and are described in [C3 Components](../05-architecture/c4/c3-components.md).
