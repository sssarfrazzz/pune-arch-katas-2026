# Test Strategy

| Field | Value |
|---|---|
| Document ID | DEL-002 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

This strategy defines future verification. It contains no executable tests and claims no results.

## Objectives

1. Demonstrate each requirement through an allowed verification method and observable evidence.
2. Prioritize safety, welfare, privacy, tenant isolation, financial integrity, offline operation, and physical mission controls.
3. Exercise normal, boundary, degraded, adversarial, recovery, and reconciliation conditions.
4. Run equivalent conformance across shared, dedicated, and self-hosted profiles.

## Verification Methods

| Method | Use |
|---|---|
| Unit Test | Deterministic calculations and policy functions when code exists. |
| Integration Test | Versioned contracts, idempotency, authority, reconciliation, and technical boundaries. |
| System Test | End-to-end business behavior, scale, roles, and topology conformance. |
| Simulation | Time, device, radio, mission, welfare, safety, and adverse-condition scenarios. |
| Security Review | Threat, privacy, access, isolation, secrets, supply-chain, and protocol assessment. |
| Operational Drill | WAN isolation, recovery, failover, emergency stop, restore, incident, and runbook execution. |
| Inspection | Documents, approvals, certifications, configurations, audit records, and control mappings. |
| Metric Validation | Production or representative measurements against explicit targets. |

## Test Levels and Ownership

| Level | Scope | Accountable owner | Entry condition | Exit evidence |
|---|---|---|---|---|
| Document conformance | IDs, links, status, traceability, policy completeness | Product owner | Draft baseline exists | Validation report |
| Component and policy | Calculations, state transitions, deterministic rules | Engineering owner TBD, 2026-10-31 | Implemented component exists | Automated and reviewed results |
| Integration | External and internal contracts | Estate IT administrator | Approved contract and environment | Contract and reconciliation report |
| System | Product behavior and capacity | Product owner | Integrated release candidate | Scenario and metric report |
| Security/privacy | Threat controls, isolation, consent, supply chain | Privacy/Safety leads | Architecture and build evidence | Signed review and remediation record |
| Operational | Isolation, recovery, support, incident, mission control | Operations supervisor | Representative estate and runbooks | Drill evidence and actions |
| Certification | Product 2 machinery/aviation/welfare scope | Safety and Compliance lead | Certified candidate and jurisdiction scope | External certification evidence |

## Environments and Data

Tests use synthetic or approved de-identified data by default. Representative animal, child, visitor, payroll, financial, mission, and safety evidence requires purpose approval and minimum access. Production data is not copied into test environments without an approved legal basis and control record.

## Critical Scenarios

- Peak admissions and anti-replay.
- Critical alerts within 10 seconds locally and 60 seconds centrally when connected.
- 72-hour isolation, storage pressure, reconnection, late and duplicate evidence.
- Single-hub loss and Product 2 route diversity.
- Tenant isolation across every listed boundary.
- Financial effective dating, allocation once, duplicate prevention, and zero-balanced batches.
- AI adversarial input, missing evidence, judge disagreement, drift, fallback, and rollback.
- Mission tampering, lost link, emergency stop, quarantine, payload custody, and prohibited actions.
- Backup restore and responsibility-boundary drills.

## Defect and Evidence Policy

A failed safety, welfare, privacy, tenant-isolation, financial-integrity, or Product 2 certification assertion blocks promotion. Evidence records require scenario/version, environment, data provenance, expected and observed results, timestamps, reviewer, defects, and disposition. Missing evidence is failure, not a pass.

Detailed scenarios are in the [Verification Plan](verification-plan.md); gates and evidence status are in [Quality Gates and Evidence](quality-gates-and-evidence.md).
