# Von Digitalis Estates — Non-Functional Requirements

## 1. Purpose and status

These requirements define the quality attributes and operational constraints for the platform. Targets are initial proposals for validation with estate operations, animal-care, safety, finance, and business stakeholders.

Priority: Must = required for the first operational release; Should = required before broad scale-up; Could = later improvement.

## 2. Availability and resilience

| ID | Requirement | Priority |
|---|---|---|
| NFR-001 | Ticket browsing, ticket verification, and admissions shall remain usable during a cloud or Wi-Fi disruption for the agreed offline window. | Must |
| NFR-002 | Estate gateways shall buffer valid device messages locally for at least 72 hours and synchronize them after connectivity returns without loss or duplication. The platform shall pass a tested 72-hour connectivity-isolation and replay exercise. | Must |
| NFR-003 | Safety-critical and animal-welfare alerts shall continue through approved local rules when cloud connectivity is unavailable. | Must |
| NFR-004 | Core ticketing, admissions, and staff workflows shall achieve 99.9% monthly availability excluding planned maintenance. | Should |
| NFR-005 | The platform shall define and test recovery targets of RPO ≤15 minutes for transactional data and RTO ≤4 hours for cloud services. | Must |
| NFR-006 | No single gateway, availability zone, device network segment, or external provider failure shall cause loss of all operational visibility. | Should |

## 3. Performance and capacity

| ID | Requirement | Priority |
|---|---|---|
| NFR-007 | Ticket search and quote responses shall complete within 2 seconds at p95 during normal operation and within 5 seconds at p99 during peak entry periods. | Must |
| NFR-008 | Online payment authorization shall complete within 5 seconds at p95, with clear pending/failure behavior when the payment provider is slow. | Must |
| NFR-009 | Online ticket validation shall return a decision within 2 seconds at p95; offline validation shall return within 1 second at p95. | Must |
| NFR-010 | A critical alert shall be raised locally within 10 seconds of a valid triggering observation where the local device network is available, and shall be visible to the responsible central staff role within 60 seconds when cloud connectivity is available. | Must |
| NFR-011 | The platform shall support 15,000 daily visitors, peak arrival bursts defined during discovery, 40 rides, 55 enclosures, and at least 10 times the initial device population with capacity headroom. | Must |
| NFR-012 | Analytical dashboards shall return standard daily/weekly views within 10 seconds at p95; long-running forecasts shall run asynchronously with progress status. | Should |

## 4. Safety, welfare, and correctness

| ID | Requirement | Priority |
|---|---|---|
| NFR-013 | Ride safety status shall default to the safer state when required inspection, certification, or critical data is missing or expired. | Must |
| NFR-014 | The platform shall never allow an AI result alone to approve ride operation, animal treatment, population correction, financial settlement, or public safety communication. | Must |
| NFR-015 | Critical welfare and safety alerts shall be acknowledged within a configurable target, escalated automatically when not acknowledged, and retain an immutable audit trail. | Must |
| NFR-016 | Animal and maintenance records shall preserve observation time, source, author/device, amendments, attachments, and decision history. | Must |
| NFR-017 | The platform shall make data freshness, uncertainty, missing data, and AI confidence visible wherever they could affect a safety, welfare, or investment decision. | Must |
| NFR-018 | Duplicate, late, or out-of-order device events shall not overwrite a newer confirmed state. | Must |

## 5. Security

| ID | Requirement | Priority |
|---|---|---|
| NFR-019 | All user, staff, gateway, device, and service communication shall use authenticated and encrypted transport. | Must |
| NFR-020 | MQTT devices shall use unique identities and credentials/certificates, least-privilege topics, rotation, revocation, and replay protection. | Must |
| NFR-021 | Access shall be role-based and least-privilege, with stronger authentication for finance, veterinary, safety, refunds, configuration, and AI-promotion actions. | Must |
| NFR-022 | The platform shall protect payment data through tokenization and shall not store raw payment credentials. | Must |
| NFR-023 | Security-relevant actions, including ticket/refund decisions, ride-status changes, welfare amendments, configuration changes, and AI approvals, shall be audited. | Must |
| NFR-024 | The platform shall apply rate limiting, input validation, malware scanning for uploads, secrets management, network segmentation, vulnerability management, and backup protection. | Must |

