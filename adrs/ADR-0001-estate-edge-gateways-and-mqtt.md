# ADR-0001: Estate Edge Gateways and MQTT

- Status: Accepted for initial architecture
- Date: 2026-09-14
- Deciders: Estate operations, animal-care, safety, security, and platform stakeholders

## Context

The estate has patchy Wi-Fi, but it needs dependable information from rides, enclosures, animal-care devices, visitor counters, and other equipment. The problem statement explicitly allows MQTT-capable hardware. Cloud-only devices would lose observations during outages and could delay safety or welfare response.

## Decision

Use zone-level estate edge gateways as the boundary between local devices and cloud services.

- Devices communicate with their gateway over authenticated MQTT.
- Gateways assign event metadata, validate basic schemas/units, and maintain a durable local buffer.
- Gateways run only a small, approved set of local safety and welfare rules.
- Gateways forward events to the cloud event backbone when connected and replay buffered events after reconnect.
- Cloud ingestion performs authoritative validation, deduplication, ordering/version checks, enrichment, routing, and long-term storage.
- Device identity is unique and certificate-based, with least-privilege topic access, rotation, revocation, expiry, and replay protection.
- Signed gateway configuration is versioned and rollbackable.

## Alternatives considered

### Cloud-only device connectivity

Rejected because patchy Wi-Fi would create data loss and unacceptable delay for critical alerts.

### Direct device-to-cloud MQTT

Rejected for the first release because it increases device credential exposure, makes buffering inconsistent, and complicates local response and fleet management.

### Fully autonomous edge control

Rejected because complex safety, animal-care, or operational decisions need central policy, auditability, and human accountability. Local behavior is limited to approved rules and alerting.

## Consequences

### Positive

- Operations continue through temporary connectivity loss.
- Local alert latency is predictable for configured rules.
- Cloud services receive a consistent event contract rather than device-specific protocols.
- Device credentials and configuration can be managed by zone.
- Replayed events preserve original event time and can be processed idempotently.

### Negative

- Gateways become operationally important infrastructure that needs power, monitoring, patching, backup configuration, and physical security.
- Local rules must be tested and versioned separately from cloud services.
- Duplicate, late, and conflicting events require explicit handling.
- Some dashboards and AI capabilities will be delayed or degraded during an outage.

## Required safeguards

- Durable storage sized for at least the agreed offline window.
- Health metrics for gateway uptime, device last-seen, buffer depth, replay age, clock drift, and rejected messages.
- A visible data-gap indicator in operational dashboards.
- Safe local behavior on gateway storage exhaustion, clock failure, or invalid configuration.
- Reconciliation tests covering duplicate replay, out-of-order events, and partial reconnect.

## Open questions

- What offline duration must be supported for each estate zone?
- Which exact alerts must run locally, and what are their response-time targets?
- What power, physical security, and network segmentation are available at each zone?
- What is the expected device count and message rate per zone?
