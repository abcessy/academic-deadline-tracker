# UML Activity Diagram — Academic Deadline Tracker

**Diagram Type:** UML Activity Diagram (with swimlanes)  
**Scope:** Core workflow — Student adds a deadline and receives a reminder  
**Audience:** Business analysts, developers  
**Risk Reduced:** Process gaps and unclear responsibilities  

```mermaid
flowchart TD
    classDef student fill:#E3F2FD,stroke:#1976D2,color:#000,stroke-width:2px
    classDef system fill:#FFF3E0,stroke:#F57C00,color:#000,stroke-width:2px
    classDef external fill:#F3E5F5,stroke:#7B1FA2,color:#000,stroke-width:2px
    classDef decision fill:#FFEBEE,stroke:#C62828,color:#000,stroke-width:2px
    classDef startend fill:#C8E6C9,stroke:#2E7D32,color:#000,stroke-width:2px

    Start([Start]):::startend --> A[Student opens app]:::student
    A --> B{Logged in?}:::decision
    B -- No --> C[Student logs in via Google Auth]:::student
    C --> D{Login successful?}:::decision
    D -- No --> E[Show error message]:::system
    E --> C
    D -- Yes --> F[Student views dashboard]:::student
    B -- Yes --> F

    F --> G[Student clicks Add Deadline]:::student
    G --> H[Student enters deadline details]:::student
    H --> I{All required fields filled?}:::decision
    I -- No --> J[Show validation errors]:::system
    J --> H
    I -- Yes --> K[System saves deadline to database]:::system
    K --> L[System displays confirmation]:::system
    L --> M{Set reminder?}:::decision
    M -- Yes --> N[Student sets reminder time]:::student
    N --> O[System schedules reminder]:::system
    O --> P[System sends confirmation]:::system
    M -- No --> P
    P --> Q[Student views upcoming deadlines]:::student
    Q --> R{Deadline approaching?}:::decision
    R -- Yes --> S[System sends reminder via email/push]:::external
    S --> T[Student receives reminder]:::student
    T --> U[Student marks task complete]:::student
    R -- No --> V[Student continues using app]:::student
    U --> End([End]):::startend
    V --> End
```

**Swimlane Legend:**

| Swimlane | Nodes | Responsibility |
|----------|-------|----------------|
| **Student** | A, C, F, G, H, N, Q, T, U, V | All user actions and decisions |
| **System** | B, D, E, I, J, K, L, M, O, P, R | All automated processing and validation |
| **External Services** | S (Email/Push) | Third-party notification delivery |

**Key:**
- **Green ovals** = Start / End nodes
- **Red diamonds** = Decision nodes with guards (labelled on every outgoing arrow)
- **Blue rectangles** = Student actions
- **Orange rectangles** = System actions
- **Purple rectangles** = External service actions

**Owner:** Princess Mae G. Morata  
**Reviewer:** Vanessa Jhane G. Guda
