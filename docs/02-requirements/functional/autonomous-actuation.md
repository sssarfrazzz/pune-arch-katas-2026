# Autonomous Actuation Requirements

| Field | Value |
|---|---|
| Document ID | REQ-005 |
| Status | Draft |
| Date | 2026-09-15 |
| Source | [Solution Overview](../../../solution-overview-15thSept.md) |

Product 2 is planned. These requirements do not claim certification or implementation.

| ID | Requirement | Upstream | Verification | Observable evidence | Design / risk |
|---|---|---|---|---|---|
| FR-023 | Every physical mission MUST be signed and bind tenant, estate, asset, Unit ID, action class, route or geofence, payload, approver or policy, start window, expiry, and abort behavior. | BN-007 | Security Review; System Test | TBD: signature and tamper test report, owner Safety and Compliance lead, trigger Product 2 pilot | [Mission Specification](../../04-specifications/autonomous-missions-and-safety.md); RISK-001 |
| FR-024 | A robot or drone MUST execute only a certified, pre-declared action in its approved action catalog. | BN-007 | Inspection; System Test | TBD: catalog conformance report, owner Safety and Compliance lead, trigger Product 2 pilot | [Mission Specification](../../04-specifications/autonomous-missions-and-safety.md); RISK-001 |
| FR-025 | Authorized staff MUST be able to pause, abort, and quarantine an active mission. | BN-007 | Operational Drill | TBD: operator-control drill, owner Operations supervisor, trigger Product 2 pilot | [Robotics View](../../05-architecture/views/robotics-and-drone-safety.md); RISK-002 |
| FR-026 | Emergency-stop, proximity, geofence, collision, lost-link, and safe-return or landing controls MUST operate without cloud or AI availability as applicable to the mission class. | BN-007 | Simulation; Operational Drill | TBD: independent interlock evidence, owner Safety and Compliance lead, trigger certification | [Robotics View](../../05-architecture/views/robotics-and-drone-safety.md); RISK-002 |
| FR-027 | Loss of mission authority MUST cause the asset to enter its certified safe-stop, return, hover, or landing state. | BN-007 | Simulation | TBD: lost-authority scenario report, owner Safety and Compliance lead, trigger certification | [Mission Specification](../../04-specifications/autonomous-missions-and-safety.md); RISK-002 |
| FR-028 | Product 2 MUST remain disabled until Product 1 maturity evidence and all applicable certifications are present. | BN-007 | Inspection | TBD: activation-gate record, owner Product owner, trigger Product 2 pilot | [Delivery Roadmap](../../06-delivery/delivery-roadmap.md); RISK-001 |
| FR-029 | Every payload or device handoff MUST record custody, source and destination identities, applicable seal, weight and temperature evidence, and positive confirmation. | BN-007 | System Test; Inspection | TBD: custody-chain report, owner Operations supervisor, trigger Product 2 pilot | [Mission Specification](../../04-specifications/autonomous-missions-and-safety.md); RISK-012 |

Risk and verification mappings are maintained in the [Traceability Matrix](../../06-delivery/traceability-matrix.md).
