# ADR-002: Critical Edge Processing

## Status

Proposed

## Date

2026-09-15

## Context

Critical alerts, admissions, animal care, workforce execution, and dashboards must continue during cloud isolation, while routine processing must control cost.

## Decision

Execute deterministic critical processing and approved alerts at the estate edge. Synchronize routine telemetry within four hours when a cloud route is available and support 72 hours of authorized local operation.

## Alternatives Considered

- Cloud-only processing: rejected because WAN loss would stop critical workflows.
- Edge-only operation: rejected because cross-estate management and scheduled analytics require cloud capability.
- Real-time cloud transfer for all data: rejected due to cost and necessity boundaries.

## Consequences

- Local policy, storage, identity, replay, conflict handling, and operations support are required.
- Edge/cloud consistency is eventual for routine evidence.
- Critical alert latency can be measured independently of cloud availability.

## Related Requirements

BR-003; FR-008; FR-014; NFR-001 to NFR-004.
