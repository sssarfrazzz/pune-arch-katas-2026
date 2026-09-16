# Architecture Overview

| Field | Value |
|---|---|
| Document ID | ARCH-001 |
| Status | Draft |
| Date | 2026-09-16 |
| Source | [Solution Overview](../solution-overview-15thSept.md) |

The current architecture baseline establishes Product 1. Product 2 remains the planned evolution in section 8 of the canonical source, with its architecture defined when administration activates that phase. [C4 Code](c4/c4-code.md) evolves with the implementation and maps namespaces, packages, entry points, data access, dependencies, and tests as they are created.

## Architecture Drivers

| Driver | Architectural response | Requirements | Decision |
|---|---|---|---|
| Patchy estate connectivity | Radio-first collection, local policy, local storage, and 72-hour operation | BR-003, NFR-001 to NFR-004 | [ADR-001](adr/ADR-001-radio-first-edge-connectivity.md), [ADR-002](adr/ADR-002-edge-critical-processing.md) |
| Safety and welfare accountability | Deterministic local gates, safer state, human approval, read-only safety integration | FR-009 to FR-011, FR-022, CON-003 | [ADR-004](adr/ADR-004-human-controlled-ai.md) |
| Operational simplicity and cost | Serverless cloud and modular monolith | BR-004, NFR-006 | [ADR-003](adr/ADR-003-serverless-modular-monolith.md) |
| Product portability | Shared contracts across shared, dedicated, and self-hosted deployments | FR-006, NFR-005, NFR-006 | [ADR-005](adr/ADR-005-portable-multi-tenant-deployment.md) |
| Enterprise authority | Anti-corruption adapters, authority registry, reconciliation | BR-006, FR-004, FR-005 | [ADR-006](adr/ADR-006-cots-authority-and-reconciliation.md) |
| Stable estate accounting | Immutable Unit ID and effective-dated economics | FR-001, FR-017 to FR-019 | [ADR-007](adr/ADR-007-operational-unit-identity.md), [ADR-011](adr/ADR-011-unit-credit-economics.md) |
| Privacy | Minimized visitor presence and aggregate queues | FR-015, FR-016, SEC-012 | [ADR-008](adr/ADR-008-privacy-minimized-visitor-presence.md) |
| Data quality and local evidence | Edge Bronze, Silver, and Gold promotion | FR-007, FR-008 | [ADR-009](adr/ADR-009-local-medallion-data-plane.md) |
| Workforce continuity | Local plan and execution coordination | FR-012 to FR-014 | [ADR-010](adr/ADR-010-local-workforce-coordination.md) |

## C4 Index

- [C1 System Context](c4/c1-system-context.md)
- [C2 Containers](c4/c2-containers.md)
- [C3 Components](c4/c3-components.md)
- [C4 Code](c4/c4-code.md)

## View Index

- [Edge and Connectivity](views/edge-and-connectivity.md)
- [Data and Integration](views/data-and-integration.md)
- [Security and Trust](views/security-and-trust.md)
- [Deployment and Tenancy](views/deployment-and-tenancy.md)
- [AI and Decisioning](views/ai-and-decisioning.md)

## Safety Boundary

The platform has no write or control path to certified ride, containment, fire, or life-support systems.
