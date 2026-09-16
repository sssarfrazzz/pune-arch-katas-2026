# Events and Commands

| Field | Value |
|---|---|
| Document ID | ES-002 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

Names are candidate ubiquitous-language terms. Payload schemas remain `TBD` under OI-005.

| Context | Command | Resulting event | Initiator | Key invariant |
|---|---|---|---|---|
| Edge Telemetry | Register Device | Device Provisioned | Estate IT administrator | Identity is attested before trust. |
| Edge Telemetry | Record Observation | Observation Captured | Device or field colleague | Tenant, estate, unit, source, and time are present. |
| Edge Telemetry | Validate Evidence | Evidence Validated or Evidence Quarantined | Deterministic policy | Late data cannot overwrite newer confirmed state. |
| Intervention | Raise Alert | Critical Alert Raised | Deterministic threshold | AI cannot suppress a valid critical alert. |
| Intervention | Create Intervention | Intervention Created | Policy | Owner and response target are present. |
| Intervention | Accept Intervention | Intervention Accepted | Qualified assignee | Assignment scope and qualification are valid. |
| Intervention | Escalate Intervention | Intervention Escalated | Policy or supervisor | Missed targets do not close the case. |
| Intervention | Verify Recovery | Recovery Verified | Authorized specialist | Return authority is independent where required. |
| Workforce Planning | Publish Plan | Plan Version Published | Workforce planner | Constraints pass before publication. |
| Workforce Planning | Re-plan Operations | Plan Recalculated | Trigger policy | A new version and explained diff are retained. |
| Workforce Planning | Record Handover | Handover Recorded | Field colleague | Shift, unit, and evidence scope are present. |
| Admission | Validate Entitlement | Admission Validated or Admission Rejected | Admissions colleague/system | Anti-replay applies online and offline. |
| Visitor Presence | Record Entry or Exit | Occupancy Updated | Approved counter | Only minimum pseudonymous evidence is retained. |
| Visitor Presence | Publish Queue | Queue Estimate Published | Aggregation policy | Individual movement is not published. |
| Unit Economics | Calculate Credits | Unit Credits Calculated | Scheduled policy | $C_{u,t}=M_{u,t}\times X_{u,t}$. |
| Unit Economics | Allocate Package Revenue | Revenue Allocated | Finance policy | Each eligible amount is allocated once. |
| Integration | Import Authoritative Record | Record Imported | Adapter | Field authority is declared. |
| Integration | Reconcile Records | Reconciliation Completed or Conflict Detected | Scheduled policy | Conflicts enter a resolution queue. |
| AI Governance | Issue Recommendation | Recommendation Issued | Approved AI capability | Required evidence package is complete. |
| AI Governance | Decide Recommendation | Human Decision Recorded | Authorized professional | Consequential decisions are human controlled. |
| AI Governance | Correct Recommendation | Recommendation Corrected | Staff member | Historical evidence remains unchanged. |
| Autonomous Fleet | Authorize Mission | Mission Authorized | Human or approved low-risk policy | Signed mission fields and certification are valid. |
| Autonomous Fleet | Start Mission | Mission Started | Certified asset | Interlocks and authority are active. |
| Autonomous Fleet | Abort Mission | Mission Aborted | Authorized operator or interlock | Abort remains local and independent. |
| Autonomous Fleet | Quarantine Asset | Asset Quarantined | Fleet policy or administrator | Command authority is revoked. |
| Visitor Engagement | Award Coin | Visitor Coin Awarded | Approved campaign | Coin ledger is isolated from credits and tokens. |
| Visitor Engagement | Approve Content | Public Content Approved | Required human roles | Sensitive content cannot self-publish. |

Each event requires a versioned contract, correlation ID, tenant and estate scope where applicable, occurrence time, producer identity, and idempotency key. Exact schemas are [OI-005](../00-governance/assumptions-and-open-items.md).
