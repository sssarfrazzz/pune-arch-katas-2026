# IoT Data Processing Architecture: Hierarchical Component Views

## Purpose

This document presents the IoT data-processing architecture in two levels:

1. A **high-level end-to-end view** showing the major components and their communication.
2. A set of **component-focused views** where one component is expanded in detail and the surrounding components remain abstract. This preserves end-to-end context while making each diagram readable during architecture reviews.

> **Source-aligned behavior:** redundant local hubs, store-before-forwarding, critical and scheduled paths, at least 72 hours of local buffering, checkpoint-based replay, Bronze/Silver/Gold data layers, and approved Gold-data distribution.
>
> **Proposed elaborations:** event identity, delivery envelopes, dead-letter flows, authentication, acknowledgements, detailed observability, and policy controls are recommended design details rather than explicit source requirements.

---

## 1. High-level end-to-end architecture

This is the abstract overview. It intentionally hides internal implementation details and shows only the important architectural components and communication paths.

```mermaid
flowchart LR
    DEVICES["Park IoT Devices"]
    INTEGRATION["Device Integration"]
    EDGE["Redundant Local Hub"]
    BUFFER[("Durable Edge Buffer<br/>at least 72 hours")]
    NETWORK["Secure Edge-to-Cloud<br/>Connectivity"]
    INGESTION["Cloud Ingestion"]
    PROCESSING["Critical and Batch<br/>Processing"]
    DATA[("Bronze, Silver and Gold<br/>Data Platform")]
    SERVING["Serving and Distribution"]
    CONSUMERS["Park Systems and<br/>Approved Consumers"]
    OBSERVE["Monitoring, Audit<br/>and Alerting"]

    DEVICES -->|"device readings and events"| INTEGRATION
    INTEGRATION -->|"normalized events"| EDGE
    EDGE -->|"store before forwarding"| BUFFER
    BUFFER -->|"critical immediately<br/>normal on schedule<br/>replay after reconnect"| NETWORK
    NETWORK -->|"authenticated transport"| INGESTION
    INGESTION -->|"accepted original events"| DATA
    INGESTION -->|"priority route"| PROCESSING
    PROCESSING -->|"validated and trusted results"| DATA
    DATA -->|"approved Gold data"| SERVING
    SERVING -->|"API, events and reports"| CONSUMERS

    EDGE -. "health, capacity and delivery state" .-> OBSERVE
    NETWORK -. "availability and replay status" .-> OBSERVE
    INGESTION -. "authentication and ingestion status" .-> OBSERVE
    PROCESSING -. "latency, failures and quality" .-> OBSERVE
    DATA -. "freshness and quality" .-> OBSERVE
    SERVING -. "access and audit trail" .-> OBSERVE

    PROCESSING -->|"processing acknowledgement"| EDGE

    classDef edge fill:#E8F1FF,stroke:#2563EB,color:#111827;
    classDef cloud fill:#ECFDF5,stroke:#059669,color:#111827;
    classDef data fill:#FFF7ED,stroke:#EA580C,color:#111827;
    classDef consumer fill:#F5F3FF,stroke:#7C3AED,color:#111827;
    classDef observe fill:#F3F4F6,stroke:#4B5563,color:#111827;

    class DEVICES,INTEGRATION,EDGE edge;
    class NETWORK,INGESTION,PROCESSING,SERVING cloud;
    class BUFFER,DATA data;
    class CONSUMERS consumer;
    class OBSERVE observe;
```

### Major communication paths

| From | To | Communication |
|---|---|---|
| Park IoT Devices | Device Integration | Raw readings and operational events |
| Device Integration | Redundant Local Hub | Normalized and enriched events |
| Local Hub | Durable Edge Buffer | Durable write before forwarding |
| Durable Edge Buffer | Secure Connectivity | Immediate critical events, scheduled normal data, and replayed events |
| Secure Connectivity | Cloud Ingestion | Protected branch-to-cloud transport |
| Cloud Ingestion | Data Platform | Original accepted events retained in Bronze |
| Cloud Ingestion | Processing | Critical or batch route based on priority |
| Processing | Data Platform | Trusted results and cleaned history |
| Data Platform | Serving | Approved Gold data |
| Serving | Consumers | APIs, subscriptions, operational updates, and reports |
| Cloud Processing | Local Hub | Successful-processing acknowledgement |

