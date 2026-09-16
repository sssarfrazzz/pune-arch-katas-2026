# ADR-010: Local Workforce Coordination

## Status

Proposed

## Date

2026-09-15

## Context

Field teams require assignments, procedures, check-in, handover, evidence, and re-planning when WAN connectivity is unavailable.

## Decision

Maintain an estate-local coordinator for the current Operational Plan and execution evidence. Synchronize HRMS qualification and EAM work references while preserving their external authority.

## Alternatives Considered

- Cloud-only workforce operations: rejected because it fails the 72-hour isolation requirement.
- Replace HRMS/EAM locally: rejected because those systems remain authoritative.
- Paper-only fallback: not selected as the primary mechanism because reconciliation and verified evidence are required.

## Consequences

- Local policy and reference data require freshness and expiry rules.
- Every re-plan creates a version and explained diff.
- Safety, welfare, legal working-time, and qualification constraints precede demand and cost optimization.

## Related Requirements

BR-003; BR-005; FR-012 to FR-014; NFR-001.
