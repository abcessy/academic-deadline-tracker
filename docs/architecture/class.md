# UML Class Diagram — Academic Deadline Tracker

**Diagram Type:** UML Class Diagram  
**Scope:** 7 domain classes with typed attributes, multiplicities, and status enumerations  
**Audience:** Developers, database designers  
**Risk Reduced:** Data model inconsistencies and missing relationships  

```mermaid
classDiagram
    class User {
        +UUID id
        +String email
        +String name
        +String googleId
        +DateTime createdAt
        +DateTime updatedAt
        +login()
        +logout()
        +addDeadline()
    }

    class Subject {
        +UUID id
        +String name
        +String code
        +String instructor
        +UUID userId
        +DateTime createdAt
    }

    class Deadline {
        +UUID id
        +String title
        +String description
        +DateTime dueDate
        +DeadlineStatus status
        +DeadlineType type
        +UUID subjectId
        +UUID userId
        +DateTime createdAt
        +DateTime updatedAt
        +markComplete()
        +updateDetails()
    }

    class Reminder {
        +UUID id
        +DateTime remindAt
        +ReminderChannel channel
        +Boolean isSent
        +UUID deadlineId
        +DateTime createdAt
        +schedule()
        +send()
    }

    class DeadlineStatus {
        <<enumeration>>
        PENDING
        IN_PROGRESS
        COMPLETED
        OVERDUE
    }

    class DeadlineType {
        <<enumeration>>
        ASSIGNMENT
        PROJECT
        EXAM
        QUIZ
        OTHER
    }

    class ReminderChannel {
        <<enumeration>>
        EMAIL
        PUSH
        BOTH
    }

    User "1" --> "0..*" Subject : creates
    User "1" --> "0..*" Deadline : owns
    Subject "1" --> "0..*" Deadline : contains
    Deadline "1" --> "0..*" Reminder : has
    Deadline --> DeadlineStatus : status
    Deadline --> DeadlineType : type
    Reminder --> ReminderChannel : channel
```

**Key:**
- **Multiplicity** shown at both ends of each association (1, 0..*, etc.)
- **Enumeration** for every status field (`DeadlineStatus`, `DeadlineType`, `ReminderChannel`)
- **Typed attributes** with visibility (`+` = public)
- **Methods** shown in parentheses

**Relationship Summary:**

| Relationship | Meaning |
|--------------|---------|
| User → Subject | One user creates many subjects |
| User → Deadline | One user owns many deadlines |
| Subject → Deadline | One subject contains many deadlines |
| Deadline → Reminder | One deadline has many reminders |

**Owner:** Shamel Joy G. Fugio  
**Reviewer:** Vanessa Jhane G. Guda
