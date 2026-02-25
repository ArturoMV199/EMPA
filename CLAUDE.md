# CLAUDE.md

This file is read automatically by Claude Code at the start of every session.
It provides project context, EMPA methodology state, and decision history so Claude never starts from zero.

---

## What is this project?

This is an **EMPA (Estimation Methodology Plus Assessments)** template repository. EMPA is a framework where Claude acts as an active team member driving discovery, architecture, prototyping, estimation, and tracking through conversation.

Full methodology: `docs/methodology.md`
Claude instructions: `docs/claude-project-instructions.md`
Output formats: `docs/output-formats.md`
Quick start: `docs/quick-start.md`

---

## EMPA Phases

```
1. Discover   → project-charter.md
2. Architect  → architecture-decision.md
2B. Prototype → prototype/ folder (HTML + inline SVGs + CSS variables)
3. Estimate   → estimation.md
3B. Scope Changes → docs/SC_XXX/scope-changes.json → scope-changes.pdf/docx (ongoing)
4. Execute    → weekly-status.md (per week)
5. Reflect    → lessons-learned.md
```

---

## Current Project State

**Status:** Template repository — no active project yet
**Current Phase:** N/A
**Last Updated:** 2026-02-24

<!-- 
When using this template for a real project, update this section:

**Status:** Active
**Project Name:** EMPA-[ProjectName]
**Client:** [Name]
**Current Phase:** [Discover / Architect / Prototype / Estimate / Execute / Reflect]
**Last Updated:** [Date]

### Decisions Made
- [Date] Charter approved: [summary]
- [Date] Architecture decided: [stack summary]
- [Date] Prototype delivered: [screens built]
- [Date] Estimation approved: [total hours, MVP scope]

### Current Sprint/Week
- Week [#]: [focus area]
- Blockers: [any blockers]
- Next: [what's coming]

### Key Context
- Team: [names and roles]
- Stack: [tech stack summary]
- Environments: [Dev/Test/Staging/Prod]
- CI/CD: [platform and strategy]
- Repo: [GitHub URL]
-->

---

## Rules for Claude

- **Language:** Documents and deliverables in English. Conversation can be in Spanish.
- **Prototypes:** Raw HTML + custom CSS. Inline SVG icons ONLY — never Font Awesome or external icon CDNs. CSS variables for brand colors. Fictional/invented placeholder data (never use real client data unless explicitly provided).
- **Estimation:** Include ALL work — infra per environment, CI/CD, DevOps, QA, learning curve, bug buffer. Map tasks to team members.
- **Scope Changes:** Every client answer gets logged in `scope-changes.json` — even 0-impact confirmations. Always quote the client's exact answer as evidence. Regenerate PDF/Word after each batch.
- **EMPA is internal only:** Never include "EMPA" in client-facing deliverables (docs, PDFs, presentations). Use only the project name (e.g. "ReMarkets") and "Simpat Tech".
- **Never change hours silently:** Always verify against official documents, flag discrepancies before acting, and get explicit approval before modifying any estimation figures.
- **Always read** `docs/methodology.md` before starting any EMPA phase.
- **Update this file** after every major decision or phase completion. When a new rule is created that affects deliverables or workflow, add it here too.