## 6. Privacy and compliance

| ID | Requirement | Priority |
|---|---|---|
| NFR-025 | The platform shall collect only the visitor, movement, feedback, payment, and staff data required for a declared purpose. | Must |
| NFR-026 | Visitor movement and location analytics shall be aggregated or pseudonymized wherever individual identity is not required, with appropriate consent and notice. | Must |
| NFR-027 | The platform shall support access, correction, deletion, portability, consent withdrawal, retention, and legal-hold workflows for personal data. | Must |
| NFR-028 | Animal welfare, veterinary, staff, finance, and incident records shall have separate access and retention policies. | Must |
| NFR-029 | Data residency, subprocessors, cross-border transfers, accessibility, conservation, animal-welfare, and applicable payment requirements shall be documented for each operating jurisdiction. | Must |
| NFR-030 | Images, video, and visitor feedback used for AI training shall have documented provenance, permission/purpose, retention, and removal procedures. | Should |

## 7. Usability and accessibility

| ID | Requirement | Priority |
|---|---|---|
| NFR-031 | A visitor shall be able to discover a ticket and reach payment in no more than five primary interaction steps on supported mobile and web experiences. | Should |
| NFR-032 | Staff applications shall support outdoor use, large touch targets, readable status/alerts, and offline operation for agreed field workflows. | Must |
| NFR-033 | Visitor-facing digital experiences shall target WCAG 2.2 AA and provide accessible ticket presentation and admission alternatives. | Should |
| NFR-034 | The platform shall support localization of language, currency, date/time, accessibility information, and emergency guidance for operating regions. | Should |
| NFR-035 | Every critical alert shall provide a clear action, severity, owner, timestamp, source, and escalation state. | Must |

## 8. Observability and supportability

| ID | Requirement | Priority |
|---|---|---|
| NFR-036 | Requests, events, device messages, alerts, AI inferences, and human decisions shall carry correlation and provenance metadata. | Must |
| NFR-037 | Operations dashboards shall show ticketing health, admission reconciliation, gateway/device health, message backlog, data freshness, alert latency, and synchronization failures. | Must |
| NFR-038 | The platform shall expose service-level indicators for availability, latency, error rate, offline backlog, alert delivery, ticket validation, and data quality. | Must |
| NFR-039 | Critical failures shall create actionable alerts with runbooks, escalation ownership, and acknowledgement tracking. | Must |
| NFR-040 | Logs and audit records shall be protected from tampering and retained for the period required by legal, financial, welfare, and operational policy. | Must |

## 9. AI quality and governance

| ID | Requirement | Priority |
|---|---|---|
| NFR-041 | Each AI capability shall have a named owner, purpose, risk classification, approved data sources, model/prompt version, evaluation set, threshold, fallback, and rollback procedure. | Must |
| NFR-042 | Pre-release evaluation shall measure task quality, safety, fairness/subgroup performance, latency, cost, robustness, and human acceptance against documented thresholds. | Must |
| NFR-043 | Production monitoring shall detect quality regression, drift, unsafe output, hallucination/grounding failure, bias indicators, latency, cost increase, and provider/model changes. | Must |
| NFR-044 | The platform shall support sampling of AI outputs for human review and capture corrections, overrides, reasons, and downstream outcomes. | Must |
| NFR-045 | The system shall support disabling or rolling back an AI capability independently of core ticketing, admissions, safety, and welfare workflows. | Must |
| NFR-046 | Initial target measures shall include: ≥95% precision for automated animal counting before operational use, ≥90% recall for configured welfare anomalies, ≥90% grounded answers for the visitor assistant, and forecast error thresholds agreed by area and season. | Should |
| NFR-047 | AI inference shall have a per-use-case cost budget and a p95 latency target appropriate to the workflow; safety alerts shall use deterministic fallbacks when the target is exceeded. | Must |

## 10. Maintainability, portability, and cost

