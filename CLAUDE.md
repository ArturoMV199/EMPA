# CLAUDE.md — EMPA

This file is read automatically by Claude Code at the start of every session.
It is the map — read this first, always.

---

## What is EMPA?

**Estimation Methodology Plus Assessments** — an AI-assisted framework for small consulting teams (2-5 people). Claude acts as an active team member driving discovery, architecture, prototyping, estimation, tracking, and documentation.

You bring the context. Claude asks the questions, recommends the stack, builds the prototype, estimates the work, and tracks the project.

**Everything happens in Claude Code.** One tool, one workflow.

---

## Phases and Skills

Each phase has its own skill file. Load only the skill for the current phase.

| Phase | Skill | Output |
|-------|-------|--------|
| 1. Discover | `skills/run-discovery.md` | `project-charter.md`, `discovery-questions.md` |
| 2. Architect | `skills/run-architecture.md` | `architecture-decision.md` |
| 2B. Prototype | `skills/build-prototype.md` | `prototype/` |
| 3. Estimate | `skills/run-estimation.md` | `estimation.md` |
| 3B. Scope Changes | `skills/track-scope-changes.md` | `docs/SC_XXX/` |
| 4. Execute | `skills/run-execution.md` | `weekly-status-wXX.md` |
| 5. Reflect | `skills/run-retrospective.md` | `lessons-learned.md` |

---

## Project Context

→ `contexts/empa-project.md`

This file tracks the active project state: current phase, decisions made, totals, and which skills are wired. Read it to know where the project stands.

---

## Rules

- **Language:** Documents and deliverables in English. Conversation can be in Spanish.
- **EMPA is internal only:** Never include "EMPA" in client-facing deliverables. Use only the project name and company name.
- **Never change hours silently:** Verify against official documents, flag discrepancies, get explicit approval before modifying estimation figures.
- **Prototypes:** Raw HTML + custom CSS. Inline SVG icons ONLY — no external icon CDNs. CSS variables for brand colors. Fictional placeholder data.
- **Evidence-based:** Every decision, estimation, and scope change traces back to documented evidence. No hallucinating, no assuming.
- **Human in the loop:** Always. Back-and-forth until the human confirms. No autonomous execution without approval.
- **Read the skill first:** Before starting any phase, read the corresponding skill file. Follow the process exactly.

---

## Document Generators

| Generator | Command | Output |
|-----------|---------|--------|
| Scope Changes | `node docs/gen-scope-changes.js SC_001` | `docs/SC_001/scope-changes.docx` |
| Estimation | `node docs/gen-estimation.js` | `docs/estimation.docx` |

Convert to PDF: `libreoffice --headless --convert-to pdf <file.docx> --outdir <folder>`

---

## Project Configuration

```yaml
project_name: ""           # e.g., "EMPA-ReMarkets"
client: ""                 # Client name
tech_lead: ""              # Name of tech lead
team_size: 0               # Number of team members
created: ""                # Date of project start
```

---

## Getting Started

1. Clone this template as `EMPA-ProjectName`
2. Open the repo in Claude Code
3. Tell Claude: "We have a new EMPA project. Here's what we know: [context]"
4. Claude reads this file, loads `run-discovery` skill, and starts asking questions
5. Follow the phases in order — each skill tells you what to do next
