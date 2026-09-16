# ADR-004: Keep People in Control of AI Decisions

## Status

Proposed

## Date

2026-09-15

## Context

AI can help people find important information and explain its recommendations. However, decisions about safety, animal welfare, money, legal matters, and public communication must remain the responsibility of an authorized person.

## Decision

Use AI to produce approved findings and recommendations only.

Before any action is taken:

1. Apply the relevant fixed rules.
2. Require approval from an authorized person for any important or difficult-to-reverse action.
3. Allow software to act on its own only for a documented list of low-risk actions that can be undone.

Treat the following as planned Operations Intelligence Platform architecture capabilities rather than optional commercial add-ons:

| Capability | Planned solution role | Governance boundary | Implementation state |
|---|---|---|---|
| Route and queue assistant | Suggest an itinerary at entry using opening status, queue estimate, accessibility needs, group preferences, weather, and available time. | Suggestions remain optional and consent-bound. Every ride and enclosure remains visible as included or skipped, every skipped item shows the reason, and visitors can select any skipped available item for recalculation unless a deterministic closure, safety, capacity, or entitlement rule makes it unavailable. | Planned |
| Zoo social-media strategist | Propose campaign themes, schedules, channel variants, and approved content for events such as births, conservation milestones, or new experiences. | Keeper, welfare, safeguarding, and marketing approval is required before publication; policy permits approved non-sensitive events. | Planned |
| Weather-aware experience promotion | Combine weather forecasts with approved historical patterns to recommend suitable indoor, outdoor, ride, or animal-viewing experiences. | Present likely conditions without promising animal behavior; deterministic closure, welfare, and safety rules take precedence. | Planned |
| Predictive maintenance and lifecycle insight | Prioritize possible ride or enclosure maintenance, hardware-failure risk, device battery replacement, and software or firmware update planning. | AI recommends investigation or timing only; qualified staff approve diagnosis, work, update rollout, shutdown, and return to service. | Planned |
| Affinity-content assistant | Draft policy-constrained animal updates, Virtual Pet activities, adoption messages, and Grow Together milestones. | Use only approved public facts and consented profile data; human review applies to welfare-sensitive, child-facing, and public content. | Planned |

### Primary Model Strategy

Start each planned capability with one well-tested primary model, provider, and version. It must pass the established evaluation, deterministic policy, fallback, rollback, and human-approval controls before release.

Do not operate competing primary models in parallel by default. Add a candidate model only when evidence identifies a material quality, safety, reliability, cost, latency, provider-resilience, or policy-control gap. A separately governed evaluator model remains permitted when deterministic evaluation is insufficient; it cannot be the sole release gate or authorize consequential action.

## Alternatives Considered

- Let AI make any decision: rejected because safety and professional responsibility would no longer be clear.
- Do not use AI: rejected because AI can help with prioritization, forecasting, and content assistance.
- Run competing primary models in parallel: rejected for the current baseline because it adds cost and operational complexity without established benefit.
- Let AI be the only release reviewer: rejected because an AI reviewer can be biased or disagree with the evidence. Independent checks and human review are required.

## Consequences

- Each AI capability has one primary model, provider, and version; it must be tested, record where its information came from, have a fallback, support rollback, be monitored for changing performance, and leave an audit trail.
- A primary-model outage or material regression routes the capability to its fallback until a validated replacement is approved.
- The organization must provide enough qualified people to review decisions and define the rules for each professional area.
- If AI is unavailable, critical rule-based workflows continue to operate.

## Related Requirements

FR-011; FR-020 to FR-022; FR-032; FR-033; CON-004.