---

# Component-focused views

## 2. Device Integration detailed view

**Expanded component:** Device Integration  
**Abstract surroundings:** Park devices and Redundant Local Hub

```mermaid
flowchart LR
    DEVICES["Park IoT Devices<br/>abstract"]

    subgraph INTEGRATION["Device Integration: Detailed"]
        ENDPOINT["Protocol Endpoint"]
        ADAPTER["Device or Vendor Adapter"]
        NORMALIZE["Normalize Protocol and Payload"]
        SCHEMA["Schema and Basic Format Check"]
        CONTEXT["Add Park, Zone and Device Context"]
        IDENTITY["Add Event ID and Timestamp"]
        OUTPUT["Normalized Event Envelope"]
        REJECT[("Integration Rejected Events")]

        ENDPOINT --> ADAPTER
        ADAPTER --> NORMALIZE
        NORMALIZE --> SCHEMA
        SCHEMA -->|"valid"| CONTEXT
        SCHEMA -->|"invalid"| REJECT
        CONTEXT --> IDENTITY
        IDENTITY --> OUTPUT
    end

    HUB["Redundant Local Hub<br/>abstract"]
    OBSERVE["Observability<br/>abstract"]

    DEVICES -->|"equipment, environment,<br/>usage and safety events"| ENDPOINT
    OUTPUT -->|"normalized event"| HUB
    REJECT -. "failure details" .-> OBSERVE
    SCHEMA -. "validation metrics" .-> OBSERVE

    classDef focus fill:#DBEAFE,stroke:#1D4ED8,color:#111827;
    classDef abstract fill:#F3F4F6,stroke:#6B7280,color:#111827;
    classDef data fill:#FEF2F2,stroke:#DC2626,color:#111827;

    class ENDPOINT,ADAPTER,NORMALIZE,SCHEMA,CONTEXT,IDENTITY,OUTPUT focus;
    class DEVICES,HUB,OBSERVE abstract;
    class REJECT data;
```

### Component responsibility

- Accept device and vendor-specific protocols.
- Normalize payloads into a common event structure.
- perform basic schema and format validation.
- Add park, zone, device, event identity, and timestamp context.
- Send one normalized event stream to the local hub.

---

## 3. Redundant Local Hub detailed view

**Expanded component:** Redundant Local Hub  
**Abstract surroundings:** Device Integration, Secure Connectivity, Cloud Processing, and Observability

```mermaid
flowchart LR
    INTEGRATION["Device Integration<br/>abstract"]

    subgraph HUB["Redundant Local Hub: Detailed"]
        ENDPOINT["Hub Service Endpoint"]

        subgraph HA["High Availability"]
            HEALTH["Health Monitor"]
            FAILOVER["Failover Controller"]
            NODE_A["Hub Node A"]
            NODE_B["Hub Node B"]
            ACTIVE["Selected Active Processing"]

            HEALTH --> FAILOVER
            HEALTH -. "health check" .-> NODE_A
            HEALTH -. "health check" .-> NODE_B
            FAILOVER -->|"select healthy node"| ACTIVE
            NODE_A -. "eligible" .-> ACTIVE
            NODE_B -. "eligible" .-> ACTIVE
        end

        VALIDATE["Validate Event"]
        CLASSIFY{"Priority Classification"}
        ENVELOPE["Create Delivery Envelope"]
        PERSIST["Durable Write"]
        BUFFER[("Local Buffer<br/>at least 72 hours")]
        REJECT[("Local Rejected Event Store")]
        DELIVERY["Delivery Scheduler"]
        CHECKPOINT["Checkpoint and Delivery State"]
        ACK["Acknowledgement Handler"]

        ENDPOINT --> ACTIVE
        ACTIVE --> VALIDATE
        VALIDATE -->|"valid"| CLASSIFY
        VALIDATE -->|"invalid"| REJECT
        CLASSIFY --> ENVELOPE
        ENVELOPE --> PERSIST
        PERSIST --> BUFFER
        BUFFER --> DELIVERY
        BUFFER --> CHECKPOINT
        ACK --> CHECKPOINT
        CHECKPOINT -->|"mark acknowledged range delivered"| BUFFER
    end

    NETWORK["Secure Connectivity<br/>abstract"]
    CLOUD["Cloud Processing<br/>abstract"]
    OBSERVE["Observability<br/>abstract"]

    INTEGRATION -->|"normalized events"| ENDPOINT
    DELIVERY -->|"critical now,<br/>normal on schedule,<br/>replay after reconnect"| NETWORK
    NETWORK --> CLOUD
    CLOUD -->|"processing acknowledgement"| ACK

    HEALTH -. "node health" .-> OBSERVE
    BUFFER -. "capacity and backlog" .-> OBSERVE
    CHECKPOINT -. "delivery and replay state" .-> OBSERVE
    REJECT -. "validation failures" .-> OBSERVE

    classDef focus fill:#DBEAFE,stroke:#1D4ED8,color:#111827;
    classDef abstract fill:#F3F4F6,stroke:#6B7280,color:#111827;
    classDef data fill:#FFF7ED,stroke:#EA580C,color:#111827;
    classDef error fill:#FEF2F2,stroke:#DC2626,color:#111827;
    classDef decision fill:#FEF3C7,stroke:#D97706,color:#111827;

    class ENDPOINT,HEALTH,FAILOVER,NODE_A,NODE_B,ACTIVE,VALIDATE,ENVELOPE,PERSIST,DELIVERY,CHECKPOINT,ACK focus;
    class INTEGRATION,NETWORK,CLOUD,OBSERVE abstract;
    class BUFFER data;
    class REJECT error;
    class CLASSIFY decision;
```

