# Data and Retention Specification

| Field | Value |
|---|---|
| Document ID | SPEC-007 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |
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
| Critical operational | Alerts, inspection state, and certification | Prioritized local durability and replay | 24 months after event closure; extend for an incident, legal hold, or longer jurisdictional rule |
| Welfare | Observations, imported results, intervention history | Professional-domain access; immutable history and corrections | While the subject record is active and for 7 years after its last activity; extend for a legal hold or longer jurisdictional rule |
| Workforce | Assignment, qualification reference, presence, handover | Shift/unit/purpose-scoped access | 3 years after the assignment or qualification expires; authoritative payroll records remain in HRMS/payroll |
| Visitor presence | Rotating pseudonymous entry/exit/duration | Minimize, aggregate, do not retain unnecessary trails | Raw pseudonymous events: 24 hours after daily reconciliation, extendable to 7 days only for failed reconciliation; de-identified unit aggregates: 24 months; finance evidence: 7 fiscal years without a visitor identifier |
| Financial | Cost allocations, credits, reconciliation, posting references | Finance-domain access and authority provenance | 7 fiscal years after period close; extend for audit, tax, dispute, or legal hold |
| AI assurance | Inputs, outputs, evidence package, versions, evaluation, correction | Capability-scoped immutable audit | 24 months after the decision or capability retirement, whichever is later; extend when linked to an incident, dispute, or regulated record |

Raw edge-vision media is discarded after approved derivation and quality checks and no later than 24 hours after capture. An authorized incident hold may retain a minimum necessary clip under the critical-operational policy. A tenant jurisdiction profile can require a longer period, and a documented privacy or legal assessment can require a shorter period when it does not conflict with a mandatory record obligation.

## Ordering and Correction

- Business occurrence time and ingestion time are retained.
- A late or duplicate item cannot overwrite newer confirmed state.
- Corrections append a linked correction record and preserve original evidence.
- Reprocessing records policy and model versions.
- Data-subject requests use the tenant jurisdiction profile for identity assurance, response deadline, exemptions, and appeal path. The platform deletes or irreversibly de-identifies eligible data, restricts records under legal hold, records the lawful basis for any denied deletion, and preserves only the minimum evidence required to demonstrate the response.

## Residency and Transfer

Tenant and estate policy controls storage, backup, model processing, support access, and cross-border transfer. Deployment responsibility follows the selected jurisdiction and contract.

## Verification

Verification covers offline retention, contract handling, privacy controls, and AI provenance. Evidence is produced during delivery.
