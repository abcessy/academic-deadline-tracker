# Architecture Design Document — Academic Deadline Tracker

**Team:** Team Baddie  
**Members:** Vanessa Jhane G. Guda, Princess Mae G. Morata, Shamel Joy G. Fugio, Wenly M. Caalam  
**Course:** BSIS 4-2  
**Institution:** Sorsogon State University — College of Information and Communications Technology, Bulan Campus  

---

## Diagram Index

| # | Diagram | File | Owner | Reviewer |
|---|---------|------|-------|----------|
| 1 | C4 System Context | [context.md](context.md) | Vanessa Jhane G. Guda | Princess Mae G. Morata |
| 2 | C4 Container | [containers.md](containers.md) | Vanessa Jhane G. Guda | Shamel Joy G. Fugio |
| 3 | Use Case | [use-cases.md](use-cases.md) | Princess Mae G. Morata | Wenly M. Caalam |
| 4 | Activity | [activity.md](activity.md) | Princess Mae G. Morata | Vanessa Jhane G. Guda |
| 5 | Sequence | [sequence.md](sequence.md) | Shamel Joy G. Fugio | Wenly M. Caalam |
| 6 | Class | [class.md](class.md) | Shamel Joy G. Fugio | Vanessa Jhane G. Guda |
| 7 | State Machine | [state-machine.md](state-machine.md) | Wenly M. Caalam | Princess Mae G. Morata |
| 8 | Package | [packages.md](packages.md) | Wenly M. Caalam | Shamel Joy G. Fugio |
| 9 | Component | [components.md](components.md) | Vanessa Jhane G. Guda | Princess Mae G. Morata |
| 10 | Deployment | [deployment.md](deployment.md) | Princess Mae G. Morata | Shamel Joy G. Fugio |
| 11 | ERD (Draft) | [erd.md](erd.md) | Shamel Joy G. Fugio | Wenly M. Caalam |

---

## Workload Distribution

| Member | Diagrams Owned | Diagrams Reviewed |
|--------|----------------|-------------------|
| Vanessa Jhane G. Guda | 1, 2, 9 | 4, 6 |
| Princess Mae G. Morata | 3, 4, 10 | 1, 7, 9 |
| Shamel Joy G. Fugio | 5, 6, 11 | 2, 8, 10 |
| Wenly M. Caalam | 7, 8 | 3, 5, 11 |

---

## Cross-View Consistency Checklist

| # | Check | Status | Evidence |
|---|-------|--------|----------|
| 1 | All actors in use case diagram match context diagram | ✅ | Student, Instructor, Google Auth, Email Service, Push Service appear in both |
| 2 | All containers in container diagram match deployment nodes | ✅ | Web App, API, Database, Reminder Service appear in both |
| 3 | Status enumeration matches state machine states | ✅ | PENDING, IN_PROGRESS, COMPLETED, OVERDUE match exactly |
| 4 | Class diagram multiplicities match ERD cardinalities | ✅ | User 1→0..* Subject; User 1→0..* Deadline; Subject 1→0..* Deadline; Deadline 1→0..* Reminder |
| 5 | Component interfaces match API endpoints in sequence | ✅ | IAuth used in login sequence; IDeadline for deadline operations |
| 6 | Package dependencies match layering rule | ✅ | Presentation → Application → Domain; Infrastructure → Domain |
| 7 | Every diagram has title, key, and labelled relationships | ✅ | Verified in each file |

---

## Architectural Style

**Layered Architecture** with clear separation:

| Layer | Responsibility | Technology |
|-------|----------------|------------|
| **Presentation** | UI and user interactions | Next.js (React) |
| **Application** | Use cases and orchestration | Node.js / Express |
| **Domain** | Entities and business rules | TypeScript classes |
| **Infrastructure** | External service adapters | PostgreSQL, SMTP, Web Push, OAuth |

---

## External Dependencies

| System | Purpose | Interface |
|--------|---------|-----------|
| Google Authentication | OAuth 2.0 login | IGoogleAuth |
| Email Service | Reminder delivery | IEmailService |
| Push Notification Service | Real-time reminders | IPushService |
| PostgreSQL | Data persistence | IDatabase |

---

## Document Purpose

This Architecture Design Document (ADD) is the core reference for the Academic Deadline Tracker MVP. It must be approved before front-end build begins and will be updated throughout the Front-End, Back-End, and Deployment units.

All diagrams follow C4 notation rules (Brown, n.d.) and UML 2.x standards. The 4+1 architectural view model (Kruchten, 1995) guides the selection of views.
