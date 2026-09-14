# Von Digitalis Estates Functional Requirements

## 1. Purpose and scope

This document defines the functional baseline for a modern digital platform for the Von Digitalis Estates. It converts the problem statement into capabilities that can be designed, delivered, and tested. It intentionally separates confirmed requirements from proposed scope and open questions.

### Confirmed context

- The estate contains 40 historic amusement-park rides.
- The animal collection contains more than 200 exotic and poisonous land and aquatic animals across 55 displays/enclosures.
- Current average attendance is approximately 5,000 visitors per day, with a target of at least 15,000 per day within three years.
- The estate needs online tickets, including family passes.
- Management needs insight into popularity and where to invest or deploy staff.
- Animal staff need to track health, food consumption/quality, and jumping-piranha population levels.
- The estate has patchy Wi-Fi; cloud services may be used with MQTT-capable hardware for estate data.
- AI use is expected, including a credible approach to evaluation and production monitoring.

### Proposed initial boundary

The platform includes visitor commerce, access, estate telemetry, operational dashboards, animal-care records, ride/facility maintenance, analytics, marketing support, and governed AI capabilities. It does not control ride machinery or animal enclosures directly in the first release; it provides monitored data, alerts, recommendations, and authorized workflows.

## 2. Actors and external systems

| Actor/system | Responsibilities |
|---|---|
| Visitor | Discovers the estate, buys tickets/passes, enters, navigates, gives feedback, and receives offers. |
| Family/group purchaser | Buys and manages multiple admissions under one order. |
| Admissions staff | Scan/validate tickets, resolve entry exceptions, and manage capacity. |
| Estate operations manager | Reviews attendance, popularity, capacity, staffing, revenue, and investment dashboards. |
| Ride operator/maintenance staff | Operate rides, record inspections, report faults, and manage maintenance work. |
| Animal-care staff/veterinarian | Record observations, health treatments, feeding, weight, mortality/birth, and care tasks. |
| Marketing/social-media team | Manages campaigns, partnerships, influencers, offers, and content performance. |
| Finance/admin | Reviews settlement, revenue, costs, refunds, and audit records. |
| Sensor/gateway devices | Collect environmental, animal, enclosure, counter, ride, and equipment observations. |
| Payment, identity, maps, messaging, social, and cloud services | External integrations supporting platform functions. |

## 3. Functional requirements

Priority: Must = first operational release; Should = next release; Could = later or experimental.

### 3.1 Visitor, ticketing, and admissions

| ID | Requirement | Priority |
|---|---|---|
| FR-001 | Visitors shall browse estate areas, rides, animal displays, opening hours, accessibility information, safety notices, and available experiences. | Must |
| FR-002 | Visitors shall purchase individual tickets and configurable family/group passes online. | Must |
| FR-003 | The system shall apply ticket type, date, time slot, age, capacity, discounts, taxes, and promotional rules to a quote. | Must |
| FR-004 | The system shall accept secure payment, issue an order and receipt, and support cancellation, refund, and amendment rules. | Must |
| FR-005 | The system shall issue verifiable digital tickets with order, admission date, party size, entitlements, and anti-replay protection. | Must |
| FR-006 | Admissions staff shall validate tickets online and in a degraded/offline mode, then synchronize scans and exceptions when connectivity returns. | Must |
| FR-007 | The system shall show attendance, capacity, admissions, no-shows, and entry exceptions by day, time, ticket type, and estate area. | Must |
| FR-008 | The system shall support optional add-ons such as guided tours, premium heritage access, bus rides, food packages, events, and accommodation. | Should |

### 3.2 Visitor experience and feedback

| ID | Requirement | Priority |
|---|---|---|
| FR-009 | The visitor experience shall provide an estate map, opening/status information, accessible routes, rest areas, food courts, and emergency guidance. | Should |
| FR-010 | The system shall capture visitor feedback from digital forms, QR codes, kiosks, staff entry, and optional conversational interfaces. | Must |
| FR-011 | The system shall associate feedback with date, area, ride/display, experience type, and consent where available. | Must |
| FR-012 | The system shall summarize, classify, and prioritize feedback, while preserving the original submission and confidence/evidence for review. | Should |
| FR-013 | Managers shall view actionable feedback themes and assign improvement actions with an owner, status, and due date. | Should |
| FR-014 | Visitors shall receive relevant, consent-based recommendations for experiences, packages, events, and facilities. | Could |

### 3.3 Popularity, flow, and commercial intelligence

| ID | Requirement | Priority |
|---|---|---|
| FR-015 | The platform shall collect aggregated visitor movement and interaction signals from ticket scans, Wi-Fi/Bluetooth/counter devices where lawful, app interactions, and attraction scans. | Must |
| FR-016 | The platform shall report popularity by estate zone, ride, display, facility, time period, visitor type, and capacity context. | Must |
| FR-017 | Managers shall compare attendance, dwell time, queue/wait indicators, repeat visits, satisfaction, revenue, and operating cost by area. | Must |
| FR-018 | The system shall identify overcrowding, under-used areas, flow bottlenecks, and likely staffing or signage interventions. | Should |
| FR-019 | The platform shall support demand forecasts for attendance and selected attractions to inform staffing, capacity, opening hours, and investment. | Should |
| FR-020 | The platform shall measure campaign, influencer, partnership, package, and social-media performance through attributable links or codes where available. | Should |

