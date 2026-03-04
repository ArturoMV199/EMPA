# EMPA - Estimation Methodology Plus Assessments

An AI-assisted project framework for small consulting and analysis teams (2-5 people). EMPA uses **Claude as an active team member** to drive discovery, architecture decisions, visual prototyping, estimation, tracking, and documentation through conversation.

You bring the context. Claude asks the questions, recommends the tech stack, builds a clickable prototype, estimates the work, and tracks the project.

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

## Methodology

| Phase | Who Drives | What Happens | Output |
|-------|-----------|-------------|--------|
| **1. Discover** | Claude asks, you answer | Business problem, scope, stakeholders | `project-charter.md` |
| **1B. Discovery Q&A** | Claude generates, client answers | Open questions, gap analysis, risk identification | `discovery-questions.md` |
| **2. Architect** | Claude analyzes, team decides | Stack, environments, CI/CD, team roles, cost | `architecture-decision.md` |
| **2B. Prototype** | Claude builds, team reviews | Clickable HTML screens with professional look | `prototype/` folder |
| **3. Estimate** | Claude proposes, team validates | All tasks mapped to people with hours and MVP | `estimation.md` |
| **3B. Scope Changes** | Claude tracks, client triggers | Every Q&A answer logged with evidence and impact | `docs/SC_XXX/` |
| **4. Execute** | Team works, Claude tracks | Weekly cycles with drift alerts | `weekly-status.md` |
| **5. Reflect** | Claude analyzes, team learns | Metrics, tech assessment, improved factors | `lessons-learned.md` |

Full details: [docs/methodology.md](docs/methodology.md)

---

## Project Structure

```
EMPA-ProjectName/
├── docs/
│   ├── methodology.md                   # EMPA methodology (5 phases + prototype)
│   ├── claude-project-instructions.md   # Instructions for Claude.ai Projects
│   ├── output-formats.md               # Document formats Claude generates
│   ├── quick-start.md                  # How to start a new project
│   ├── discovery-questions.md          # Living backlog of open questions
│   ├── gen-scope-changes.js            # Word/PDF generator for scope changes
│   ├── gen-estimation.js               # Word/PDF generator for estimation
│   └── SC_XXX/                         # Scope change batches (one folder per batch)
│       ├── scope-changes.json          # Change data with client evidence
│       ├── scope-changes.docx          # Generated Word document
│       └── scope-changes.pdf           # Generated PDF
├── prototype/                           # Clickable HTML prototype
│   ├── index.html                      # Login / landing
│   ├── dashboard.html                  # Main dashboard
│   ├── css/prototype.css               # Styles with CSS variables
│   └── ...                             # Feature screens
├── project-charter.md                   # Phase 1 output
├── CLAUDE.md                            # Project state + rules for Claude Code
├── package.json                         # npm config (docx dependency for generators)
├── .gitignore
└── README.md
```

---

## Quick Start

1. **Use this template** → Click "Use this template" → name it `EMPA-ProjectName`
2. **Create a Claude.ai Project** → paste instructions from `docs/claude-project-instructions.md`
3. **Upload your project context** (emails, briefs, SOWs, technical docs)
4. **Start:** "Claude, we have a new EMPA project. Here's what we know: [context]"

Full guide: [docs/quick-start.md](docs/quick-start.md)

---

## What Makes EMPA Different

- **Claude is a team member, not a tool.** Claude drives discovery, challenges assumptions, flags risks, and generates all documentation from conversation. Claude also acts as Data Architect, UI/UX Designer, and Technical Architect when the team doesn't have dedicated resources.
- **Evidence-based, never assumed.** Every decision, estimation, and scope change is traced back to documented evidence — transcripts, emails, or client answers. Nothing is guessed or invented.
- **Architecture before estimation.** You can't estimate accurately without knowing the stack, environments, CI/CD, and team roles first.
- **Visual prototypes sell projects.** Claude builds clickable HTML prototypes with inline SVGs, CSS variables, and realistic data — no wireframes, no mockups. Clients believe it's a working app.
- **Estimation includes everything.** Not just code — infra per environment, CI/CD pipelines, DevOps, QA, learning curve, bug buffer, all mapped to team members with MoSCoW prioritization.
- **Scope changes are auditable.** Every client answer gets logged with exact quotes, impact analysis, and before/after totals. Word/PDF documents generated automatically.
- **Continuous improvement.** Every project ends with a retrospective that updates estimation factors for the next one.

---

## Document Generators

EMPA includes Node.js generators that produce professional Word/PDF documents:

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
