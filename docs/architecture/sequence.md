# UML Sequence Diagram — Academic Deadline Tracker

**Diagram Type:** UML Sequence Diagram  
**Scope:** Riskiest flow — Login via Google Auth (external system + security)  
**Audience:** Developers, security reviewers  
**Risk Reduced:** Authentication failures and security vulnerabilities  

```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant WebApp as Web App (Next.js)
    participant API as API (Express)
    participant Google as Google Auth
    participant DB as PostgreSQL

    Student->>WebApp: Click "Login with Google"
    WebApp->>Google: Redirect to OAuth consent
    Google-->>Student: Show consent screen
    Student->>Google: Grant permission
    Google-->>WebApp: Redirect with authorization code
    WebApp->>API: POST /auth/google (code)
    API->>Google: Exchange code for tokens
    Google-->>API: Return access token + ID token
    API->>API: Validate ID token
    alt Token valid
        API->>DB: Find or create user
        DB-->>API: Return user record
        API-->>WebApp: Return JWT session token
        WebApp-->>Student: Redirect to dashboard
    else Token invalid
        API-->>WebApp: Return 401 Unauthorized
        WebApp-->>Student: Show login error
    end
```

**Key:**
- **Solid arrow (→)** = Synchronous message
- **Dashed arrow (-->>)** = Reply / Return message
- **alt / else** = Alternative flow (branch)
- **Lifelines** = Student, Web App, API, Google Auth, PostgreSQL

**Why this is the riskiest flow:** It involves an external system (Google), security tokens, database writes, and session management. A failure here blocks all other features.

**Owner:** Shamel Joy G. Fugio  
**Reviewer:** Wenly M. Caalam
