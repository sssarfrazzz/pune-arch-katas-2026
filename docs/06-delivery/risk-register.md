# Risk Register

| Field | Value |
|---|---|
| Document ID | DEL-001 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

Likelihood and impact are baseline assessments for planning, not accepted risk decisions. Owners MUST review them by 2026-09-30 unless a later trigger is stated.

| ID | Description | Likelihood | Impact | Mitigation | Residual Risk | Owner | Requirements / verification |
|---|---|---|---|---|---|---|---|
| RISK-001 | Product 2 certification may be delayed, costly, or unavailable for a hardware, route, payload, action, or jurisdiction. | High | High | Keep Product 2 separately gated; require certification evidence and route diversity before activation. | High | Safety and Compliance lead | BR-007, NFR-011, COM-006; VER-010 |
| RISK-002 | Compromised, spoofed, unsafe, or uncontrolled robot/drone commands could cause physical harm. | Medium | High | Hardware identity, signed missions, allow-listed actions, independent interlocks, safe states, emergency stop, quarantine. | Medium | Safety and Compliance lead | FR-023 to FR-027, SEC-006 to SEC-011, CON-007; VER-010 |
| RISK-003 | External system failure or ambiguous authority could corrupt operational or financial state. | High | High | Field authority registry, versioned adapters, idempotency, inbox/outbox, dead letters, resolution queue, reconciliation. | Medium | Estate IT administrator | BR-006, FR-004, FR-005, FR-034, COM-004, CON-001; VER-004 |
| RISK-004 | WAN, radio, gateway, power, or storage failure could interrupt critical operations or lose evidence. | High | High | Local deterministic operation, overlapping hubs, 72-hour storage, prioritization, replay, safer state, drills. | Medium | Estate IT administrator | BR-003, FR-007, FR-008, FR-014, NFR-001 to NFR-004; VER-003 |
| RISK-005 | Invalid qualifications, fatigue, absence, or re-plan conflicts could leave mandatory work uncovered. | Medium | High | Constraint validation, current qualification sync, versioned diffs, escalation, local handover, human approval. | Medium | Workforce planner | BR-005, FR-012 to FR-014; VER-006 |
| RISK-006 | Tenant leakage, unclear hosting responsibility, or inconsistent topology controls could expose sensitive data. | Medium | High | Tenant context everywhere, no forks, common conformance, least privilege, responsibility matrix, release-blocking isolation tests. | Medium | Estate IT administrator | BR-004, FR-006, NFR-005, NFR-006, SEC-001 to SEC-005; VER-008, VER-011 |
| RISK-007 | Incorrect welfare aggregation or AI interpretation could delay care or imply unsupported clinical authority. | Medium | High | Independent subject history, species-specific approval, deterministic thresholds, human clinical authority, safer-state escalation. | Medium | Veterinarian | BR-002, FR-003, FR-009 to FR-011, CON-004, COM-005; VER-001 |
| RISK-008 | Visitor, child, workforce, or biometric data could be collected or used beyond lawful purpose. | Medium | High | DPIA, minimization, rotation, retention, guardian control, equivalent access, disabled biometrics, access review. | Medium | Privacy and Safeguarding lead | FR-015, FR-016, FR-031, FR-037, SEC-012, COM-003, CON-005, CON-006; VER-007, VER-008 |
| RISK-009 | Incorrect weights, late events, duplicate allocation, cost mapping, or CAPEX policy could misstate unit economics. | High | High | Effective dating, immutable Unit ID, allocate once, idempotency, reconciliation, balanced batches, finance approval. | Medium | Finance controller | FR-001, FR-017 to FR-019, FR-036, NFR-009, NFR-010; VER-005 |
| RISK-010 | AI error, prompt injection, drift, evaluator bias, or weak explanations could cause harmful recommendations or content. | High | High | Versioned harness, deterministic gates, human approval, input isolation, calibration, fallback, staged rollout, rollback. | Medium | Product owner | FR-020 to FR-022, FR-033, CON-004; VER-009 |
| RISK-011 | Unknown gate bursts, sensor counts, storage, provider limits, or multi-estate load could exceed capacity. | High | Medium | Measure baseline, load-test stated 1x/3x/10x scenarios, monitor saturation, revalidate each estate. | Medium | Estate IT administrator | BR-001, NFR-007, NFR-008; VER-011 |
| RISK-012 | Payload contamination, identity mismatch, custody loss, animal disturbance, or unsafe handoff could cause harm. | Medium | High | Controlled zones, identity and seal checks, weight/temperature evidence, positive confirmation, abort and escalation. | Medium | Operations supervisor | FR-029, COM-006; VER-010 |
| RISK-013 | Visitor Coins or Pass Tokens could create unplanned accounting, tax, stored-value, refund, fraud, or consumer obligations. | Medium | High | Separate ledgers, no silent conversion, provider authority, legal/finance review before Pass Token launch. | Medium | Finance controller | FR-030, FR-036, COM-004; VER-005, VER-007 |
| RISK-014 | The all-attractions itinerary obligation may be impossible or unsafe under time, accessibility, closure, and queue constraints. | High | High | Block FR-032; resolve OI-009 before design; prioritize safety and accessibility in any replacement rule. | Medium | Product owner | FR-032; VER-007 blocked |
| RISK-015 | Modular-monolith coupling or data contention could exceed an operational threshold without a decomposition plan. | Medium | Medium | Track coupling, queue depth, contention, estate count, and request rate; approve numeric extraction triggers. | Medium | Product owner | BR-004, NFR-006; VER-011 |

## Review Rules

- Any High residual risk blocks the affected release until an authorized owner records acceptance or stronger mitigation.
- Product 2 cannot accept RISK-001 or RISK-002 without jurisdiction-specific evidence.
- Changes to a mitigation require updates to related requirements, ADRs, verification scenarios, operations, and traceability.