### Component responsibility

- Present a single service endpoint while operating two hub nodes.
- Select one healthy node for active processing.
- Validate and classify events.
- Persist each event before forwarding.
- Retain at least 72 hours of expected data.
- Track delivery progress and process cloud acknowledgements.
- Replay undelivered events after reconnection.

### Design decision still required

The durable-buffer topology must be defined. The implementation may use shared storage, replicated node-local storage, or another durable arrangement. The selected option determines failover consistency, checkpoint ownership, and duplicate risk.

---

## 4. Secure connectivity and recovery detailed view

**Expanded component:** Secure Edge-to-Cloud Connectivity  
**Abstract surroundings:** Local Hub and Cloud Ingestion

```mermaid
flowchart LR
    HUB["Redundant Local Hub<br/>abstract"]

    subgraph CONNECTIVITY["Secure Connectivity and Recovery: Detailed"]
        SEND["Outbound Sender"]
        AVAILABILITY{"Connection Available?"}
        PRIMARY["Primary Network Connection"]
        PROBE["Connectivity Probe"]
        RECONNECT["Reconnection Detector"]
        LOAD["Load Last Successful Checkpoint"]
        REPLAY["Replay Undelivered Events"]
        TRANSPORT["Protected Transport Channel"]

        SEND --> AVAILABILITY
        AVAILABILITY -->|"available"| PRIMARY
        PRIMARY --> TRANSPORT
        AVAILABILITY -->|"unavailable"| PROBE
        PROBE --> RECONNECT
        RECONNECT -->|"not restored"| PROBE
        RECONNECT -->|"restored"| LOAD
        LOAD --> REPLAY
        REPLAY --> TRANSPORT
    end

    INGESTION["Cloud Ingestion<br/>abstract"]
    CHECKPOINT["Hub Checkpoint State<br/>abstract"]
    BUFFER["Hub Durable Buffer<br/>abstract"]
    OBSERVE["Observability<br/>abstract"]

    HUB -->|"send request"| SEND
    CHECKPOINT -->|"resume position"| LOAD
    BUFFER -->|"undelivered events"| REPLAY
    TRANSPORT -->|"critical, scheduled<br/>or replayed events"| INGESTION

    AVAILABILITY -. "network state" .-> OBSERVE
    REPLAY -. "replay progress and lag" .-> OBSERVE

    classDef focus fill:#D1FAE5,stroke:#059669,color:#111827;
    classDef abstract fill:#F3F4F6,stroke:#6B7280,color:#111827;
    classDef decision fill:#FEF3C7,stroke:#D97706,color:#111827;

    class SEND,PRIMARY,PROBE,RECONNECT,LOAD,REPLAY,TRANSPORT focus;
    class HUB,INGESTION,CHECKPOINT,BUFFER,OBSERVE abstract;
    class AVAILABILITY decision;
```

