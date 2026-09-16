# Operations Readiness

| Field | Value |
|---|---|
| Document ID | DEL-007 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

## Product 1 Readiness

| Area | Required readiness evidence | Owner | Status |
|---|---|---|---|
| Service ownership | Named owner, support window, escalation, provider contacts | Operations supervisor | TBD, trigger pilot planning |
| Monitoring | Edge/cloud availability, alert latency, freshness, storage, queue, reconciliation, isolation, cost | Estate IT administrator | TBD, trigger implementation |
| Incident response | Safety, welfare, privacy, security, financial, integration, AI, and tenant-isolation playbooks | Safety and Compliance lead | TBD, trigger pilot readiness |
| Offline operation | 72-hour procedures, local authority, storage pressure, clock/time handling, reconnection, conflict resolution | Estate IT administrator | TBD, trigger pilot readiness |
| Backup and restore | Scope, RTO/RPO, immutable copies, restore drill, tenant and estate responsibilities | Estate IT administrator | TBD under OI-007/OI-013 |
| Access operations | Joiner/mover/leaver, quarterly review, emergency elevation, support access, certificate and secret rotation | Estate IT administrator | TBD, trigger security acceptance |
| Integration operations | Contract owner, status, dead letter, retry, reconciliation, provider outage, manual workaround | Estate IT administrator | TBD under OI-005 |
| AI operations | Capability owner, monitoring, thresholds, disable, fallback, rollback, incident and correction flow | Product owner | TBD under OI-006 |
| Finance operations | Period close, recalculation, exception, reconciliation, posting, audit and dispute procedures | Finance controller | TBD under OI-008 |
| Training | Role-specific field, supervisor, specialist, privacy, safety, and support training | Operations supervisor | TBD, trigger pilot readiness |

## Product 2 Additional Readiness

| Area | Required readiness evidence | Owner | Status |
|---|---|---|---|
| Certification | Hardware, firmware, action, route, payload, estate, operator, welfare, machinery, and aviation approvals | Safety and Compliance lead | TBD under OI-012 |
| Mission operations | Request, authorization, preflight, pause, abort, quarantine, custody, acceptance, exception | Operations supervisor | TBD before pilot |
| Emergency control | Local emergency stop, lost-link, safe return/landing, flight termination, responder access | Safety and Compliance lead | TBD before certification |
| Fleet lifecycle | Attestation, commissioning, maintenance, charging, certificate, update, rollback, decommissioning | Estate IT administrator | TBD before pilot |
| Coverage | Three diverse hubs/routes, power, backhaul, obstruction, congestion, failure coverage | Estate IT administrator | TBD before activation |
| Physical incident | Injury, animal disturbance, payload, contamination, intrusion, rogue asset, evidence preservation | Safety and Compliance lead | TBD before activation |

## Release Checklist

- Required ADRs are Accepted or the affected scope is removed.
- All applicable requirements map to passed verification evidence.
- No blocked requirement drives implementation.
- High residual risks have authorized disposition.
- Critical owners, contacts, runbooks, training, rollback, and support are verified.
- Backup/restore and 72-hour isolation drills have current evidence.
- Product 2 remains disabled unless every additional gate passes.

Readiness is verified by VER-012 and recorded as EV-012. Current status is `TBD`; no operational evidence exists.