# Integrations and Contracts Specification

| Field | Value |
|---|---|
| Document ID | SPEC-006 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |
| Requirements | BR-006, FR-004, FR-005, FR-034, COM-004, CON-001 to CON-003 |

Every integration uses least-privilege service identity, versioned contracts, idempotency where messages can repeat, durable outbox/inbox handling where asynchronous, dead-letter handling, and reconciliation. Exact schemas, timeouts, retry limits, and named owners are [OI-005](../00-governance/assumptions-and-open-items.md).

| Integration | Owner | Direction | Protocol/style | Data contract | Timeout | Retry | Failure handling | Authority |
|---|---|---|---|---|---|---|---|---|
| Ticketing and commerce | TBD (Estate IT administrator), 2026-10-15 | Bidirectional | Versioned API, signed webhook, entitlement feed | TBD: entitlement/order/refund schema | TBD | TBD bounded, idempotent | Local admission rules, queue, dead letter, reconcile | Provider: sale, order, refund, entitlement; platform: admission evidence |
| Payment provider | TBD (Finance controller), 2026-10-15 | Bidirectional | Hosted checkout, token, signed webhook | TBD: token/payment-status schema | TBD | TBD bounded, idempotent | No raw card fallback; reconcile provider status | Provider: card data and authorization |
| Identity provider | TBD (Estate IT administrator), 2026-10-15 | Provider to platform | OIDC/OAuth 2.0 federation | Standard identity claims plus TBD mappings | TBD | Interactive retry TBD | Deny access when authentication or required claims fail | Provider: workforce identity and authentication |
| Notification provider | TBD (Operations supervisor), 2026-10-15 | Platform to provider; status return | HTTPS API | TBD: intent/status schema | TBD | TBD bounded | Retain intent, expose delivery failure, alternate human workflow | Platform: intent; provider: delivery |
| Veterinary/laboratory | TBD (Veterinarian), 2026-10-15 | Bidirectional | Versioned API or governed file exchange | TBD: diagnosis/result/observation schema | TBD | TBD bounded or scheduled batch | Quarantine invalid records; owned reconciliation | External: imported diagnosis/result; platform: local observation |
| Weather/event data | TBD (Operations supervisor), 2026-10-15 | Provider to platform | HTTPS API or governed file exchange | TBD: forecast/event schema | TBD | TBD bounded | Mark stale/unavailable; deterministic rules continue | External provider |
| Independent safety systems | TBD (Safety and Compliance lead), 2026-10-15 | Safety system to platform only | Isolated read-only interface | TBD: certified status schema | TBD | No command retry; read retry TBD | Treat unavailable/stale state as safer state | Independent safety system |
| Service desk/parts | TBD (Maintenance lead), 2026-10-15 | Bidirectional | Versioned HTTPS API/events | TBD: work/parts schema | TBD | TBD bounded, idempotent | Resolution queue and manual escalation | Contracted system by record |
| HRMS/payroll | TBD (HR administrator), 2026-10-15 | Bidirectional | Versioned API/events/files | TBD: person/employment/qualification/payroll reference | TBD | TBD bounded or scheduled batch | Preserve local plan, flag stale qualifications, reconcile | HRMS/payroll |
| ERP/procurement/inventory/EAM | TBD (Finance controller), 2026-10-15 | Bidirectional | Versioned API/events/files | TBD: purchase/inventory/asset/work/cost/accounting schema | TBD | TBD bounded or scheduled batch | Resolution queue; block unbalanced posting | ERP/EAM by record |

## Contract Envelope

Every asynchronous contract MUST include contract version, message ID, idempotency key, correlation and causation IDs, tenant and estate scope, producer identity, occurrence time, publication time, payload classification, and integrity metadata.

## Reconciliation

1. Compare local and authoritative records by contract key and version.
2. Apply idempotent confirmed changes.
3. Route authority conflicts, malformed data, and stale updates to a named resolution queue.
4. Retain source payload, provenance, attempted action, error, and resolution.
5. Never silently overwrite confirmed state or promote the platform to payroll, tax, card, or general-ledger authority.

## Verification

VER-004 covers contract conformance, identity, idempotency, dead letters, field authority, failure fallback, and reconciliation. Evidence remains TBD under OI-015.