### 3.4 Ride, facility, and estate maintenance

| ID | Requirement | Priority |
|---|---|---|
| FR-021 | Staff shall maintain a register of rides, facilities, safety-critical components, inspection schedules, certificates, and operating constraints. | Must |
| FR-022 | Staff shall record inspections, defects, incidents, closures, repairs, parts, labor, photos, approvals, and return-to-service decisions. | Must |
| FR-023 | The system shall prevent or flag the operational workflow for a ride whose inspection, certification, or safety status is expired or failed; it shall not directly control certified ride machinery or safety interlocks. | Must |
| FR-024 | The system shall create, prioritize, assign, escalate, and close maintenance work orders with a complete audit trail. | Must |
| FR-025 | Managers shall see maintenance backlog, downtime, repeat faults, cost, risk, and investment indicators by ride/facility. | Must |
| FR-026 | The platform shall ingest equipment telemetry where available and create alerts for abnormal readings or loss of signal. | Should |

### 3.5 Animal welfare and collection management

| ID | Requirement | Priority |
|---|---|---|
| FR-027 | Staff shall maintain an animal profile with species, identity or group, enclosure, provenance, permitted care data, and welfare plan. | Must |
| FR-028 | Authorized staff shall record health observations, weight, activity, treatment, medication, incidents, veterinary assessment, and follow-up tasks. | Must |
| FR-029 | Staff shall record feeding schedule, food type, quantity offered, quantity consumed/estimated, feeding behavior, and missed feeding. | Must |
| FR-030 | The system shall monitor enclosure/environment observations such as temperature, humidity, water quality, lighting, and equipment status where sensors are available. | Must |
| FR-031 | The system shall alert animal-care staff to out-of-range conditions, missed care activities, concerning health trends, or unusual consumption. | Must |
| FR-032 | The system shall maintain population counts and changes for group species, with specific support for jumping-piranha population counts, births, deaths, transfers, and uncertainty. | Must |
| FR-033 | The system shall provide animal and enclosure dashboards with current status, history, trends, alerts, treatments, feeding, and unresolved tasks. | Must |
| FR-034 | The system may use AI to detect behavior, count animals, or identify welfare anomalies from images/video/sensor data, but every automated finding shall include confidence and a human review path. | Should |
| FR-035 | The system shall preserve welfare records and evidence according to veterinary, legal, privacy, and conservation retention policies. | Must |

### 3.6 Visitor growth and profitability

| ID | Requirement | Priority |
|---|---|---|
| FR-036 | Marketing users shall manage campaigns, audience segments, offers, referral/influencer codes, partnerships, and campaign consent. | Should |
| FR-037 | The system shall provide revenue, attendance, conversion, average order value, package uptake, occupancy, cost, and profitability views. | Must |
| FR-038 | The system shall support experiments for offers, packages, content, and visitor journeys, recording cohort, variant, exposure, and outcome. | Should |
| FR-039 | An AI marketing assistant may propose content, campaigns, partnerships, or visitor-growth opportunities from approved data, subject to human approval before publishing. | Should |
| FR-040 | The system shall distinguish recommendations from approved business actions and record the approver, rationale, and resulting outcome. | Must |

### 3.7 Connectivity, AI governance, and platform operations

| ID | Requirement | Priority |
|---|---|---|
| FR-041 | Estate gateways shall authenticate field devices using approved local protocols, buffer data during Wi-Fi/cloud outages, and forward normalized events northbound using MQTT or an equivalent secured event protocol when connectivity resumes. | Must |
| FR-042 | The platform shall validate, timestamp, deduplicate, version, and route device data to operational dashboards, alerts, history, and analytics. | Must |
| FR-043 | Operators shall see device health, last-seen time, buffered data, battery/connectivity state, and data-quality failures. | Must |
| FR-044 | AI features shall have an owner, purpose, approved data sources, model/prompt version, evaluation set, quality threshold, fallback, and rollback procedure. | Must |
| FR-045 | The platform shall evaluate AI outputs before release using task-specific quality, safety, fairness, latency, cost, and human-acceptance measures. | Must |
| FR-046 | The platform shall monitor production AI for drift, quality regression, unsafe output, hallucination, bias indicators, latency, cost, and provider/model changes. | Must |
| FR-047 | Staff shall be able to correct AI outputs, record the reason, and feed approved corrections into evaluation and improvement workflows. | Must |
| FR-048 | The platform shall fall back to deterministic rules, last-known safe state, or human review when AI, cloud, or connectivity is unavailable. | Must |

### 4.8 Workforce, incidents, and ecosystem operations

