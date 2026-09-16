# Security, Privacy, and Compliance Requirements

| Field | Value |
|---|---|
| Document ID | REQ-008 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../solution-overview-15thSept.md) |

## Security and Privacy

| ID | Requirement | Upstream | Verification | Observable evidence | Design / risk |
|---|---|---|---|---|---|
| SEC-001 | Authorization MUST evaluate tier, estate, unit, domain, shift, purpose, data class, and time attributes. | BN-001 to BN-007 | Security Review | TBD: policy decision matrix, owner Estate IT administrator, trigger security acceptance | [Identity Specification](../04-specifications/identity-access-and-policy.md); RISK-006 |
| SEC-002 | Persona-to-data and persona-to-action permissions MUST be stored in a versioned, machine-readable policy table. | BN-001 to BN-007 | Inspection | TBD: policy schema and version audit, owner Safety and Compliance lead, trigger design approval | [Identity Specification](../04-specifications/identity-access-and-policy.md); RISK-006 |
| SEC-003 | Access permissions MUST undergo review at least quarterly with each accountable domain owner. | BN-001 to BN-007 | Security Review | TBD: quarterly review record, owner Safety and Compliance lead, trigger quarter end | [Identity Specification](../04-specifications/identity-access-and-policy.md); RISK-006 |
| SEC-004 | Emergency and privileged elevation MUST be scoped, approved, time-boxed, reason-coded, and audited. | BN-001 to BN-007 | Security Review | TBD: elevation test and log, owner Estate IT administrator, trigger security acceptance | [Security View](../05-architecture/views/security-and-trust.md); RISK-006 |
| SEC-005 | Standing access to personal, welfare, payroll, fleet-command, and financial data MUST be denied. | BN-001 to BN-007 | Security Review | TBD: standing-access audit, owner Privacy and Safeguarding lead, trigger security acceptance | [Security View](../05-architecture/views/security-and-trust.md); RISK-006 |
| SEC-006 | Reusable secrets MUST NOT be embedded in application, device, robot, or drone firmware or configuration. | BN-003, BN-007 | Security Review | TBD: secret scan report, owner Estate IT administrator, trigger every release | [Security View](../05-architecture/views/security-and-trust.md); RISK-002 |
| SEC-007 | Certificates for devices, gateways, robots, drones, workloads, integrations, and mission signing MUST support automated issuance, rotation, expiry monitoring, and revocation. | BN-003, BN-007 | Security Review; Integration Test | TBD: certificate lifecycle report, owner Estate IT administrator, trigger security acceptance | [Security View](../05-architecture/views/security-and-trust.md); RISK-002 |
| SEC-008 | Robot and drone command channels MUST be mutually authenticated, encrypted, replay-protected, and rate-limited. | BN-007 | Security Review | TBD: protocol security report, owner Safety and Compliance lead, trigger Product 2 certification | [Robotics View](../05-architecture/views/robotics-and-drone-safety.md); RISK-002 |
| SEC-009 | Telemetry MUST be trusted only when signed by a provisioned device identity. | BN-001, BN-003 | Security Review; Integration Test | TBD: spoofing and quarantine report, owner Estate IT administrator, trigger pilot readiness | [Edge View](../05-architecture/views/edge-and-connectivity.md); RISK-004 |
| SEC-010 | OT, robotics, workforce, and cloud networks MUST exchange only allow-listed traffic through defined gateways. | BN-003, BN-007 | Security Review | TBD: segmentation assessment, owner Estate IT administrator, trigger security acceptance | [Security View](../05-architecture/views/security-and-trust.md); RISK-002 |
| SEC-011 | Software updates MUST use signed artifacts, SBOM and compatibility checks, staged rollout, rollback, and active-mission exclusion. | BN-003, BN-007 | Security Review; Operational Drill | TBD: update and rollback evidence, owner Estate IT administrator, trigger release acceptance | [Security View](../05-architecture/views/security-and-trust.md); RISK-002 |
| SEC-012 | Biometric capabilities MUST remain disabled until lawful basis, necessity, proportionality, consent where applicable, residency, retention, and stakeholder approval are documented. | BN-002 | Security Review; Inspection | TBD: DPIA and approval record, owner Privacy and Safeguarding lead, trigger any biometric proposal | [Visitor Specification](../04-specifications/visitor-commerce-and-engagement.md); RISK-008 |

## Compliance

| ID | Requirement | Upstream | Verification | Observable evidence | Design / risk |
|---|---|---|---|---|---|
| COM-001 | The assurance program MUST treat SOC 2 as its first-priority control scope. | BN-004 | Security Review | TBD: scoped control matrix, owner Safety and Compliance lead, trigger assurance planning | [Quality Gates](../06-delivery/quality-gates-and-evidence.md); RISK-006 |
| COM-002 | ISO/IEC 27001 alignment MUST reuse the SOC 2 risk and control catalog. | BN-004 | Inspection | TBD: control crosswalk, owner Safety and Compliance lead, trigger assurance planning | [Quality Gates](../06-delivery/quality-gates-and-evidence.md); RISK-006 |
| COM-003 | Personal-data processing MUST implement applicable lawful-basis, consent, minimization, retention, rights, residency, and transfer controls. | BN-002 | Security Review | TBD: privacy control assessment, owner Privacy and Safeguarding lead, trigger design approval | [Data Specification](../04-specifications/data-and-retention.md); RISK-008 |
| COM-004 | Payment design MUST minimize PCI DSS scope through hosted checkout and tokenized provider integration and MUST undergo periodic scope verification. | BN-006 | Security Review; Inspection | TBD: PCI scope review, owner Finance controller, trigger payment integration acceptance | [Integrations](../04-specifications/integrations-and-contracts.md); RISK-003 |
| COM-005 | Welfare, veterinary, conservation, and heritage records MUST follow the applicable operating jurisdiction's rules. | BN-001 | Inspection | TBD: jurisdiction control mapping, owner Safety and Compliance lead, trigger estate onboarding | [Data Specification](../04-specifications/data-and-retention.md); RISK-007 |
| COM-006 | Each Product 2 class, route, payload, operator model, and safety envelope MUST obtain applicable jurisdiction-specific assessment and certification before activation. | BN-007 | Inspection | TBD: certification pack, owner Safety and Compliance lead, trigger Product 2 activation | [Mission Specification](../04-specifications/autonomous-missions-and-safety.md); RISK-001 |
| COM-007 | Introduction of human clinical data MUST trigger a scoped HIPAA and Business Associate Agreement review before processing begins. | BN-002 | Inspection | TBD: scope decision record, owner Privacy and Safeguarding lead, trigger clinical-data proposal | [Data Specification](../04-specifications/data-and-retention.md); RISK-008 |
