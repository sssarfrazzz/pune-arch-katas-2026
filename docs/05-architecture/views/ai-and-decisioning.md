# AI and Decisioning View

| Field | Value |
|---|---|
| Document ID | ARCH-010 |
| Status | Draft |
| Date | 2026-09-15 |
| Implementation | Planned |
| Source | [Solution Overview](../../../solution-overview-15thSept.md) |

```mermaid
flowchart LR
    Evidence[Governed Evidence] --> Deterministic[Deterministic Rules]
    Deterministic -->|critical| Alert[Critical Alert]
    Evidence --> AI[Approved AI Capability]
    AI --> Package[Recommendation Evidence Package]
    Package --> Policy[Deterministic Policy Gate]
    Policy -->|consequential| Human[Authorized Human Decision]
    Policy -->|approved low-risk catalog| Execute[Reversible Software Action]
    Human -->|approved| Execute
    Human -->|rejected| Retain[Retain Case and Evidence]
    Execute --> Outcome[Outcome Evidence]
    Outcome --> Evaluation[Evaluation and Drift Monitoring]
    Evaluation -->|threshold breach| Disable[Disable or Roll Back]
```

## Decision Precedence

1. Independent certified safety status and deterministic safety/welfare policy.
2. Authorized professional decision.
3. Governed AI recommendation.
4. Commercial or optimization preference.

Lower levels cannot override higher levels.

## Isolation

Natural-language input is isolated and sanitized before model processing. Model output cannot invoke consequential tools directly. The action executor accepts only a versioned policy decision, authorized identity where required, and a declared action catalog entry.

## Failure Modes

| Failure | Response |
|---|---|
| Model/provider unavailable | Deterministic or staff-operated fallback. |
| Missing or stale evidence | No approval; request evidence or human review. |
| Prompt injection or policy breach | Reject, audit, and optionally disable capability. |
| Drift or evaluation threshold breach | Stop promotion or disable/roll back. |
| Judge disagreement | Qualified human review; never default to approval. |

Thresholds and owners remain OI-006. Requirements: FR-020 to FR-022, FR-033, CON-004.