| ID | Requirement | Priority / phase |
|---|---|---|
| FR-049 | The platform shall create staff rosters using role, qualification, certification, availability, working-time, and rest constraints. | Must / Phase 1 |
| FR-050 | The staff application shall provide offline shifts, assignments, procedures, checklists, evidence capture, task completion, exceptions, and handovers, with synchronization after reconnection. | Must / Phase 1 |
| FR-051 | The platform shall detect missing mandatory coverage, identify qualified available replacements, dispatch an offer/request, and escalate when coverage is not restored. | Must / Phase 1 |
| FR-052 | Staff shall check in to a duty or task without requiring continuous precise employee tracking by default. | Must / Phase 1 |
| FR-053 | The platform shall manage an incident from report through timeline, evidence, classification, ownership, escalation, review, corrective action, closure, and end-of-day handover. | Must / Phase 1 |
| FR-054 | The platform shall route visitor service cases, including accessibility requests, missing passes, complaints, lost-person reports, and service concerns, to an owner with status and escalation. | Should / Phase 2 |
| FR-055 | The platform shall track device and equipment software/version, warranty, support status, staged update, compatibility, rollback, and update outcome. | Should / Phase 2 |
| FR-056 | The platform shall integrate with authoritative enterprise systems for inventory, procurement, payroll, and asset records, preserving synchronization status and ownership rather than creating conflicting records. | Must / Phase 1 |
| FR-057 | The platform shall support parts reservation, issue, return, and reorder requests while treating the approved inventory system as authoritative. | Should / Phase 2 |
| FR-058 | The platform shall support controlled, purpose-limited access for veterinarians, inspectors, researchers, laboratories, maintenance partners, and other approved external stakeholders. | Should / Phase 2 |
| FR-059 | The platform shall support memberships, renewals, benefits, guest entitlements, points/rewards, consent-managed communications, and cancellation. | Should / Phase 2 |
| FR-060 | The platform shall support approved events, venues, partnerships, packages, and transport add-ons with capacity, entitlement, scheduling, safety review, attribution, and settlement information. | Should / Phase 2 |

### 4.9 Deferred productization and safeguarding scope

The following are deliberately not Phase One requirements. They require separate business and governance decisions:

- Zoo, Rides, and Combined product editions with multi-tenant isolation and tenant lifecycle management.
- Developer sandboxes, API certification, quotas, version-change notices, and revocation.
- Guardian-controlled child profiles, child-linked journeys, live media, and advanced personalization.
- Biometrics, which are disabled by default pending a separate lawful-necessity and proportionality decision.

## 4. Key acceptance scenarios

### Buy and use a family pass

The purchaser selects a date and family pass, receives a quote, completes payment, receives verifiable tickets for the party, and can present them at admissions. A disconnected gate can validate an already-issued ticket and later synchronize the scan without allowing replay.

### Respond to a welfare alert

A sensor or staff observation crosses a configured threshold. The platform records the observation, alerts the responsible care team, creates a task, shows recent history and feeding/health context, and records acknowledgement, action, outcome, and escalation.

### Monitor jumping-piranha population

Authorized staff record a count or upload evidence. The platform maintains a dated population history, distinguishes confirmed from estimated counts, flags an unexpected change, and does not silently replace a confirmed count with an uncertain AI estimate.

### Decide where to invest

A manager selects a period and compares area popularity, visitor flow, satisfaction, revenue, operating cost, downtime, and capacity. The dashboard explains data freshness and uncertainty and allows an AI-generated recommendation to be accepted, rejected, or annotated.

### Operate through a connectivity outage

An estate gateway buffers MQTT observations while cloud connectivity is unavailable. Safety-critical local alerts continue according to approved rules. When connectivity returns, events are replayed idempotently, with their original event time and a visible data gap.

## 5. Business rules and invariants

- A paid order has one authoritative status and cannot be double-refunded.
- A ticket is valid only for its configured date, entitlement, and admission rules and cannot be replayed.
- A ride cannot be presented as available when its safety status is expired, failed, or unresolved.
- Animal health and care records are append-only clinical/operational observations; corrections are amendments, not silent edits.
- AI recommendations never directly change safety status, animal treatment, financial settlement, or public content without an authorized human or deterministic policy decision.
- Device and AI events are idempotent and retain source time, ingestion time, source identity, confidence, and version.

## 6. Assumptions and open questions

### Assumptions

- Online ticketing is the first visitor-facing transaction capability.
- Estate staff have role-based access and mobile devices that can work offline.
- MQTT devices can be installed at gates, rides, enclosures, and selected visitor-flow points.
- Aggregated movement analytics will be designed with consent, minimization, and applicable privacy review.

### Open questions

- Which attractions, events, food, accommodation, and transport offerings are in the first commercial release?
- What are the legal and welfare thresholds for each species and enclosure?
- Which sensors are available and what must remain manual?
- What is the required offline duration and which local safety alerts are mandatory?
- What are the ticket capacity, pricing, refund, accessibility, and family-pass rules?
- Which AI use cases are advisory only, and which—if any—may be automated?
- Is external productization a business goal, or should multi-tenancy remain outside this estate platform?
- Which enterprise systems remain authoritative for people, inventory, procurement, finance, and asset management?
- What workforce qualifications, rest rules, staffing coverage, and incident severity levels apply to each estate operation?
