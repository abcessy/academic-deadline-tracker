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
Compose
Write to CAPSTONE 2 GROUPINGERS
