# Provisional UML Deployment Diagram — Academic Deadline Tracker

**Diagram Type:** UML Deployment Diagram  
**Scope:** Hosting infrastructure — nodes, execution environments, artifacts  
**Audience:** DevOps, system administrators  
**Risk Reduced:** Deployment misconfiguration and missing infrastructure  

> **Title:** Provisional — provider names are generic until hosting is finalized.

```mermaid
flowchart TB
    classDef device fill:#E1F5FE,stroke:#0288D1,color:#000,stroke-width:2px
    classDef node fill:#F3E5F5,stroke:#7B1FA2,color:#000,stroke-width:2px
    classDef artifact fill:#FFF3E0,stroke:#F57C00,color:#000,stroke-width:2px
    classDef external fill:#999999,stroke:#6B6B6B,color:#fff,stroke-width:2px

    subgraph UserDevice["Student Device (Browser)"]
        Browser["Web Browser<br/>Chrome, Firefox, Safari"]:::device
    end

    subgraph Cloud["Cloud Provider (e.g., Vercel / Railway)"]
        subgraph WebServer["Web Server"]
            NextApp["Next.js App<br/>Node.js runtime"]:::artifact
        end

        subgraph APIServer["API Server"]
            ExpressApp["Express API<br/>Node.js runtime"]:::artifact
        end

        subgraph ReminderWorker["Reminder Worker"]
            CronJob["Cron Job<br/>Node.js"]:::artifact
        end

        subgraph DatabaseServer["Database Server"]
            Postgres["PostgreSQL<br/>managed instance"]:::node
        end
    end

    subgraph ExternalServices["External Services"]
        GoogleAuth["Google Auth<br/>OAuth 2.0"]:::external
        EmailSvc["Email Service<br/>SMTP"]:::external
        PushSvc["Push Service<br/>Web Push API"]:::external
    end

    Browser -->|"HTTPS"| NextApp
    NextApp -->|"JSON/HTTPS"| ExpressApp
    ExpressApp -->|"SQL/TCP"| Postgres
    CronJob -->|"SQL/TCP"| Postgres
    CronJob -->|"SMTP"| EmailSvc
    CronJob -->|"HTTPS"| PushSvc
    ExpressApp -->|"OAuth 2.0/HTTPS"| GoogleAuth
    NextApp -->|"HTTPS"| GoogleAuth
```

**Key:**
- **Blue box** = User device (browser)
- **Purple box** = Cloud infrastructure boundary
- **Orange boxes** = Deployable artifacts (Next.js, Express, Cron)
- **Gray boxes** = External services
- **Arrows** = Labelled with protocol on every path

**Deployment Notes:**

| Node | Artifact | Technology |
|------|----------|------------|
| Web Server | Next.js App | Node.js runtime |
| API Server | Express API | Node.js runtime |
| Reminder Worker | Cron Job | Node.js |
| Database Server | PostgreSQL | Managed instance |

**Protocols Used:** HTTPS, JSON/HTTPS, SQL/TCP, SMTP, OAuth 2.0/HTTPS

**No secrets or real addresses are shown.**

**Owner:** Princess Mae G. Morata  
**Reviewer:** Shamel Joy G. Fugio
