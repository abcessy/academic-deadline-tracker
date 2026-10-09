# C4 System Context Diagram — Academic Deadline Tracker

**Diagram Type:** C4 Level 1 — System Context  
**Scope:** The Academic Deadline Tracker as a single system, all user roles, and all external systems  
**Audience:** All stakeholders  
**Risk Reduced:** Scope creep and missing external dependencies  

```mermaid
flowchart TB
    classDef person fill:#08427B,stroke:#052E56,color:#fff,stroke-width:2px
    classDef system fill:#1168BD,stroke:#0B4884,color:#fff,stroke-width:2px
    classDef external fill:#999999,stroke:#6B6B6B,color:#fff,stroke-width:2px

    Student["👤 Student<br/>College student who tracks<br/>academic deadlines"]:::person
    Instructor["👤 Instructor<br/>Provides deadline information<br/>for subjects"]:::person

    ADT["🎯 Academic Deadline Tracker<br/>Centralized deadline manager<br/>for college students"]:::system

    GoogleAuth["🔐 Google Authentication<br/>OAuth 2.0 login provider"]:::external
    EmailService["📧 Email Service<br/>Sends email reminders"]:::external
    PushService["🔔 Push Notification Service<br/>Delivers push notifications"]:::external

    Student -->|"Registers, logs in, adds deadlines,<br/>views upcoming tasks, marks complete"| ADT
    Instructor -->|"Provides subject<br/>deadline information"| ADT
    ADT -->|"Authenticates users<br/>via OAuth 2.0"| GoogleAuth
    ADT -->|"Sends reminder emails<br/>via SMTP"| EmailService
    ADT -->|"Sends push notifications<br/>via API"| PushService
```

**Key:**
- **Blue box** = Your MVP (one box)
- **Dark blue boxes** = Human user roles
- **Gray boxes** = External systems your MVP depends on
- **Arrows** = Labelled with what each actor/system is trying to do

**Owner:** Vanessa Jhane G. Guda  
**Reviewer:** Princess Mae G. Morata
