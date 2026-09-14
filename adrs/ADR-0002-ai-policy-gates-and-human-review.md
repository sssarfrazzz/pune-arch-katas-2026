# ADR-0002: AI Policy Gates and Human Review

- Status: Accepted for initial architecture
- Date: 2026-09-14
- Deciders: Estate operations, animal-care, safety, finance, marketing, data, and platform stakeholders

## Context

Potential AI use cases include visitor-feedback analysis, demand forecasting, animal counting, welfare anomaly detection, maintenance prioritization, visitor assistance, and marketing recommendations. These outputs are probabilistic and can change as data, models, prompts, providers, and costs change. Errors could affect animal welfare, ride safety, customer trust, finances, or public communications.

## Decision

AI capabilities will be isolated behind versioned internal APIs and will produce recommendations or findings—not unreviewed authority over consequential actions.

Every capability must have:

- a named owner and documented purpose;
- approved data sources and retention rules;
- a model/prompt/provider version;
- a versioned evaluation set and task-specific quality thresholds;
- confidence, evidence, latency, and cost metadata;
- a deterministic fallback or human-review route;
- production monitoring, disablement, and rollback procedures.

A deterministic policy engine will decide whether output can be used automatically. Human review is mandatory for ride safety, animal treatment/welfare findings, population corrections, financial settlement, refunds, and public marketing/content publication unless a later ADR explicitly approves a narrower automation boundary.

## Alternatives considered

### Direct model-to-action integration

Rejected because it creates unclear accountability, makes nondeterministic output a control path, and increases the impact of hallucination, drift, and provider changes.

### No AI in production

Rejected because the kata specifically asks for AI-assisted solutions and the estate has valuable opportunities for analysis, forecasting, and staff assistance. AI will be introduced incrementally and safely.

### AI-only approval with confidence threshold

Rejected as insufficient for high-impact decisions. Confidence is a model signal, not proof of correctness; policy, evidence, and human accountability remain necessary.

## Consequences

### Positive

- Core ticketing, admissions, safety, welfare, and finance continue if AI is unavailable.
- The architecture supports model/provider replacement and independent rollback.
- Errors and corrections become observable data for evaluation improvement.
- Stakeholders can understand why a recommendation was made and who approved it.
- Advisory use can be expanded gradually after evidence demonstrates value.

### Negative

- Human review introduces operational cost and response-time requirements.
- Inference audit metadata and evaluation datasets require storage and governance.
- Some AI features will deliver recommendations rather than full automation.
- Quality measurement must be designed per use case; one overall “AI accuracy” metric is inadequate.

## Evaluation and monitoring baseline

- Animal counting: count error, precision/recall, and agreement with reviewed counts.
- Welfare anomaly detection: incident recall, false-alert rate, and lead time.
- Visitor assistant: grounded-answer rate, unsafe-answer rate, refusal correctness, and human rating.
- Feedback analysis: classification F1, factual summary rate, and action extraction accuracy.
- Forecasting: error by area and season, calibration, and business impact.
- All capabilities: latency, cost, drift, subgroup performance, override rate, and rollback readiness.

## Open questions

- Which use cases are advisory-only in the first release?
- Who is authorized to approve model promotion and automated policy changes?
- What minimum quality thresholds are acceptable for each species, ride, and business workflow?
- How frequently can sampled production outputs be reviewed by qualified staff?
