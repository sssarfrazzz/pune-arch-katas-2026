---
description: "Apply SDLC documentation governance, traceability, and verification rules to Markdown files."
applyTo: "**/*.md"
---

# SDLC Documentation Instructions

Apply these rules to all Markdown documentation in this workspace.

## Documentation Governance

Before editing documentation:

1. Read `README.md` when it exists.
2. Discover related SDLC artifacts.
3. Identify the canonical source and source-of-truth level.
4. Assess requirements, architecture, ADR, risk, test, operations, and traceability impact.
5. Update all affected artifacts in the same task.

When an artifact is missing, record the gap as `TBD` with an owner and trigger date. Do not invent content that implies approval, implementation, evidence, stakeholder agreement, or compliance.

## Style and Metadata

- Write concise, active-voice prose.
- Use ISO 8601 dates: `YYYY-MM-DD`.
- Use only these status values: `Draft`, `Proposed`, `Accepted`, `Superseded`, `Retired`.
- Use stable, unique, uppercase IDs.
- Prefer tables for structured records.
- Use Mermaid for diagrams.
- Keep headings meaningful and ordered.
- Link related artifacts with relative Markdown links.
- Preserve accepted ADR history; create a superseding ADR instead of rewriting it.

## Requirements

Each requirement MUST:

- have one stable uppercase ID;
- express one obligation;
- use objectively testable language;
- include measurable criteria where applicable;
- identify a verification method and observable evidence;
- link upstream to its business need and downstream to design, implementation, tests, risks, and evidence as applicable.

Use `MUST` for normative obligations. Do not use `should`, `may`, `appropriate`, `user-friendly`, `fast`, `secure`, or `efficient` as substitutes for measurable criteria.

## Architecture Documentation

Document architecture using C4 views:

- C1 System Context
- C2 Containers
- C3 Components
- C4 Code

C4 documentation MUST describe implemented code only. Label future work `Planned`. For every integration, document owner, direction, protocol, data contract, timeout, retry behavior, and failure handling. Document safety-critical behavior as isolated, local, and deterministic where required.

## ADR Documentation

An ADR is required for an expensive-to-reverse, security, safety, operationally significant, cross-cutting, or architectural decision.

Required sections:

- Status
- Date
- Context
- Decision
- Alternatives Considered
- Consequences
- Related Requirements
- Related Risks
- Related Tests

## Risk Documentation

Risk entries MUST include ID, description, likelihood, impact, mitigation, residual risk, and owner. Use `Low`, `Medium`, or `High` consistently for likelihood and impact.

## Traceability and Verification

Maintain bidirectional traceability through:

`Business Need -> Requirement -> Design -> ADR -> Component -> Test -> Risk -> Evidence`

Every requirement MUST have a verification method from this set: Unit Test, Integration Test, System Test, Simulation, Security Review, Operational Drill, Inspection, or Metric Validation.

Do not leave orphaned requirements, unlinked tests, or risks without mitigations.

## Documentation Review Checklist

Before completing a documentation change, verify:

- IDs are unique and links resolve.
- Status values are valid.
- Dates use `YYYY-MM-DD`.
- Requirements contain one testable obligation each.
- Requirements map to verification and evidence.
- Architecture diagrams use Mermaid and match implementation status.
- ADR references and statuses are consistent.
- Risks include owners, mitigations, and residual risk.
- Traceability links are complete in both directions.
- Unknowns use `TBD`, owner, and trigger date.