### Component responsibility

- Send critical events immediately when connectivity is available.
- Send normal events according to the scheduled path.
- Detect loss and restoration of connectivity.
- Resume from the last successful checkpoint.
- Replay the undelivered range through the same protected transport channel.

---

## 5. Cloud Ingestion detailed view

**Expanded component:** Cloud Ingestion  
**Abstract surroundings:** Connectivity, Processing, Bronze, and Observability

```mermaid
flowchart LR
    NETWORK["Secure Connectivity<br/>abstract"]

    subgraph INGESTION["Cloud Ingestion: Detailed"]
        ENTRY["Cloud Ingestion Endpoint"]
        AUTHN["Authenticate Source"]
        AUTHZ["Authorize Submission"]
        FORMAT["Envelope and Format Check"]
        ACCEPT["Accept Original Event"]
        ROUTER{"Priority Router"}
        DLQ[("Cloud Dead-Letter Store")]

        ENTRY --> AUTHN
        AUTHN -->|"authenticated"| AUTHZ
        AUTHN -->|"rejected"| DLQ
        AUTHZ -->|"authorized"| FORMAT
        AUTHZ -->|"rejected"| DLQ
        FORMAT -->|"valid"| ACCEPT
        FORMAT -->|"invalid"| DLQ
        ACCEPT --> ROUTER
    end

    BRONZE[("Bronze Layer<br/>abstract")]
    CRITICAL["Critical Processor<br/>abstract"]
    BATCH["Batch Processor<br/>abstract"]
    OBSERVE["Observability<br/>abstract"]

    NETWORK -->|"event envelope"| ENTRY
    ACCEPT -->|"retain original event"| BRONZE
    ROUTER -->|"critical"| CRITICAL
    ROUTER -->|"normal or replayed"| BATCH

    AUTHN -. "authentication outcome" .-> OBSERVE
    FORMAT -. "validation status" .-> OBSERVE
    ROUTER -. "route and throughput" .-> OBSERVE
    DLQ -. "rejected event status" .-> OBSERVE

    classDef focus fill:#D1FAE5,stroke:#059669,color:#111827;
    classDef abstract fill:#F3F4F6,stroke:#6B7280,color:#111827;
    classDef decision fill:#FEF3C7,stroke:#D97706,color:#111827;
    classDef error fill:#FEF2F2,stroke:#DC2626,color:#111827;

    class ENTRY,AUTHN,AUTHZ,FORMAT,ACCEPT focus;
    class NETWORK,BRONZE,CRITICAL,BATCH,OBSERVE abstract;
    class ROUTER decision;
    class DLQ error;
```

### Component responsibility

- Receive event envelopes from the edge connection.
- Authenticate the source and authorize submission.
- Check the envelope and basic format.
- Retain the accepted original event in Bronze.
- Route critical events to critical processing.
- Route normal and replayed events to batch processing.
- Quarantine rejected cloud-ingestion events.

---

## 6. Critical Processing detailed view

**Expanded component:** Critical Processing  
**Abstract surroundings:** Priority Router, Bronze, Gold, Hub, Consumers, and Observability

```mermaid
flowchart LR
    ROUTER["Priority Router<br/>abstract"]
    BRONZE[("Bronze Layer<br/>abstract")]

    subgraph CRITICAL["Critical Processing: Detailed"]
        RECEIVE["Receive Critical Event"]
        VALIDATE["Validate Critical Event"]
        DEDUP["Check Event ID and Deduplicate"]
        RULES["Apply Critical Business Rules"]
        TRUST{"Trusted Result?"}
        RESULT["Create Trusted Current Result"]
        FAILURE["Reject or Controlled Retry"]
        ACK["Create Processing Acknowledgement"]

        RECEIVE --> VALIDATE
        VALIDATE -->|"valid"| DEDUP
        VALIDATE -->|"invalid"| FAILURE
        DEDUP --> RULES
        RULES --> TRUST
        TRUST -->|"yes"| RESULT
        TRUST -->|"no"| FAILURE
        RESULT --> ACK
    end

    GOLD[("Gold Layer<br/>abstract")]
    HUB["Local Hub Delivery State<br/>abstract"]
    CONSUMERS["Park Systems and Approved<br/>External Consumers<br/>abstract"]
    OBSERVE["Observability<br/>abstract"]

    ROUTER -->|"critical event reference"| RECEIVE
    BRONZE -. "original event" .-> RECEIVE
    RESULT -->|"trusted current result"| GOLD
    GOLD -->|"near-real-time approved update"| CONSUMERS
    ACK -->|"processing succeeded"| HUB

    VALIDATE -. "validation status" .-> OBSERVE
    DEDUP -. "duplicate status" .-> OBSERVE
    RULES -. "latency and outcome" .-> OBSERVE
    FAILURE -. "failure and retry status" .-> OBSERVE

    classDef focus fill:#D1FAE5,stroke:#059669,color:#111827;
    classDef abstract fill:#F3F4F6,stroke:#6B7280,color:#111827;
    classDef decision fill:#FEF3C7,stroke:#D97706,color:#111827;
    classDef error fill:#FEF2F2,stroke:#DC2626,color:#111827;

    class RECEIVE,VALIDATE,DEDUP,RULES,RESULT,ACK focus;
    class ROUTER,BRONZE,GOLD,HUB,CONSUMERS,OBSERVE abstract;
    class TRUST decision;
    class FAILURE error;
```

