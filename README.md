# EMPA - Estimation Methodology Plus Assessments

An AI-assisted project framework for small consulting and analysis teams (2-5 people). EMPA uses **Claude as an active team member** to drive discovery, architecture decisions, visual prototyping, estimation, tracking, and documentation.

You bring the context. Claude asks the questions, recommends the tech stack, builds a clickable prototype, estimates the work, and tracks the project.

**Everything runs in Claude Code. One tool, one workflow.**

---

## How It Works

```
YOU: "We have a new project, here's what we know..." [upload docs]
         |
         v
CLAUDE: Asks questions --> Understands business problem --> Generates charter
         |
         v
CLAUDE: Analyzes needs --> Proposes architecture options --> Team decides
         |
         v
CLAUDE: Builds clickable HTML prototype --> Team reviews --> Client sees it
         |
         v
CLAUDE: Breaks down ALL tasks --> Maps to team --> Estimates hours --> Defines MVP
         |
         v
TEAM:   Executes --> Reports progress weekly --> Claude tracks and flags drift
         |
         v
CLAUDE: Analyzes results --> Evaluates decisions --> Improves future estimates
```

---

## Phases and Skills

Each phase is a skill — a packaged process Claude follows step by step. Only the skill for the current phase is loaded.

| Phase | Skill | Output |
|-------|-------|--------|
| **1. Discover** | `skills/run-discovery.md` | `project-charter.md`, `discovery-questions.md` |
| **2. Architect** | `skills/run-architecture.md` | `architecture-decision.md` |
| **2B. Prototype** | `skills/build-prototype.md` | `prototype/` |
| **3. Estimate** | `skills/run-estimation.md` | `estimation.md` |
| **3B. Scope Changes** | `skills/track-scope-changes.md` | `docs/SC_XXX/` |
| **4. Execute** | `skills/run-execution.md` | `weekly-status-wXX.md` |
| **5. Reflect** | `skills/run-retrospective.md` | `lessons-learned.md` |

---

## Project Structure

```
EMPA-ProjectName/
├── CLAUDE.md                    <- The map — Claude reads this first
├── contexts/
│   └── empa-project.md          <- Project state, phase tracking, wired skills
├── skills/
│   ├── run-discovery.md         <- Phase 1: Discover + Discovery Q&A
│   ├── run-architecture.md      <- Phase 2: Architecture decisions
│   ├── build-prototype.md       <- Phase 2B: Clickable HTML prototype
│   ├── run-estimation.md        <- Phase 3: Full estimation with MoSCoW
│   ├── track-scope-changes.md   <- Phase 3B: Scope change audit trail
│   ├── run-execution.md         <- Phase 4: Weekly tracking and drift
│   └── run-retrospective.md     <- Phase 5: Lessons learned
├── docs/
│   ├── quick-start.md           <- How to start a new project
│   ├── gen-scope-changes.js     <- Word/PDF generator for scope changes
│   └── gen-estimation.js        <- Word/PDF generator for estimation
├── prototype/                   <- Clickable HTML prototype
├── README.md
├── package.json
└── .gitignore
```

---

## Quick Start

1. **Use this template** → Click "Use this template" → name it `EMPA-ProjectName`
2. **Clone and open in Claude Code**
3. **Tell Claude:** "We have a new EMPA project. Here's what we know: [context]"
4. **Follow the phases** — each skill tells Claude what to do next

Full guide: [docs/quick-start.md](docs/quick-start.md)

---

## What Makes EMPA Different

- **Claude is a team member, not a tool.** Claude drives discovery, challenges assumptions, flags risks, and generates all documentation. Claude also acts as Data Architect, UI/UX Designer, and Technical Architect when the team doesn't have dedicated resources.
- **Skills, not monoliths.** Each phase is a standalone skill file. Claude loads only what it needs — no wasted tokens, no context pollution.
- **Evidence-based, never assumed.** Every decision, estimation, and scope change traces back to documented evidence.
- **Architecture before estimation.** You can't estimate accurately without knowing the stack, environments, CI/CD, and team roles.
- **Visual prototypes sell projects.** Clickable HTML with inline SVGs, CSS variables, and realistic data. Clients believe it's a working app.
- **Estimation includes everything.** Not just code — infra per environment, CI/CD, DevOps, QA, learning curve, bug buffer, all mapped to team members.
- **Scope changes are auditable.** Every client answer gets logged with exact quotes, impact analysis, and before/after totals.
- **Continuous improvement.** Every project ends with a retrospective that updates estimation factors for the next one.

---

## Document Generators

| Generator | Command | Output |
|-----------|---------|--------|
| Scope Change Register | `node docs/gen-scope-changes.js SC_001` | `docs/SC_001/scope-changes.docx` |
| Estimation Document | `node docs/gen-estimation.js` | `docs/estimation.docx` |

Convert to PDF: `libreoffice --headless --convert-to pdf <file.docx> --outdir <folder>`

---

## Projects Built with EMPA

| Project | Repository | Stack | Status | Phase |
|---------|------------|-------|--------|-------|
| ReMarkets — Bid Intelligence Platform | [EMPA-ReMarkets](https://github.com/ArturoMV199/EMPA-ReMarkets) | Blazor + .NET 10 + Azure SQL | Pre-Execution | Estimate complete (~998 MVP hrs) |
| Celink | [EMPA-Celink](https://github.com/ArturoMV199/EMPA-Celink) | TBD | Pre-Discovery | Starting |

---

## License

This project is for personal use.
