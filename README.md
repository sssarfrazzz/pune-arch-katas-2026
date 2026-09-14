# Von Digitalis Estates — AI-Assisted Architecture

Initial architecture repository for the Von Digitalis Estates problem from [Architectural Katas 2026: AI-Assisted Software Architecture](../architecturalkatas2026aiassistedsoftwarearchitecture1787836977189.pdf).

## Problem in one paragraph

The Von Digitalis Estates are a large, historically important estate combining a 40-ride, 18th-century amusement park with an exotic and poisonous animal collection of more than 200 animals in 55 displays and enclosures. The estate currently receives about 5,000 visitors per day and must prepare for at least 15,000 within three years. The digital solution must improve visitor access and revenue, reveal how visitors use the estate, improve ride and facility investment decisions, and help staff keep animals healthy while operating with patchy Wi-Fi.

## Business goals

- Grow attendance from approximately 5,000 to at least 15,000 visitors per day within three years.
- Increase estate revenue through better ticketing, family passes, packages, events, partnerships, and facilities.
- Understand visitor behavior and popularity so investment and staffing decisions are evidence-based.
- Keep rides safe, available, and maintainable.
- Keep the exotic animal collection healthy through timely, trustworthy care information and alerts.
- Use AI responsibly to improve insight and productivity without delegating safety-critical decisions to an ungoverned model.

## Biggest challenges

- The estate is large and operational information is distributed across rides, enclosures, gates, staff, and visitors.
- Patchy Wi-Fi makes continuous cloud connectivity unreliable.
- Animal welfare and ride safety require timely action, trustworthy records, and clear human accountability.
- Visitor growth increases peak admission, telemetry, analytics, and support load.
- AI output is probabilistic and may change as models, providers, data, and costs change.

## Repository map

- [Functional requirements](requirements/functional-requirements.md)
- [Non-functional requirements](requirements/non-functional-requirements.md)
- [Initial architecture proposal](architecture/initial-architecture-proposal.md)
- [Architecture diagrams](architecture/diagrams/README.md)
- [Architecture decision records](adrs/README.md)

### Planned additions

The repository can grow with the following artifacts as design decisions mature:

- `adrs/` — architecture decision records and trade-off analysis
- [architecture/diagrams/](architecture/diagrams/) — context, container, deployment, data-flow, and AI workflow diagrams
- [adrs/](adrs/) — architecture decision records and trade-off analysis
- `requirements/` — business goals, functional/non-functional requirements, assumptions, risks, and future scope
- `ai-evaluation/` — evaluation datasets, metrics, release gates, and production monitoring approach

## Current status

This is an initial architecture baseline. Functional and non-functional requirements, the first architecture proposal, initial diagrams, and two foundational ADRs are available. The requirements also distinguish Phase One operational foundations from Phase Two commercial and ecosystem capabilities; further technology decisions and implementation details remain to be refined after stakeholder review.

## How to review

1. Review the functional requirements and confirm scope, priorities, assumptions, and open questions.
2. Review the architecture proposal against the requirements, especially offline operation, safety, welfare, and AI governance.
3. Record significant trade-offs as ADRs.
4. Review the architecture diagrams and identify the highest-risk trade-offs.
5. Record those trade-offs as ADRs before implementation planning.

## Source and interpretation

The PDF is the problem statement and competition guidance. Its submission instructions, judging criteria, and schedule are not product requirements. This repository treats the following as product requirements: ticketing, visitor/popularity insight, ride maintenance visibility, animal health/feeding/population monitoring, visitor growth and profitability, estate-to-cloud connectivity, and meaningful AI validation. Business decisions not specified in the brief are identified as assumptions or open questions in the documents.
