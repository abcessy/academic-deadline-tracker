# C4 Container Diagram — Academic Deadline Tracker

**Diagram Type:** C4 Level 2 — Container  
**Scope:** Every separately deployable unit inside the Academic Deadline Tracker  
**Audience:** Development team, technical stakeholders  
**Risk Reduced:** Technology mismatch and deployment confusion  

```mermaid
flowchart TB
    classDef person fill:#08427B,stroke:#052E56,color:#fff,stroke-width:2px
    classDef container fill:#1168BD,stroke:#0B4884,color:#fff,stroke-width:2px
    classDef database fill:#1168BD,stroke:#0B4884,color:#fff,stroke-width:2px
    classDef external fill:#999999,stroke:#6B6B6B,color:#fff,stroke-width:2px

    Student["Student<br/>College student who tracks<br/>academic deadlines"]:::person

    subgraph System["Academic Deadline Tracker"]
        WebApp["Web Application<br/>Next.js (React)<br/>Provides the user interface"]:::container
        APIApp["API Application<br/>Node.js / Express<br/>Business logic and auth"]:::container
        Database["Database<br/>PostgreSQL<br/>Stores all data"]:::database
        ReminderSvc["Reminder Service<br/>Node.js / Cron<br/>Schedules reminders"]:::container
    end

    GoogleAuth["Google Authentication<br/>OAuth 2.0 login provider"]:::external
    EmailService["Email Service<br/>Sends reminder emails"]:::external
    PushService["Push Notification Service<br/>Delivers push notifications"]:::external

    Student -->|"Uses HTTPS"| WebApp
    WebApp -->|"Calls API JSON/HTTPS"| APIApp
    APIApp -->|"Reads/writes SQL/TCP"| Database
    APIApp -->|"Triggers jobs Internal/HTTP"| ReminderSvc
    ReminderSvc -->|"Sends emails SMTP"| EmailService
    ReminderSvc -->|"Sends notifications HTTPS/API"| PushService
    APIApp -->|"Validates tokens OAuth 2.0"| GoogleAuth
```

**Key:**
- **Blue boxes inside boundary** = Containers (separately deployable units)
- **Database box** = Data store
- **Gray boxes** = External systems
- **Arrows** = Labelled with intent and protocol

**Statement:** The Next.js app is drawn as **one container** because we use Next.js as a single full-stack application with API routes, not a separate frontend/backend split.

**Owner:** Vanessa Jhane G. Guda  
**Reviewer:** Shamel Joy G. Fugio