### Component responsibility

- Validate critical events.
- Remove duplicates before applying critical rules.
- Produce a trusted current result for Gold.
- Return successful-processing acknowledgement to the edge delivery state.
- Record failures for controlled retry or rejection.

---

## 7. Batch Processing detailed view

**Expanded component:** Batch Processing  
**Abstract surroundings:** Priority Router, Bronze, Silver, Gold, Hub, Consumers, and Observability

```mermaid
flowchart LR
    ROUTER["Priority Router<br/>abstract"]
    BRONZE[("Bronze Layer<br/>abstract")]

    subgraph BATCH["Batch Processing: Detailed"]
        READ["Read Scheduled or Replayed Batch"]
        VALIDATE["Validate Records"]
        DEDUP["Deduplicate by Event Identity"]
        CLEAN["Clean and Standardize"]
        HISTORY["Build Historical Records"]
        CURRENT["Create Current-State Views"]
        SUMMARY["Create Scheduled Summaries"]
        FAILURE[("Batch Rejected Records")]
        ACK["Create Batch Acknowledgement"]

        READ --> VALIDATE
        VALIDATE -->|"valid"| DEDUP
        VALIDATE -->|"invalid"| FAILURE
        DEDUP --> CLEAN
        CLEAN --> HISTORY
        HISTORY --> CURRENT
        HISTORY --> SUMMARY
        CURRENT --> ACK
        SUMMARY --> ACK
    end

    SILVER[("Silver Layer<br/>abstract")]
    GOLD[("Gold Layer<br/>abstract")]
    HUB["Hub Checkpoint State<br/>abstract"]
    CONSUMERS["Reports and Approved<br/>Consumers<br/>abstract"]
    OBSERVE["Observability<br/>abstract"]

    ROUTER -->|"normal or replayed events"| READ
    BRONZE -. "original event batch" .-> READ
    HISTORY -->|"cleaned history"| SILVER
    SILVER -. "validated history" .-> CURRENT
    SILVER -. "validated history" .-> SUMMARY
    CURRENT -->|"trusted current view"| GOLD
    SUMMARY -->|"trusted summaries"| GOLD
    GOLD -->|"approved scheduled output"| CONSUMERS
    ACK -->|"advance checkpoint"| HUB

    VALIDATE -. "quality results" .-> OBSERVE
    DEDUP -. "duplicate metrics" .-> OBSERVE
    FAILURE -. "rejected records" .-> OBSERVE
    ACK -. "batch outcome and replay lag" .-> OBSERVE

    classDef focus fill:#D1FAE5,stroke:#059669,color:#111827;
    classDef abstract fill:#F3F4F6,stroke:#6B7280,color:#111827;
    classDef error fill:#FEF2F2,stroke:#DC2626,color:#111827;

    class READ,VALIDATE,DEDUP,CLEAN,HISTORY,CURRENT,SUMMARY,ACK focus;
    class ROUTER,BRONZE,SILVER,GOLD,HUB,CONSUMERS,OBSERVE abstract;
    class FAILURE error;
```

### Component responsibility

