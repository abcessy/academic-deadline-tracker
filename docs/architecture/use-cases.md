# UML Use Case Diagram — Academic Deadline Tracker

**Diagram Type:** UML Use Case Diagram  
**Scope:** Every actor from the context diagram and 10 goal-level use cases from the MVP feature list  
**Audience:** Product owner, QA team  
**Risk Reduced:** Missing user goals and scope misalignment  

```mermaid
flowchart LR
    classDef actor fill:#08427B,stroke:#052E56,color:#fff,stroke-width:2px
    classDef usecase fill:#E1F5FE,stroke:#0288D1,color:#000,stroke-width:2px
    classDef external fill:#999999,stroke:#6B6B6B,color:#fff,stroke-width:2px

    Student(("Student")):::actor
    Instructor(("Instructor")):::actor

    GoogleAuth["Google Auth"]:::external
    EmailService["Email Service"]:::external
    PushService["Push Service"]:::external

    subgraph System["Academic Deadline Tracker"]
        UC1["Register Account"]:::usecase
        UC2["Log In"]:::usecase
        UC3["Add Deadline"]:::usecase
        UC4["View Upcoming Deadlines"]:::usecase
        UC5["Edit Deadline"]:::usecase
        UC6["Delete Deadline"]:::usecase
        UC7["Mark Task Complete"]:::usecase
        UC8["Set Reminder"]:::usecase
        UC9["View Deadline by Subject"]:::usecase
        UC10["Receive Reminder"]:::usecase
    end

    Student --> UC1
    Student --> UC2
    Student --> UC3
    Student --> UC4
    Student --> UC5
    Student --> UC6
    Student --> UC7
    Student --> UC8
    Student --> UC9
    Student --> UC10

    Instructor --> UC3

    UC1 --> GoogleAuth
    UC2 --> GoogleAuth
    UC8 --> EmailService
    UC8 --> PushService
    UC10 --> EmailService
    UC10 --> PushService
```

**Key:**
- **Dark blue circles** = Actors (users or external systems)
- **Light blue boxes** = Use cases (goal-level features, named verb + object)
- **Gray boxes** = External systems
- **Arrows** = Association between actor and use case

**Use Case → MVP Feature Mapping:**

| # | Use Case | MVP Feature |
|---|----------|-------------|
| 1 | Register Account | Login with Google |
| 2 | Log In | Login with Google |
| 3 | Add Deadline | Add deadline |
| 4 | View Upcoming Deadlines | View deadlines |
| 5 | Edit Deadline | Edit deadline |
| 6 | Delete Deadline | Delete deadline |
| 7 | Mark Task Complete | Mark complete |
| 8 | Set Reminder | Set reminder |
| 9 | View Deadline by Subject | Organize by subject |
| 10 | Receive Reminder | Receive reminder |

**Owner:** Princess Mae G. Morata  
**Reviewer:** Wenly M. Caalam
