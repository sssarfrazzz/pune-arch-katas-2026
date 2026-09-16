# Security, Privacy, and Compliance Requirements

| Field | Value |
|---|---|
| Document ID | REQ-008 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |

## Security and Privacy

| ID | Requirement | Verification | Observable evidence | Design |
| --- | --- | --- | --- | --- |
| SEC-001 | Authorization MUST evaluate tier, estate, unit, domain, shift, purpose, data class, and time attributes. | Security Review | policy decision matrix, owner Estate IT administrator, trigger security acceptance | [Identity Specification](../specifications/identity-access-and-policy.md) |
| SEC-002 | Persona-to-data and persona-to-action permissions MUST be stored in a versioned, machine-readable policy table. | Inspection | policy schema and version audit, owner Safety and Compliance lead, trigger design approval | [Identity Specification](../specifications/identity-access-and-policy.md) |
| SEC-003 | Access permissions MUST undergo review at least quarterly with each accountable domain owner. | Security Review | quarterly review record, owner Safety and Compliance lead, trigger quarter end | [Identity Specification](../specifications/identity-access-and-policy.md) |
| SEC-004 | Emergency and privileged elevation MUST be scoped, approved, time-boxed, reason-coded, and audited. | Security Review | elevation test and log, owner Estate IT administrator, trigger security acceptance | [Security View](../architecture/views/security-and-trust.md) |
| SEC-005 | Standing access to personal, welfare, payroll, and financial data MUST be denied. | Security Review | standing-access audit, owner Privacy and Safeguarding lead, trigger security acceptance | [Security View](../architecture/views/security-and-trust.md) |
| SEC-006 | Reusable secrets MUST NOT be embedded in application or device firmware or configuration. | Security Review | secret scan report, owner Estate IT administrator, trigger every release | [Security View](../architecture/views/security-and-trust.md) |
| SEC-007 | Certificates for devices, gateways, workloads, and integrations MUST support automated issuance, rotation, expiry monitoring, and revocation. | Security Review; Integration Test | certificate lifecycle report, owner Estate IT administrator, trigger security acceptance | [Security View](../architecture/views/security-and-trust.md) |
| SEC-009 | Telemetry MUST be trusted only when signed by a provisioned device identity. | Security Review; Integration Test | spoofing and quarantine report, owner Estate IT administrator, trigger pilot readiness | [Edge View](../architecture/views/edge-and-connectivity.md) |
| SEC-010 | OT, workforce, and cloud networks MUST exchange only allow-listed traffic through defined gateways. | Security Review | segmentation assessment, owner Estate IT administrator, trigger security acceptance | [Security View](../architecture/views/security-and-trust.md) |
| SEC-011 | Software updates MUST use signed artifacts, SBOM and compatibility checks, staged rollout, and rollback. | Security Review; Operational Drill | update and rollback evidence, owner Estate IT administrator, trigger release acceptance | [Security View](../architecture/views/security-and-trust.md) |
| SEC-012 | Biometric capabilities MUST remain disabled until lawful basis, necessity, proportionality, consent where applicable, residency, retention, and stakeholder approval are documented. | Security Review; Inspection | DPIA and approval record, owner Privacy and Safeguarding lead, trigger any biometric proposal | [Visitor Specification](../specifications/visitor-commerce-and-engagement.md) |

## Compliance

| ID | Requirement | Verification | Observable evidence | Design |
| --- | --- | --- | --- | --- |
| COM-001 | The assurance program MUST treat SOC 2 as its first-priority control scope. | Security Review | scoped control matrix, owner Safety and Compliance lead, trigger assurance planning | - |
| COM-002 | ISO/IEC 27001 alignment MUST reuse the SOC 2 risk and control catalog. | Inspection | control crosswalk, owner Safety and Compliance lead, trigger assurance planning | - |
| COM-003 | Personal-data processing MUST implement applicable lawful-basis, consent, minimization, retention, rights, residency, and transfer controls. | Security Review | privacy control assessment, owner Privacy and Safeguarding lead, trigger design approval | [Data Specification](../specifications/data-and-retention.md) |
| COM-004 | Payment design MUST minimize PCI DSS scope through hosted checkout and tokenized provider integration and MUST undergo periodic scope verification. | Security Review; Inspection | PCI scope review, owner Finance controller, trigger payment integration acceptance | [Integrations](../specifications/integrations-and-contracts.md) |
| COM-005 | Welfare, veterinary, conservation, and heritage records MUST follow the applicable operating jurisdiction's rules. | Inspection | jurisdiction control mapping, owner Safety and Compliance lead, trigger estate onboarding | [Data Specification](../specifications/data-and-retention.md) |
| COM-007 | Introduction of human clinical data MUST trigger a scoped HIPAA and Business Associate Agreement review before processing begins. | Inspection | scope decision record, owner Privacy and Safeguarding lead, trigger clinical-data proposal | [Data Specification](../specifications/data-and-retention.md) |
