# Von Digitalis Estates — Architecture Diagrams

These diagrams are the first visual baseline for the architecture proposal. They use the following notation:

- Rounded boxes represent people or external systems.
- Rectangles represent application services or processing components.
- Cylinders represent persistent stores.
- Dashed arrows represent asynchronous events or eventual consistency.
- AI output is advisory until it passes a deterministic policy gate and, where required, human review.

## 1. System context

```mermaid
flowchart LR
  Visitor([Visitor]) --> Experience[Visitor web/mobile experience]
  Staff([Estate staff]) --> StaffApp[Staff and operations apps]
  Vet([Animal-care and veterinary staff]) --> StaffApp
  Experience --> Platform[Von Digitalis Estates platform]
  StaffApp --> Platform
  Devices([MQTT sensors and estate devices]) --> Edge[Estate edge gateways]
  Edge --> Platform
  Payment([Payment provider]) --> Platform
  Identity([Identity provider]) --> Platform
  Maps([Maps, messaging, social and external data]) --> Platform
  Platform --> Outcomes[Tickets, safe operations, animal welfare, insight and growth]
```

## 2. Container view

```mermaid
flowchart TB
  subgraph Channels[Channels]
    Web[Visitor web/mobile]
    Ops[Staff and operations apps]
    Gate[Admission gate clients]
  end

  API[API gateway / BFF]
  Identity[Identity and consent]
  Commerce[Ticketing and orders]
  Admission[Admissions and scan ledger]
  Catalogue[Estate catalogue]
  Welfare[Animal welfare]
  Maintenance[Ride and facility maintenance]
  Devices[Device and edge management]
  Marketing[Marketing and partnerships]
  Insight[Visitor insight and reporting]
  Policy[Safety, welfare and business policy]
  Bus[(Event backbone)]
  Data[(Governed analytical data platform)]
  AI[AI capability layer]
  Review[Human review and approval]
  External[Payment, maps, messaging and social providers]

  Web --> API
  Ops --> API
  Gate --> API
  API --> Identity
  API --> Commerce
  API --> Admission
  API --> Catalogue
  API --> Welfare
  API --> Maintenance
  API --> Marketing
  Commerce -. events .-> Bus
  Admission -. events .-> Bus
  Welfare -. events .-> Bus
  Maintenance -. events .-> Bus
  Devices -. telemetry .-> Bus
  Bus --> Insight
  Bus --> Data
  Data --> AI
  AI --> Policy
  Policy --> Review
  Review --> Welfare
  Review --> Maintenance
  Review --> Marketing
  Review --> Insight
  API --> External
```

## 3. Edge-to-cloud data flow

```mermaid
flowchart LR
  Sensor[Sensor, counter or staff device] -->|MQTT| Gateway[Zone edge gateway]
  Gateway --> Buffer[(Durable local buffer)]
  Gateway --> LocalRules[Approved local safety/welfare rules]
  LocalRules --> AlertLocal[Local staff alert]
  Gateway -->|when connected| Ingest[Authenticated cloud ingestion]
  Buffer -->|replay after reconnect| Ingest
  Ingest --> Validate[Validate, timestamp, deduplicate and version]
  Validate --> EventBus[(Regional event backbone)]
  EventBus --> Current[Operational projections]
  EventBus --> AlertCloud[Cloud alerting and task creation]
  EventBus --> Raw[(Immutable raw data)]
  Raw --> Curated[(Curated analytical data and features)]
  Curated --> Models[Forecasting, anomaly and counting models]
  Models --> Policy[Policy gate and human review]
```

## 4. Ticket purchase and offline admission

```mermaid
sequenceDiagram
  actor Visitor
  participant App as Visitor experience
  participant API as API gateway
  participant Ticket as Ticketing service
  participant Pay as Payment provider
  participant Gate as Gate client
  participant Ledger as Admission scan ledger

  Visitor->>App: Select date, ticket or family pass
  App->>API: Request quote
  API->>Ticket: Validate capacity and pricing rules
  Ticket-->>App: Quote and availability
  Visitor->>App: Confirm purchase
  App->>API: Submit order with idempotency key
  API->>Pay: Authorize payment
  Pay-->>API: Authorization result
  API->>Ticket: Commit order and issue signed ticket
  Ticket-->>App: Ticket and receipt
  Visitor->>Gate: Present ticket
  Gate->>Gate: Verify signature, date, entitlement and replay status
  Gate->>Ledger: Record scan locally or online
  Ledger-->>Gate: Admit or refer to staff
  Gate-->>Visitor: Admission result
  Note over Gate,Ledger: Offline scans reconcile after connectivity returns
```

## 5. Animal-welfare alert

```mermaid
sequenceDiagram
  participant Device as Enclosure device or staff app
  participant Edge as Edge gateway
  participant Ingest as Ingestion and validation
  participant Welfare as Welfare service
  participant Rules as Welfare policy engine
  participant Staff as Care staff
  participant AI as Optional AI detector

  Device->>Edge: Reading or observation
  Edge->>Edge: Timestamp, buffer and apply local rule if needed
  Edge-->>Ingest: MQTT event when connected
  Ingest->>Welfare: Validated observation
  Welfare->>Rules: Evaluate threshold and care policy
  Rules-->>Staff: Alert and care task
  Welfare->>AI: Request anomaly/count estimate when configured
  AI-->>Rules: Finding, confidence and evidence
  Rules-->>Staff: Review request or supporting signal
  Staff->>Welfare: Acknowledge, act, amend, escalate or close
  Welfare->>Welfare: Append immutable history and audit decision
```

## 6. AI evaluation and production control

```mermaid
flowchart LR
  Data[Approved data and golden set] --> Eval[Offline evaluation]
  Eval --> Gate{Quality, safety, fairness, cost and latency gates}
  Gate -->|fail| Improve[Correct data/model/prompt or reject]
  Gate -->|pass| Shadow[Shadow or canary deployment]
  Shadow --> Human[Human review and acceptance]
  Human --> Release[Approved production release]
  Release --> Monitor[Production monitoring]
  Monitor --> Outcome[Later outcomes and sampled review]
  Outcome --> Drift[Drift, quality, safety and cost analysis]
  Drift --> Decision{Within thresholds?}
  Decision -->|yes| Monitor
  Decision -->|no| Rollback[Disable or roll back capability]
  Rollback --> Fallback[Deterministic rule, last-known safe state or human workflow]
  Fallback --> Improve
```

## 7. Diagram review questions

- Are the boundaries between ticketing, admissions, payment, and identity clear enough to prevent inconsistent ownership?
- Is the edge gateway capable of the required offline window and local alert behavior?
- Which welfare and ride signals must be local and which may wait for cloud processing?
- Are aggregated visitor insights sufficient without collecting unnecessary individual movement data?
- Does every AI path show a fallback, evidence, monitoring, and an accountable decision maker?