| ID | Requirement | Priority |
|---|---|---|
| NFR-048 | Domain services, events, schemas, device adapters, external providers, and model providers shall be replaceable behind documented interfaces. | Should |
| NFR-049 | Deployments shall support automated testing, infrastructure as code, feature flags, progressive rollout, and rollback without interrupting admissions. | Should |
| NFR-050 | Each production service and AI capability shall have an owner, runbook, dependency map, backup/restore procedure, and support contact. | Must |
| NFR-051 | The platform shall report infrastructure, storage, device, data-processing, and AI cost by capability and, where practical, per visitor/order. | Should |
| NFR-052 | Storage shall use retention and tiering policies so high-volume telemetry, media, and raw data do not remain in the most expensive tier unnecessarily. | Should |

## 11. Workforce, integration, and extended operations

| ID | Requirement | Priority / phase |
|---|---|---|
| NFR-053 | Missing mandatory workforce coverage shall be detected and a qualified replacement notification shall be issued within 30 seconds of the schedule/availability change being known. | Must / Phase 1 |
| NFR-054 | Offline staff changes shall use encrypted local storage, versioned records, idempotent synchronization, explicit conflict ownership, and an authorized conflict queue. | Must / Phase 1 |
| NFR-055 | Routine telemetry shall become visible to cloud operational systems within four hours after connectivity is available; the target for normal conditions should be hourly where practical. | Must / Phase 1 |
| NFR-056 | Critical device networks shall use surveyed overlapping receiver coverage or an approved alternate alert route, with congestion, obstruction, gateway-loss, and battery-failure testing. | Must / Phase 1 |
| NFR-057 | Device or equipment software updates shall use signed artifacts, compatibility checks, staged rollout, automatic stop conditions, rollback, and recovery drills. | Should / Phase 2 |
| NFR-058 | Staff privacy controls shall minimize precise location tracking, use duty/task evidence instead of continuous tracking by default, limit retention, and restrict access to authorized roles. | Must / Phase 1 |
| NFR-059 | External stakeholder access shall be purpose-limited, tenant/organization-scoped, time-limited where appropriate, approved, auditable, and revocable. | Should / Phase 2 |
| NFR-060 | If productization is approved, there shall be no cross-tenant access through APIs, events, storage, caches, logs, metrics, secrets, support sessions, or backups. | Should / Later productization |
| NFR-061 | Shared, dedicated, and any supported operator-hosted deployments shall pass the same conformance, security, backup/restore, and AI evaluation suites. | Should / Later productization |
| NFR-062 | Child-linked features shall require verified guardian control, age-appropriate consent, restricted messaging, moderation, withdrawal, and deletion workflows before release. | Must if introduced |
| NFR-063 | Biometric processing shall be disabled by default and shall require documented lawful basis, necessity, proportionality, security, retention, and stakeholder approval before implementation. | Must if proposed |

## 12. Verification approach

| Area | Verification |
|---|---|
| Offline operation | Gateway outage, cloud outage, reconnect, duplicate replay, clock skew, and admission reconciliation tests. |
| Safety/welfare | Rule threshold tests, stale-data tests, alert escalation drills, fail-safe tests, and audit completeness checks. |
| Scale/performance | Peak ticketing/admission load tests, device-message load tests, dashboard query tests, and soak tests. |
| Security/privacy | Threat modeling, penetration testing, device credential rotation, access reviews, deletion tests, and upload scanning tests. |
| AI | Golden-set evaluation, adversarial/edge cases, subgroup analysis, human review agreement, shadow mode, canary, drift simulation, and rollback drills. |
| Resilience | Dependency failure, zone failure, gateway failure, data replay, backup restore, and disaster-recovery exercises. |

## 13. Decisions still required

- Exact offline admission window and the local safety rules that must continue without cloud access.
- Peak arrival rate and device/message volume used for capacity sizing.
- Alert acknowledgement and escalation targets for each safety and welfare class.
- Applicable jurisdictional privacy, payment, accessibility, and animal-welfare obligations.
- Final AI quality thresholds and which use cases may progress from advisory to automated behavior.
- Required retention periods for ticketing, movement, feedback, media, maintenance, and welfare records.
- Whether the four-hour routine telemetry target and hourly aspiration are acceptable for each device class.
- Which local alert route and overlapping coverage are feasible for each estate zone.
- Whether external productization, multi-tenancy, and operator-hosted deployment are part of the business roadmap.
