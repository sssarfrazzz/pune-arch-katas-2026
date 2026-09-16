# Visitor, Commerce, and Engagement Specification

| Field | Value |
|---|---|
| Document ID | SPEC-005 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |
| Requirements | FR-015, FR-016, FR-030 to FR-037, FR-050, SEC-012, COM-003, COM-004 |

## Admission and Presence

The ticketing provider owns sales, orders, refunds, and issued entitlements. The platform owns local admission evidence. Online and offline admission use anti-replay controls and reconcile after reconnection.

Approved RFID or counter sources collect only the pseudonymous entry, occupancy, exit, and duration evidence required to calculate visitor-minutes and aggregate queues. Collection omits raw movement trails and biometrics, and accessible non-tracking alternatives remain available.

## Family and Group Pass

A Family or Group Pass is one ticketing purchase that admits multiple people, such as a day or family pass. The ticketing provider remains authoritative for sale, pricing, and issuance. For estate operations, every individual admitted under a Family or Group Pass is counted as one visitor for occupancy, visitor-minute, and admission-evidence purposes, the same as an individual-ticket holder; a shared purchase never collapses multiple admitted people into a single visitor count. Maximum group size, member age rules, and pricing linkage are TBD (Product owner, trigger 2026-10-15).

## Queue Publication

Queue estimates combine validated entry, occupancy, exit, and capacity evidence. Public output contains aggregate status only. An estimate is publishable when its newest contributing evidence is no more than 5 minutes old, calculated confidence is at least 0.80, and at least 10 pseudonymous observations contribute within the preceding 15 minutes. The minimum-observation rule does not apply to an approved non-identifying people counter. When any applicable threshold fails, the public channel reports `Unavailable` with a stale, low-confidence, or privacy-suppressed reason category and publishes no prior numeric estimate.

## Value Types

| Value | Purpose | Transferability | Authority | Status |
|---|---|---|---|---|
| Unit Credit | Internal management accounting | Non-transferable | Platform calculation under finance policy | Planned |
| Visitor Coin | Promotional loyalty reward | No cash value or transfer by default | Commerce/loyalty provider and platform policy | Planned |
| Pass Token | Prepaid access entitlement | Not cryptocurrency or blockchain | Separate future entitlement ledger | Future |

Separate ledgers, policies, expiry, refund, fraud, reconciliation, and financial treatment apply. No balance converts silently into another.

## Engagement Controls

| Capability | Required control |
|---|---|
| Animal affinity, Virtual Pets, adoption, Grow Together | Verified guardian control for children; approved public facts; no sensitive welfare data or guarantee of access, health, or behavior. |
| Route and queue assistant | Recommendations remain optional and use preferences only with consent. The complete ride and enclosure catalogue remains visible; each unit is marked included or skipped, every skip shows a reason, and a visitor can select any skipped available unit to recalculate the itinerary. Deterministic closure, safety, capacity, and entitlement rules remain authoritative. |
| Social and affinity content | Keeper, welfare, safeguarding, and marketing approval as applicable before publication. |
| Merchandise | Existing commerce, payment, inventory, and fulfilment providers remain authoritative. |
| Digital advertising | Labeled, brand-safe, frequency-limited, and lower priority than operational, accessibility, queue, and emergency content. |

## Payment Boundary

Hosted checkout and tokenized provider integration prevent platform capture of raw card data. The Finance controller verifies PCI DSS scope before payment integration acceptance, at least annually, and after any material change to payment flow, provider, token handling, hosting, or client-side payment code.

## Verification

Verification covers admission, privacy minimization, queue aggregation, guardian control, ledger separation, accessibility equivalence, content approval, complete attraction visibility, skip reasons, visitor selection of skipped available units, itinerary recalculation, and Family or Group Pass per-person admission counting. Evidence is produced during delivery.
