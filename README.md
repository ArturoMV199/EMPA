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
| **2. Architect** | Claude analyzes, team decides | Stack, environments, CI/CD, team roles, cost | `architecture-decision.md` |
| **2B. Prototype** | Claude builds, team reviews | Clickable HTML screens with professional look | `prototype/` folder |
| **3. Estimate** | Claude proposes, team validates | All tasks mapped to people with hours and MVP | `estimation.md` |
| **4. Execute** | Team works, Claude tracks | Weekly cycles with drift alerts | `weekly-status.md` |
| **5. Reflect** | Claude analyzes, team learns | Metrics, tech assessment, improved factors | `lessons-learned.md` |

Full details: [docs/methodology.md](docs/methodology.md)

---

## Project Structure

```
EMPA/
├── docs/
│   ├── methodology.md                   # EMPA methodology (5 phases + prototype)
│   ├── claude-project-instructions.md   # Instructions for Claude.ai Projects
│   ├── output-formats.md               # Document formats Claude generates
│   └── quick-start.md                  # How to start a new project
├── prototype/                           # Clickable HTML prototype (per project)
├── index.html                           # Project dashboard
├── css/styles.css                       # Base styles
├── js/main.js                           # Main logic
├── img/                                 # Visual assets
├── assets/                              # Additional resources
├── fonts/                               # Custom fonts
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

- **Claude is a team member, not a tool.** Claude drives discovery, challenges assumptions, flags risks, and generates all documentation from conversation.
- **Architecture before estimation.** You can't estimate accurately without knowing the stack, environments, CI/CD, and team roles first.
- **Visual prototypes sell projects.** Claude builds clickable HTML prototypes with inline SVGs, CSS variables, and realistic data — no wireframes, no mockups.
- **Estimation includes everything.** Not just code — infra per environment, CI/CD pipelines, DevOps, QA, learning curve, bug buffer, all mapped to team members.
- **Continuous improvement.** Every project ends with a retrospective that updates estimation factors for the next one.

---

## Projects Built with EMPA

| Project | Repository | Stack | Status | Accuracy |
|---------|------------|-------|--------|----------|
| -       | -          | -     | -      | -        |

---

## License

This project is for personal use.
