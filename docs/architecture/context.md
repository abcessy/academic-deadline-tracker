---
  config:
    theme: redux
---
flowchart TB
    %% Define styles
    classDef person fill:#08427B,stroke:#052E56,color:#fff,stroke-width:2px,rx:8,ry:8
    classDef system fill:#1168BD,stroke:#0B4884,color:#fff,stroke-width:2px,rx:8,ry:8
    classDef external fill:#999999,stroke:#6B6B6B,color:#fff,stroke-width:2px,rx:8,ry:8

    %% Actors
    Student["👤 Student<br/><i>s7"]:::person
    Instructor["👤 Instructor<br/><i>s8"]:::person

    %% Main system
    ADT["🎯 Academic Deadline Tracker<br/><i>s9"]:::system

    %% External systems
    GoogleAuth["🔐 Google Authentication<br/><i>s10"]:::external
    EmailService["📧 Email Service<br/><i>s11"]:::external
    PushService["🔔 Push Notification Service<br/><i>s12"]:::external

    %% Relationships
    Student -->|"Registers, logs in, adds deadlines,<br/>views upcoming tasks, marks complete"| ADT
    Instructor -->|"Provides subject<br/>deadline information"| ADT
    ADT -->|"Authenticates users<br/>via OAuth 2.0"| GoogleAuth
    ADT -->|"Sends reminder emails<br/>via SMTP"| EmailService
    ADT -->|"Sends push notifications<br/>via API"| PushService

    %% Force layout to prevent overlap
    linkStyle default stroke:#666,stroke-width:2px