- Read scheduled and replayed batches.
- Validate and deduplicate records.
- Clean events and build historical records in Silver.
- Produce current-state views and summaries in Gold.
- Acknowledge successful processing so the local checkpoint can advance.

---

## 8. Medallion Data Platform detailed view

**Expanded component:** Bronze, Silver, and Gold Data Platform  
**Abstract surroundings:** Cloud Ingestion, Processing, Serving, and Observability

```mermaid
flowchart LR
    INGESTION["Cloud Ingestion<br/>abstract"]
    CRITICAL["Critical Processing<br/>abstract"]
    BATCH["Batch Processing<br/>abstract"]

    subgraph MEDALLION["Medallion Data Platform: Detailed"]
        subgraph B["Bronze"]
            BRONZE[("Original Immutable Events")]
            RAW["Original Payload"]
            META["Source and Ingestion Metadata"]
            BRONZE --> RAW
            BRONZE --> META
        end

        subgraph S["Silver"]
            SILVER[("Validated and Cleaned History")]
            STANDARD["Standardized Records"]
            QUALITY["Data-Quality Status"]
            HISTORY["Historical Event View"]
            SILVER --> STANDARD
            SILVER --> QUALITY
            SILVER --> HISTORY
        end

        subgraph G["Gold"]
            GOLD[("Trusted Serving Data")]
            CURRENT["Trusted Current State"]
            SUMMARIES["Approved Summaries"]
            GOLD --> CURRENT
            GOLD --> SUMMARIES
        end

        BRONZE -->|"batch cleansing path"| SILVER
        SILVER -->|"aggregation and current views"| GOLD
    end

    SERVING["Serving and Distribution<br/>abstract"]
    OBSERVE["Observability<br/>abstract"]

    INGESTION -->|"accepted original event"| BRONZE
    BRONZE -->|"critical event source"| CRITICAL
    BRONZE -->|"normal and replay source"| BATCH
    CRITICAL -->|"trusted critical result"| GOLD
    BATCH -->|"cleaned historical record"| SILVER
    BATCH -->|"trusted current view and summary"| GOLD
    GOLD -->|"approved data"| SERVING

    BRONZE -. "ingestion completeness" .-> OBSERVE
    SILVER -. "validation and quality" .-> OBSERVE
    GOLD -. "freshness and trust status" .-> OBSERVE

    classDef bronze fill:#FFEDD5,stroke:#C2410C,color:#111827;
    classDef silver fill:#F3F4F6,stroke:#6B7280,color:#111827;
    classDef gold fill:#FEF3C7,stroke:#D97706,color:#111827;
    classDef abstract fill:#E5E7EB,stroke:#4B5563,color:#111827;

    class BRONZE,RAW,META bronze;
    class SILVER,STANDARD,QUALITY,HISTORY silver;
    class GOLD,CURRENT,SUMMARIES gold;
    class INGESTION,CRITICAL,BATCH,SERVING,OBSERVE abstract;
```

### Component responsibility

- **Bronze:** retain the original accepted event and its ingestion context.
- **Silver:** retain validated, standardized, and cleaned historical data.
- **Gold:** retain trusted current data and summaries for controlled serving.
- Support the fast critical route to Gold and the historical batch route through Silver to Gold.

---

## 9. Serving and Distribution detailed view

**Expanded component:** Serving and Distribution  
**Abstract surroundings:** Gold, Consumers, and Observability

