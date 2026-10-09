# C4 System Context Diagram — Academic Deadline Tracker

**Diagram Type:** C4 Level 1 — System Context  
**Scope:** The Academic Deadline Tracker as a single system, all user roles, and all external systems  
**Audience:** All stakeholders  
**Risk Reduced:** Scope creep and missing external dependencies  

```mermaid
C4Context
    title C4 System Context Diagram — Academic Deadline Tracker

    Person(student, "Student", "College student who tracks academic deadlines")
    Person(instructor, "Instructor", "Provides deadline information for subjects")

    System(adt, "Academic Deadline Tracker", "A centralized web application that allows students to organize, view, and receive reminders for academic deadlines across multiple subjects")

    System_Ext(emailService, "Email Service", "Sends email reminders for upcoming deadlines")
    System_Ext(pushService, "Push Notification Service", "Delivers browser/mobile push notifications")
    System_Ext(googleAuth, "Google Authentication", "Provides OAuth 2.0 login for students")

    Rel(student, adt, "Registers, logs in, adds deadlines, views upcoming tasks, marks tasks complete")
    Rel(instructor, adt, "Provides subject deadline information")
    Rel(adt, emailService, "Sends reminder emails via SMTP")
    Rel(adt, pushService, "Sends push notifications via API")
    Rel(adt, googleAuth, "Authenticates users via OAuth 2.0")

    UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")
```

**Key:**
- **Person** = Human user role
- **System** = Your MVP (one box)
- **System_Ext** = External system your MVP depends on
- **Rel** = Labelled relationship showing intent

**Owner:** Vanessa Jhane G. Guda  
**Reviewer:** Princess Mae G. Morata
