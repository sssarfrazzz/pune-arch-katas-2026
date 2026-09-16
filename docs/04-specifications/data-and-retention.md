# Data and Retention Specification

| Field | Value |
|---|---|
| Document ID | SPEC-007 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |
| Requirements | FR-002, FR-007, FR-008, FR-015, NFR-004, SEC-009, SEC-012, COM-003, COM-005, CON-005 |

## Data Planes

| Stage | Purpose | Location | Promotion rule |
|---|---|---|---|
| Bronze | Preserve source evidence and provenance. | Estate edge by default | Signed or attributable source; retention policy applies. |
| Silver | Validate, normalize, deduplicate, classify, and link evidence. | Estate edge | Quality, freshness, schema, tenant, estate, and Unit ID checks pass. |
| Gold | Produce governed aggregates and decision/reporting inputs. | Edge and approved cloud targets | Purpose, minimization, consent, authority, and quality policy pass. |

Raw edge vision media remains local by policy. Cloud aggregation receives approved derived Silver or Gold data only.

## Data Classes

| Class | Examples | Default handling | Retention |
|---|---|---|---|
| Critical operational | Alerts, inspection state, certification, mission authority | Prioritized local durability and replay | TBD (Safety and Compliance lead), trigger 2026-09-30 |
| Welfare | Observations, imported results, intervention history | Professional-domain access; immutable history and corrections | TBD (Veterinarian), trigger 2026-09-30 |
| Workforce | Assignment, qualification reference, presence, handover | Shift/unit/purpose-scoped access | TBD (HR administrator), trigger 2026-09-30 |
| Visitor presence | Rotating pseudonymous entry/exit/duration | Minimize, aggregate, do not retain unnecessary trails | OI-010 |
| Financial | Cost allocations, credits, reconciliation, posting references | Finance-domain access and authority provenance | TBD (Finance controller), trigger 2026-09-30 |
| AI assurance | Inputs, outputs, evidence package, versions, evaluation, correction | Capability-scoped immutable audit | TBD (Product owner), trigger 2026-10-15 |
| Fleet | Mission, route, payload, telemetry, video, exception | Estate and mission scoped; safety retention applies | OI-012 |

## Ordering and Correction

- Business occurrence time and ingestion time are retained.
- A late or duplicate item cannot overwrite newer confirmed state.
- Corrections append a linked correction record and preserve original evidence.
- Reprocessing records policy and model versions.
- Data-subject rights are executed without deleting records that must be retained under another lawful obligation; exact jurisdictional rules remain TBD.

## Residency and Transfer

Tenant and estate policy controls storage, backup, model processing, support access, and cross-border transfer. Sovereign-cloud and self-hosted responsibilities are OI-013.

## Verification

VER-003, VER-004, VER-008, and VER-009 cover offline retention, contract handling, privacy controls, and AI provenance. Evidence remains TBD under OI-015.
