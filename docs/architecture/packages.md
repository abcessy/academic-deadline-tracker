mermaid
flowchart TD
    subgraph Presentation["presentation/ (Next.js pages & components)"]
        P1[pages/]
        P2[components/]
        P3[hooks/]
    end

    subgraph Application["application/ (Use cases & services)"]
        A1[services/]
        A2[usecases/]
        A3[dtos/]
    end

    subgraph Domain["domain/ (Entities & business rules)"]
        D1[entities/]
        D2[value-objects/]
        D3[repositories/]
    end

    subgraph Infrastructure["infrastructure/ (External concerns)"]
        I1[database/]
        I2[email/]
        I3[push/]
        I4[auth/]
    end

    Presentation --> Application
    Application --> Domain
    Infrastructure --> Domain
    Application --> Infrastructure

    style Presentation fill:#e1f5fe
    style Application fill:#fff3e0
    style Domain fill:#e8f5e9
    style Infrastructure fill:#fce4ec

*Key:*
- *Package* = Folder grouping related modules
- *Dependency arrow* = Direction of import/dependency
- *Layering* = Presentation → Application → Domain ← Infrastructure

*Layering Rule (one sentence):*

*"Presentation never imports Infrastructure directly; all external services are accessed through Application services and Domain repository interfaces."*