```mermaid
flowchart LR
    GOLD[("Gold Layer<br/>abstract")]

    subgraph SERVING["Serving and Distribution: Detailed"]
        REQUEST["Gold Publication Request"]
        POLICY["Approval and Policy Checks"]
        DECISION{"Approved for Consumer?"}
        API["Developer API"]
        EVENTS["Approved Event Subscriptions"]
        REPORTING["Reports and Analytics Access"]
        DENIED["Deny and Record Decision"]
        AUDIT["Access and Publication Audit"]

        REQUEST --> POLICY
        POLICY --> DECISION
        DECISION -->|"yes: API"| API
        DECISION -->|"yes: event"| EVENTS
        DECISION -->|"yes: reporting"| REPORTING
        DECISION -->|"no"| DENIED
        API --> AUDIT
        EVENTS --> AUDIT
        REPORTING --> AUDIT
        DENIED --> AUDIT
    end

    PARK["Park Operational Systems<br/>abstract"]
    EXTERNAL["Approved External Consumers<br/>abstract"]
    USERS["Reporting and Analytics Users<br/>abstract"]
    OBSERVE["Observability<br/>abstract"]

    GOLD -->|"trusted current data<br/>and summaries"| REQUEST
    API -->|"approved data response"| EXTERNAL
    EVENTS -->|"near-real-time update"| PARK
    EVENTS -->|"approved subscription event"| EXTERNAL
    REPORTING -->|"approved report or dataset"| USERS
    AUDIT -. "access and decision trail" .-> OBSERVE

    classDef focus fill:#D1FAE5,stroke:#059669,color:#111827;
    classDef abstract fill:#F3F4F6,stroke:#6B7280,color:#111827;
    classDef decision fill:#FEF3C7,stroke:#D97706,color:#111827;
    classDef denied fill:#FEF2F2,stroke:#DC2626,color:#111827;

    class REQUEST,POLICY,API,EVENTS,REPORTING,AUDIT focus;
    class GOLD,PARK,EXTERNAL,USERS,OBSERVE abstract;
    class DECISION decision;
    class DENIED denied;
```

### Component responsibility

- Apply approval and policy checks before publishing Gold data.
- Expose approved data through the Developer API.
- Deliver approved event subscriptions to park systems and external consumers.
- Provide controlled reporting and analytics access.
- Record publication, access, approval, and denial decisions.

---

## 10. Observability detailed view

**Expanded component:** Monitoring, Audit, Metrics, and Alerting  
**Abstract surroundings:** All operational architecture components

```mermaid
flowchart TB
    EDGE["Redundant Local Hub<br/>abstract"]
    NETWORK["Secure Connectivity<br/>abstract"]
    INGESTION["Cloud Ingestion<br/>abstract"]
    CRITICAL["Critical Processing<br/>abstract"]
    BATCH["Batch Processing<br/>abstract"]
    DATA["Bronze, Silver and Gold<br/>abstract"]
    SERVING["Serving and Distribution<br/>abstract"]

    subgraph OBSERVE["Observability: Detailed"]
        COLLECT["Telemetry Collection"]
        METRICS["Operational Metrics"]
        LOGS["Structured Logs"]
        TRACES["End-to-End Event Traces"]
        AUDIT["Security and Access Audit"]
        HEALTH["Health and Availability View"]
        QUALITY["Data Freshness and Quality View"]
        ALERTS["Alerts and Notifications"]
        DASHBOARD["Operational Dashboard"]

        COLLECT --> METRICS
        COLLECT --> LOGS
        COLLECT --> TRACES
        COLLECT --> AUDIT
        METRICS --> HEALTH
        LOGS --> HEALTH
        TRACES --> QUALITY
        AUDIT --> DASHBOARD
        HEALTH --> DASHBOARD
        QUALITY --> DASHBOARD
        HEALTH --> ALERTS
        QUALITY --> ALERTS
    end

    EDGE -->|"node health, buffer use,<br/>delivery checkpoint"| COLLECT
    NETWORK -->|"connection state and replay lag"| COLLECT
    INGESTION -->|"authentication, rejection<br/>and throughput"| COLLECT
    CRITICAL -->|"critical latency and outcome"| COLLECT
    BATCH -->|"batch status, duplicates<br/>and replay progress"| COLLECT
    DATA -->|"layer freshness and quality"| COLLECT
    SERVING -->|"access and approval trail"| COLLECT

    classDef focus fill:#E5E7EB,stroke:#4B5563,color:#111827;
    classDef abstract fill:#F9FAFB,stroke:#9CA3AF,color:#111827;

    class COLLECT,METRICS,LOGS,TRACES,AUDIT,HEALTH,QUALITY,ALERTS,DASHBOARD focus;
    class EDGE,NETWORK,INGESTION,CRITICAL,BATCH,DATA,SERVING abstract;
```

### Proposed monitoring coverage

- Hub-node health and failover status
- Buffer utilization and expected remaining capacity
- Network state and time since disconnection
- Replay backlog, progress, and lag
- Authentication and ingestion rejection outcomes
- Critical-event processing latency and status
- Batch status, duplicate detection, and rejected records
- Bronze ingestion completeness
- Silver data-quality status
- Gold freshness and trusted-output status
- Serving approval, access, and audit history

---