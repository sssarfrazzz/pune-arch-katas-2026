# Document Control

| Field | Value |
|---|---|
| Document ID | GOV-001 |
| Status | Draft |
| Date | 2026-09-15 |
| Canonical source | [Solution Overview](../../solution-overview-15thSept.md) |

## Authority

The Solution Overview is the canonical source for this documentation baseline. These artifacts decompose that source without claiming implementation, approval, certification, or verification evidence.

Where an artifact conflicts with the canonical source, work on the affected decision stops until the conflict is resolved. Proposed ADRs capture architectural decisions but do not outrank the source until accepted by an authorized decision owner.

## Source Hierarchy

1. Accepted ADRs, when any exist.
2. [Solution Overview](../../solution-overview-15thSept.md).
3. Business and non-functional requirements.
4. Architecture and specifications.
5. Verification, risk, operations, and traceability records.

## Lifecycle

| Status | Meaning |
|---|---|
| Draft | Being developed and not approved |
| Proposed | Submitted for decision |
| Accepted | Approved by an authorized owner |
| Superseded | Replaced by a linked artifact |
| Retired | No longer applicable |

## Artifact Register

| Area | Identifier pattern | Authority | Current state |
|---|---|---|---|
| Business need | `BN-NNN` | Solution Overview | Draft decomposition |
| Requirement | `BR/FR/NFR/SEC/COM/CON-NNN` | Requirements set | Draft |
| Open item | `OI-NNN` | Governance record | Draft |
| Architecture decision | `ADR-NNN` | Accepted ADR when approved | Proposed |
| Risk | `RISK-NNN` | Risk register | Draft |
| Verification scenario | `VER-NNN` | Verification plan | Draft; no executed evidence |
| Objective | `OBJ-NNN` / `KR-NNN` | OKR record | Draft |

## Change Control

Every change MUST identify requirements, architecture, ADR, risk, verification, operations, and traceability impact. Unknown values MUST be recorded in [Assumptions and Open Items](assumptions-and-open-items.md) with an owner role and trigger date.

## Review Record

| Review | Owner | Trigger date | Evidence |
|---|---|---|---|
| Baseline stakeholder approval | TBD (Product owner) | 2026-09-30 | TBD: approved review record |
| Safety and welfare review | TBD (Safety and Compliance lead) | 2026-09-30 | TBD: signed review record |
| Privacy and safeguarding review | TBD (Privacy and Safeguarding lead) | 2026-09-30 | TBD: signed review record |
| Finance and commercial review | TBD (Finance controller) | 2026-09-30 | TBD: signed review record |
