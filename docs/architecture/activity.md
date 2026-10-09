flowchart TB
    %% Define Styles
    classDef person fill:#08427B,stroke:#073B6F,color:#fff,stroke-width:2px,rx:5,ry:5;
    classDef system fill:#1168BD,stroke:#0B5394,color:#fff,stroke-width:2px,rx:5,ry:5;
    classDef external fill:#999999,stroke:#6B6B6B,color:#fff,stroke-width:2px,rx:5,ry:5;
    classDef label fill:none,stroke:none,color:#000,font-size:12px;

    %% Nodes
    Student["<b>Student</b><br/><i>[person]</i><br/>College student who tracks academic deadlines"]:::person
    Instructor["<b>Instructor</b><br/><i>[person]</i><br/>Provides deadline information for subjects"]:::person
    
    System["<b>Academic Deadline Tracker</b><br/><i>[system]</i><br/>A centralized web application that allows students to organize,<br/>view, and receive reminders for academic deadlines across multiple subjects"]:::system
    
    Email["<b>Email Service</b><br/><i>[external system]</i><br/>Sends email reminders for upcoming deadlines"]:::external
    Push["<b>Push Notification Service</b><br/><i>[external system]</i><br/>Delivers browser/mobile push notifications"]:::external
    Auth["<b>Google Authentication</b><br/><i>[external system]</i><br/>Provides OAuth 2.0 login for students"]:::external

    %% Relationships (Arrows)
    Student -->|Registers, logs in, adds deadlines,<br/>views upcoming deadlines| System
    Instructor -->|Provides subject details<br/>and deadline information| System
    
    System -->|Sends reminder<br/>emails via SMTP| Email
    System -->|Sends push notifications via API| Push
    System -->|Authenticates users via OAuth 2.0| Auth

    %% Layout adjustments (to keep top and bottom rows somewhat aligned)
    subgraph Top [ ]
        direction LR
        Student
        Instructor
    end
    
    subgraph Bottom [ ]
        direction LR
        Email
        Push
        Auth
    end
    
    style Top fill:none,stroke:none
    style Bottom fill:none,stroke:none
ate developer sham
# UML Activity Diagram — Academic Deadline Tracker

*Diagram Type:* UML Activity Diagram (with swimlanes)  
*Scope:* Core workflow — Student adds a deadline and receives a reminder  
*Audience:* Business analysts, developers  
*Risk Reduced:* Process gaps and unclear responsibilities  

mermaid
flowchart TD
    Start([Start]) --> A[Student opens app]
    A --> B{Logged in?}
    B -- No --> C[Student logs in via Google Auth]
    C --> D{Login successful?}
    D -- No --> E[Show error message]
    E --> C
    D -- Yes --> F[Student views dashboard]
    B -- Yes --> F

    F --> G[Student clicks Add Deadline]
    G --> H[Student enters deadline details]
    H --> I{All required fields filled?}
    I -- No --> J[Show validation errors]
    J --> H
    I -- Yes --> K[System saves deadline to database]
    K --> L[System displays confirmation]
    L --> M{Set reminder?}
    M -- Yes --> N[Student sets reminder time]
    N --> O[System schedules reminder]
    O --> P[System sends confirmation]
    M -- No --> P
    P --> Q[Student views upcoming deadlines]
    Q --> R{Deadline approaching?}
    R -- Yes --> S[System sends reminder via email/push]
    S --> T[Student receives reminder]
    T --> U[Student marks task complete]
    R -- No --> V[Student continues using app]
    U --> End([End])
    V --> End

*Swimlane Legend:*

| Swimlane | Nodes | Responsibility |
|----------|-------|----------------|
| *Student* | A, C, F, G, H, N, Q, T, U | All user actions and decisions |
| *System* | B, D, E, I, J, K, L, M, O, P, R, S | All automated processing and validation |
| *External Services* | C (Google Auth), S (Email/Push) | Third-party authentication and notification delivery |

*Key:*
- *Diamond* = Decision node with guards (labelled on every outgoing arrow)
- *Rounded rectangle* = Action/Activity
- *Start/End* = Initial and final nodes
- *Swimlanes* = Student | System | External Services

*Owner:* Princess Mae G. Morata  
*Reviewer:* Vanessa Jhane G. Guda
ate developer sham
sequenceDiagram
    autonumber
    actor Student
    participant WebApp as Web App (Next.js)
    participant API as API (Express)
    participant Google as Google Auth
    participant DB as PostgreSQL

    Student->>WebApp: Click "Login with Google"
    WebApp->>Google: Redirect to OAuth consent
    Google-->>Student: Show consent screen
    Student->>Google: Grant permission
    Google-->>WebApp: Redirect with authorization code
    WebApp->>API: POST /auth/google { code }
    API->>Google: Exchange code for tokens
    Google-->>API: Return access token + ID token
    API->>API: Validate ID token
    alt Token valid
        API->>DB: Find or create user
        DB-->>API: Return user record
        API-->>WebApp: Return JWT session token
        WebApp-->>Student: Redirect to dashboard
    else Token invalid
        API-->>WebApp: Return 401 Unauthorized
        WebApp-->>Student: Show login error
    end
    *Key:*
- *Solid arrow (→)* = Synchronous message
- *Dashed arrow (-->>)* = Reply/Return message
- *alt* = Alternative flow (branch)
- *Lifelines* = Student, Web App, API, Google Auth, PostgreSQL

*Why this is the riskiest flow:* It involves an external system (Google), security tokens, database writes, and session management. A failure here blocks all other features.

*Owner:* Shamel Joy G. Fugio  
*Reviewer:* Wenly M. Caalam
Compose
Write to CAPSTONE 2 GROUPINGERS
