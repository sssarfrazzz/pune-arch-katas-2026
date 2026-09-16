# Diagram Source Backup

This file preserves the editable Mermaid source for the PNG diagrams embedded in the root [README](../README.md). The PNG files are the presentation assets; these definitions are retained as backup source.

| Diagram | PNG |
|---|---|
| Estate as Operational Units | [Estate-as-Units.png](./Estate-as-Units.png) |
| Operational Unit Evidence Flow | [Unit-Economics.png](./Unit-Economics.png) |
| Actors and Access Model | [Roles.png](./Roles.png) |

## Estate as Operational Units

```mermaid
flowchart TD
    subgraph AP[" "]
        direction TB
        subgraph Header[" "]
            direction LR
            ESTATE["Estate"]
            DESC["Each enclosure or ride is an abstract unit with its own visitor management, health monitoring, and person in charge.<br/>All units can be aggregated at the overall estate level."]
            ESTATE --- DESC
        end
        subgraph Row1[" "]
            direction LR
            RC["Roller Coaster"]
            AQ["Aquarium"]
            LE["Lion Enclosure"]
            MH["Magic House"]
        end
        subgraph Row2[" "]
            direction LR
            FW["Ferris Wheel"]
            WR["Water Rapids"]
            HC["Haunted Castle"]
            DZ["Dinosaur Zone"]
        end
        subgraph Row3[" "]
            direction LR
            ST["Sky Tower"]
            PB["Pirate Bay"]
            SA["Safari Train"]
            SD["Space Dome"]
        end
    end

    classDef colorOne fill:#176B73,stroke:#0E464C,color:#FFFFFF
    classDef colorTwo fill:#8A5A00,stroke:#5C3C00,color:#FFFFFF
    classDef colorThree fill:#A12B3A,stroke:#6E1D28,color:#FFFFFF
    classDef description fill:none,stroke:none
    classDef estate fill:none,stroke:none,font-size:150%,font-weight:bold

    linkStyle 0 stroke:transparent,fill:none
    class RC,MH,WR,ST colorOne
    class AQ,FW,DZ,PB colorTwo
    class LE,HC,SA,SD colorThree
    class DESC description
    class ESTATE estate
    style AP fill:#EAF6F6,stroke:#2A6F73,stroke-width:2px
```

## Operational Unit Evidence Flow

```mermaid
flowchart TB
    subgraph Layers["Operational Unit Layers"]
        direction TB

        subgraph L3["Attendance Analytics"]
            direction LR
            IOTOS1(["IOT-OS"])
            PERSON1(["Operator"])
            IOT1["IoT Attendance Device"]
            Visitor --> |Entry/Exit| IOT1
            IOT1 -->|Attendance| PERSON1
            IOT1 -->|Attendance| IOTOS1
        end

        subgraph L2["Health Analytics"]
            direction LR
            IOTOS2(["IOT-OS"])
            PERSON2(["Operator/Specialist"])
            IOT2["IoT Health Device"]
            RIDE2["Ride/Animal"]
            IOT2 -->|Health Indicators| PERSON2
            IOT2 -->|Health Indicators| IOTOS2
            RIDE2 -->|Sensors| IOT2
        end

        subgraph L1["Operator/Specialist Activities"]
            direction LR
            WORKOS(["WORK-OS"])
            PERSON3(["Operator/Specialist"])
            RIDE3["Ride/Animal"]
            WORKOS -->|WorkItem| PERSON3
            PERSON3 -->|Updates| WORKOS
            PERSON3 -->|repair / feed| RIDE3
        end

        L3 ~~~ L2
        L2 ~~~ L1
    end

    style Layers fill:#F7FAFC,stroke:#718096,stroke-width:2px
    style L3 fill:#E8F1FF,stroke:#2B6CB0,stroke-width:2px
    style L2 fill:#E6F6EE,stroke:#2F855A,stroke-width:2px
    style L1 fill:#FFF4D6,stroke:#B7791F,stroke-width:2px
```

## Actors and Access Model

```mermaid
flowchart LR
    Visitors[Visitors and Guardians]
    Staff[Estate Staff and Specialists]
    Governance[Auditors Regulators and Governance]
    MonetizationPartners[Developers Researchers]
    OperationalPartners[OEMs and Service Partners]
    Platform[Autonomous Estate Management Platform]
    Commerce[Ticketing Commerce and Payment]
    Identity[Identity Provider]
    Enterprise[HRMS Payroll ERP Procurement Inventory EAM]
    Clinical[Veterinary and Laboratory Systems]
    External[Weather Notification Service Desk and Parts]
    Safety[Independent Certified Safety Systems]

    Visitors --> Platform
    Platform --> Staff
    Governance <--> Platform
    MonetizationPartners <--> Platform
    OperationalPartners <--> Platform
    Platform <--> Commerce
    Platform <--> Identity
    Platform <--> Enterprise
    Platform <--> Clinical
    Platform <--> External
    Platform --> Safety
```