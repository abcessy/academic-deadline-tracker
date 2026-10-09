# Contribution Log and AI-Use Disclosure

**Team:** Team Baddie  
**Activity:** CC106b Unit 3 Activity 7 — Architectural Views  
**Date:** October 9, 2026

---

## Contribution Log

| Member | Work done (diagrams drafted, diagrams reviewed) | Commit evidence (hashes or links) | AI tools used, and how the output was checked |
|--------|------------------------------------------------|-----------------------------------|-----------------------------------------------|
| Vanessa Jhane G. Guda | Drafted: context.md, containers.md, components.md. Reviewed: activity.md, class.md. | See GitHub commit history | Used AI to draft Mermaid syntax. Verified every actor and external system against our Lean Canvas and MVP feature list. Removed any AI-invented components not in our MVP. |
| Princess Mae G. Morata | Drafted: use-cases.md, activity.md, deployment.md. Reviewed: context.md, state-machine.md, components.md. | See GitHub commit history | Used AI to draft Mermaid syntax. Verified all 10 use cases map to actual MVP features. Checked swimlane assignments against our core workflow. Deployment diagram uses generic provider names per instructions. |
| Shamel Joy G. Fugio | Drafted: sequence.md, class.md, erd.md. Reviewed: containers.md, packages.md, deployment.md. | See GitHub commit history | Used AI to draft Mermaid syntax. Verified login flow matches our Google Auth integration plan. Checked class multiplicities against ERD crow's-foot notation. Marked PII columns based on data privacy requirements. |
| Wenly M. Caalam | Drafted: state-machine.md, packages.md. Reviewed: use-cases.md, sequence.md, erd.md. | See GitHub commit history | Used AI to draft Mermaid syntax. Verified state names (PENDING, IN_PROGRESS, COMPLETED, OVERDUE) match class diagram enumeration exactly. Checked package dependencies follow our layering rule. |

---

## AI-Use Summary

**Tool used:** AI assistant for drafting Mermaid syntax and suggesting missing elements.

**How output was checked:**

1. Every actor, class, state, table, and flow was compared against our own Lean Canvas and MVP feature list.
2. Any AI-invented components not in our MVP were removed.
3. Cross-view consistency was verified using the checklist in `README.md`.
4. Each diagram owner personally reviewed their diagram before committing.
5. Peer review with another team (see `peer-review.md`) confirmed consistency.

**Declaration:** We confirm that all diagrams reflect our own Academic Deadline Tracker MVP, not the laundry service example from the lecture notes. We did not submit AI-generated diagrams without checking every element against our own project.

---

## Instructions for Filling This Out

- **Member:** Write your full name.
- **Work done:** List every diagram you drafted and reviewed. Match the owner/reviewer table in `README.md`.
- **Commit evidence:** After you commit, find your commit hash by clicking on the commit in GitHub. Paste the short hash (7 characters) or the full link.
- **AI tools used:** If you used AI (like Claude, ChatGPT, Copilot, etc.), write the tool name and how you checked its output. If you didn't use AI, write "None."

Each member must write their own row. Undisclosed AI use is treated under the course policy on plagiarism and due credit.

---

## How to Find Your Commit Hash

1. Go to your repository on GitHub
2. Click **Commits** (the clock icon near the top of the file list)
3. Find the commit you made for each diagram
4. Click the commit
5. The commit hash is shown at the top (e.g., `da6d088`)
6. Copy the first 7 characters
