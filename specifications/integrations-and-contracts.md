# Integrations and Contracts Specification

| Field | Value |
|---|---|
| Document ID | SPEC-006 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |
| Requirements | BR-006, FR-004, FR-005, FR-034, COM-004, CON-001 to CON-003 |

Every integration uses least-privilege service identity, versioned contracts, idempotency where messages can repeat, durable outbox/inbox handling where asynchronous, dead-letter handling, and reconciliation. The table defines the integration boundary; detailed schemas and provider transformations are delivery-level adapter configuration.

## Ticketing Platform SLA

The Ticketing Platform owns the ticketing capability and its integration boundary. The baseline standard SLA is 99.9% monthly availability during published operating hours, p95 quote and booking response time below 2 seconds, and priority-1 incident acknowledgement within 15 minutes. Planned maintenance, provider outages, and force majeure follow the agreed service-credit and communication policy.

The SLA covers the platform's APIs, booking workflow, pricing quote handling, entitlement synchronization, and reconciliation. Payment authorization, card-data handling, capture, and refund execution remain dependencies governed by the payment provider's SLA.

| Group | Integration | Owner | Direction | Protocol/style | Failure handling | Authority |
|---|---|---|---|---|---|---|
| Visitor Platform | Ticketing and commerce | Estate IT administrator | Bidirectional | Versioned API, signed webhook, entitlement feed | Process quote acceptance, booking, refund, and webhooks idempotently; hold quote briefly; reject expired or changed prices; queue, dead letter, and reconcile by booking/entitlement version | Provider: catalogue, demand-pricing decision, sale, order, refund, entitlement; platform: admission evidence and operational attribution |
| Visitor Platform | Payment provider | Finance controller | Bidirectional | Hosted checkout, token, signed webhook | Process create, capture, refund, and webhooks idempotently; provide no raw card fallback; keep booking pending until confirmed; reconcile provider status and route mismatches to finance queue | Provider: card data, authorization, capture, and refund; platform: booking/payment association |
| Employee & Workforce | Identity provider | Estate IT administrator | Provider to platform | OIDC/OAuth 2.0 federation | Deny access when authentication or required claims fail | Provider: workforce identity and authentication |
| Visitor Platform | Notification provider | Operations supervisor | Platform to provider; status return | HTTPS API | Retain intent, expose delivery failure, alternate human workflow | Platform: intent; provider: delivery |
| Operations, Safety & Clinical | Veterinary/laboratory | Veterinarian | Bidirectional | Versioned API or governed file exchange | Quarantine invalid records; owned reconciliation | External: imported diagnosis/result; platform: local observation |
| Operations, Safety & Clinical | Weather/event data | Operations supervisor | Provider to platform | HTTPS API or governed file exchange | Mark stale/unavailable; deterministic rules continue | External provider |
| Operations, Safety & Clinical | Independent safety systems | Safety and Compliance lead | Safety system to platform only | Isolated read-only interface | Provide no command path; treat unavailable/stale state as safer state | Independent safety system |
| Maintenance & Enterprise Back Office | Service desk/parts | Maintenance lead | Bidirectional | Versioned HTTPS API/events | Resolution queue and manual escalation | Contracted system by record |
| Employee & Workforce | HRMS/payroll | HR administrator | Bidirectional | Versioned API/events/files | Preserve local plan, flag stale qualifications, reconcile | HRMS/payroll |
| Maintenance & Enterprise Back Office | ERP/procurement/inventory/EAM | Finance controller | Bidirectional | Versioned API/events/files | Resolution queue; block unbalanced posting | ERP/EAM by record |

## Contract Envelope

Every asynchronous contract MUST include contract version, message ID, idempotency key, correlation and causation IDs, tenant and estate scope, producer identity, occurrence time, publication time, payload classification, and integrity metadata.
## Ticketing and Dynamic Pricing Contract

The ticketing provider is the system of record for the public catalogue, booking, pricing, payment-linked order, refund, and issued entitlement. The platform consumes the resulting entitlement and admission data; it does not become a second ticket ledger.

### Booking and quote

`PriceQuote` MUST contain `quoteId`, `tenantId`, `estateId`, requested visit date/time, ticket type, quantity, currency, unit price, subtotal, discounts, taxes or tax reference, total, expiry time, pricing policy version, demand segment or band, and an integrity signature. Quantity MUST be a positive integer, so the same contract supports a single ticket and a bulk booking. Bulk pricing MAY use an approved quantity tier, but the applied tier and policy version MUST be retained with the quote.

`Booking` MUST contain `bookingId`, `quoteId`, customer reference or guest reference, line items, quantity, total, currency, payment status, booking status, created time, and version. A booking is accepted only when its quote is unexpired and the provider confirms the price and capacity atomically. The final price is the quoted price snapshot; later demand changes do not reprice an accepted booking.

### Entitlement and refund

Each issued entitlement MUST contain `entitlementId`, `bookingId`, ticket type, quantity or unique ticket reference, validity window, admission constraints, status, issue time, and version. Refunds MUST reference the booking or entitlement, original payment reference, refund amount, currency, reason code, and provider refund status. Partial refunds MUST identify the affected line item or ticket quantity.

### Payment flow

1. The platform requests a quote and receives an expiring `PriceQuote`.
2. The platform creates a payment intent for the quoted total using the provider's hosted checkout or tokenized reference.
3. The ticketing provider confirms the booking only after payment authorization succeeds.
4. Signed payment and booking webhooks are processed idempotently; the payment provider remains authoritative for payment state.
5. A failed, expired, or disputed payment cannot issue or validate an entitlement. Reconciliation resolves any booking/payment mismatch before admission.

Demand-based price calculation MAY use capacity, visit date/time, season, inventory, and approved demand bands. The contract MUST expose the resulting price, currency, validity, and pricing-policy version, but MUST NOT require the platform to reproduce the provider's pricing algorithm.

## Reconciliation

1. Compare local and authoritative records by contract key and version.
2. Apply idempotent confirmed changes.
3. Route authority conflicts, malformed data, and stale updates to a named resolution queue.
4. Retain source payload, provenance, attempted action, error, and resolution.
5. Never silently overwrite confirmed state or promote the platform to payroll, tax, card, or general-ledger authority.

## Verification

Verification covers contract conformance, identity, idempotency, dead letters, field authority, failure fallback, and reconciliation. Evidence is produced during delivery.
