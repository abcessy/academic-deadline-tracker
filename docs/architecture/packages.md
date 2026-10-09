# UML Package Diagram — Academic Deadline Tracker

**Diagram Type:** UML Package Diagram  
**Scope:** Folder structure for the codebase with dependency arrows  
**Audience:** Developers, architects  
**Risk Reduced:** Circular dependencies and layering violations  

```mermaid
flowchart TD
    classDef presentation fill:#E1F5FE,stroke:#0288D1,color:#000,stroke-width:2px
    classDef application fill:#FFF3E0,stroke:#F57C00,color:#000,stroke-width:2px
    classDef domain fill:#E8F5E9,stroke:#388E3C,color:#000,stroke-width:2px
    classDef infrastructure fill:#FCE4EC,stroke:#C2185B,color:#000,stroke-width:2px

    subgraph Presentation["presentation/ (Next.js pages and components)"]
        P1["pages/"]:::presentation
        P2["components/"]:::presentation
        P3["hooks/"]:::presentation
    end

    subgraph Application["application/ (Use cases and services)"]
        A1["services/"]:::application
        A2["usecases/"]:::application
        A3["dtos/"]:::application
    end

    subgraph Domain["domain/ (Entities and business rules)"]
        D1["entities/"]:::domain
        D2["value-objects/"]:::domain
        D3["repositories/"]:::domain
    end

    subgraph Infrastructure["infrastructure/ (External concerns)"]
        I1["database/"]:::infrastructure
        I2["email/"]:::infrastructure
        I3["push/"]:::infrastructure
        I4["auth/"]:::infrastructure
    end

    Presentation --> Application
    Application --> Domain
    Infrastructure --> Domain
    Application --> Infrastructure
```

**Key:**
- **Blue boxes** = Presentation layer (UI)
- **Orange boxes** = Application layer (use cases)
- **Green boxes** = Domain layer (business rules)
- **Pink boxes** = Infrastructure layer (external services)
- **Arrows** = Direction of dependency (who imports whom)

**Layering Rule (one sentence):**

> Presentation never imports Infrastructure directly; all external services are accessed through Application services and Domain repository interfaces.

**Owner:** Wenly M. Caalam  
**Reviewer:** Shamel Joy G. Fugio
