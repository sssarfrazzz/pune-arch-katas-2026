# Visitor, Commerce, and Engagement Specification

| Field | Value |
|---|---|
| Document ID | SPEC-005 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |
| Requirements | FR-015, FR-016, FR-030 to FR-037, SEC-012, COM-003, COM-004 |

## Admission and Presence

The ticketing provider owns sales, orders, refunds, and issued entitlements. The platform owns local admission evidence. Online and offline admission use anti-replay controls and reconcile after reconnection.

Approved RFID or counter sources collect only the pseudonymous entry, occupancy, exit, and duration evidence required to calculate visitor-minutes and aggregate queues. Identifier rotation, retention, DPIA, guardian treatment, and accessible alternatives remain [OI-010](../00-governance/assumptions-and-open-items.md).

## Queue Publication

Queue estimates combine validated entry, occupancy, exit, and capacity evidence. Public output contains aggregate status only. Stale, low-confidence, or privacy-threshold-breaching estimates are withheld or labeled according to a policy that is TBD (Product owner, trigger 2026-09-30).

## Value Types

| Value | Purpose | Transferability | Authority | Status |
|---|---|---|---|---|
| Unit Credit | Internal management accounting | Non-transferable | Platform calculation under finance policy | Planned |
| Visitor Coin | Promotional loyalty reward | No cash value or transfer by default | Commerce/loyalty provider and platform policy | Planned |
| Pass Token | Prepaid access entitlement | Not cryptocurrency or blockchain by default | TBD under OI-008 | Future / blocked pending review |

Separate ledgers, policies, expiry, refund, fraud, reconciliation, and financial treatment apply. No balance converts silently into another.

## Engagement Controls

| Capability | Required control |
|---|---|
| Animal affinity, Virtual Pets, adoption, Grow Together | Verified guardian control for children; approved public facts; no sensitive welfare data or guarantee of access, health, or behavior. |
| Route and queue assistant | Optional recommendations, consented preferences, accessible and safe routes, deterministic closure rules. The all-attractions obligation is blocked by OI-009. |
| Social and affinity content | Keeper, welfare, safeguarding, and marketing approval as applicable before publication. |
| Merchandise | Existing commerce, payment, inventory, and fulfilment providers remain authoritative. |
| Digital advertising | Labeled, brand-safe, frequency-limited, and lower priority than operational, accessibility, queue, and emergency content. |

## Payment Boundary

Hosted checkout and tokenized provider integration prevent platform capture of raw card data. PCI scope verification is periodic; cadence is TBD (Finance controller, trigger payment integration acceptance).

## Verification

VER-007 covers admission, privacy minimization, queue aggregation, guardian control, ledger separation, accessibility equivalence, and content approval. FR-032 has no executable acceptance baseline until OI-009 is resolved.