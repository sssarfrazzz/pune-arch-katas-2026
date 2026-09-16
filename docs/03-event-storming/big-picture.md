# Big-Picture EventStorming

| Field | Value |
|---|---|
| Document ID | ES-001 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

This model is a proposed domain discovery view. It does not assert implemented services or approved event contracts.

```mermaid
flowchart LR
    Observe[Observation Captured] --> Validate[Evidence Validated]
    Validate --> Deviation[Deviation Detected]
    Deviation --> Recommend[Recommendation Issued]
    Recommend --> Policy[Policy Evaluated]
    Policy -->|Consequential| Approval[Human Decision Recorded]
    Policy -->|Low-risk catalog| Execute[Routine Action Executed]
    Approval -->|Approved| Execute
    Approval -->|Rejected| Closed[Case Closed]
    Execute --> Outcome[Outcome Recorded]
    Outcome --> Learn[Evaluation Evidence Added]

    Staff[Staff Absence Recorded] --> Replan[Plan Recalculated]
    Asset[Asset Failure Recorded] --> Replan
    Weather[Weather Change Recorded] --> Replan
    Replan --> Diff[Plan Version Published]

    Entry[Visitor Entry Recorded] --> Presence[Occupancy Updated]
    Presence --> Queue[Queue Estimate Published]
    Presence --> Credits[Unit Credits Calculated]
    Credits --> Revenue[Revenue Allocation Reconciled]

    Approval -. approved physical action .-> Mission[Mission Authorized]
    Mission --> Interlock[Safety Envelope Validated]
    Interlock --> Physical[Physical Mission Executed]
    Physical --> Outcome
```

## Timeline Boundaries

| Phase | Start event | End event | Primary contexts |
|---|---|---|---|
| Observe and respond | Observation Captured | Outcome Recorded | Edge Telemetry, Intervention, Animal and Population, Operational Unit |
| Plan and execute | Trigger Recorded | Plan Version Published | Workforce Planning, Maintenance |
| Visit and attribute | Admission Validated | Revenue Allocation Reconciled | Admission, Visitor Presence, Unit Economics |
| Govern AI | Capability Proposed | Capability Disabled or Promoted | AI Governance, Identity and Policy |
| Execute physical mission | Mission Requested | Mission Accepted or Exception Recorded | Autonomous Fleet, Intervention |

## Pivotal Events

- `CriticalAlertRaised` starts deterministic local escalation.
- `PlanVersionPublished` changes authorized field work.
- `UnitAvailabilityChanged` affects operations, visitors, and attribution.
- `HumanDecisionRecorded` is required before consequential execution.
- `MissionAuthorityLost` requires an independent safe state.
- `ReconciliationConflictDetected` prevents silent source-of-truth overwrite.

Detailed definitions are in [Events and Commands](events-and-commands.md). Conflicts and unvalidated assumptions are in [Hotspots and Open Questions](hotspots-and-open-questions.md).
