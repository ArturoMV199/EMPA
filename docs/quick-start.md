# EMPA Quick Start Guide

How to start a new project using EMPA.

---

## Step 1: Create the Project Repo

1. Go to the [EMPA template repository](https://github.com/ArturoMV199/EMPA)
2. Click **"Use this template"** → **"Create a new repository"**
3. Name it `EMPA-ProjectName` (e.g., `EMPA-ClientPortal`, `EMPA-InventoryApp`)
4. Clone it locally

```bash
git clone https://github.com/ArturoMV199/EMPA-ProjectName.git
cd EMPA-ProjectName
```

---

## Step 2: Create a Claude.ai Project

1. Go to [claude.ai](https://claude.ai) → **Projects** → **New Project**
2. Name it the same: `EMPA-ProjectName`
3. Open `docs/claude-project-instructions.md` from your repo
4. Copy everything under **"## Instructions (copy from here)"**
5. Paste it into the Project's **custom instructions**

---

## Step 3: Upload Context

Upload everything you have about the project into the Claude.ai Project:
- Client emails or briefs
- SOW (Statement of Work) if available
- Technical documents, API docs, existing system diagrams
- Meeting notes
- Any reference material

The more context Claude has, the better the discovery and architecture phases will be.

---

## Step 4: Start Discovery

Open a conversation in the Claude.ai Project and say:

> "We have a new EMPA project. Here's what we know: [paste or describe everything you know about the project]"

Claude will start asking questions to understand the full scope. Answer them. When Claude has enough info, it will generate the **project charter**.

Review the charter with your team. When approved, move to architecture.

---

## Step 5: Architecture Discussion

Tell Claude:

> "Charter is approved. Let's decide the architecture."

Upload any technical constraints or client requirements if you haven't already. Claude will run through its internal checklists (team, stack, infra, environments, CI/CD, cost) and ask what it needs to.

Claude will propose 2-3 architecture options. Team discusses, decides, and Claude generates the **architecture decision document**.

---

## Step 6: Visual Prototype

Tell Claude:

> "Architecture is decided. Let's build the prototype."

Claude will build a clickable HTML prototype with:
- Key screens (login, dashboard, core features)
- Inline SVG icons (no external dependencies)
- CSS variables for brand colors
- Working navigation between screens
- Realistic placeholder data

Review with the team, iterate, and use it to impress the client.

---

## Step 7: Estimation

Tell Claude:

> "Architecture and prototype are done. Let's estimate."

Claude will break down ALL work (frontend, backend, infra per environment, CI/CD, QA, learning curve, bug buffer) and map tasks to team members showing parallelization.

Claude defines the MVP using MoSCoW prioritization and produces the **estimation document**.

---

## Step 8: Execute

During the project, check in weekly:

> "Here's what we did this week: [summary of completed tasks and hours]"

Claude generates the **weekly status report**, tracks estimated vs actual hours, and flags drift.

---

## Step 9: Reflect

After delivery:

> "Project is done. Final hours: [data by module and person]. Let's reflect."

Claude analyzes everything and generates **lessons learned** with updated estimation factors for future projects.

---

## Conversation Starters by Phase

| Phase | What to Say |
|-------|------------|
| Discover | "We have a new EMPA project. Here's what we know: [context]" |
| Architect | "Charter is approved. Let's decide the architecture." |
| Prototype | "Architecture is decided. Let's build the prototype." |
| Estimate | "Architecture and prototype are done. Let's estimate." |
| Execute | "Here's what we did this week: [summary]" |
| Reflect | "Project is done. Final hours: [data]. Let's reflect." |

---

## File Checklist

After a complete EMPA project, your repo should contain:

```
EMPA-ProjectName/
├── docs/
│   ├── project-charter.md          <- Phase 1 output
│   ├── architecture-decision.md    <- Phase 2 output
│   ├── estimation.md               <- Phase 3 output
│   ├── weekly-status-w01.md        <- Phase 4 output (per week)
│   ├── weekly-status-w02.md
│   └── lessons-learned.md          <- Phase 5 output
├── prototype/
│   ├── index.html                  <- Login / landing
│   ├── dashboard.html              <- Dashboard / home
│   ├── feature-1.html              <- Core feature
│   ├── css/
│   │   └── prototype.css           <- Styles
│   └── img/
└── README.md
```

---

## Tips

- **Upload everything** — the more context Claude has, the better it performs
- **Don't skip Architecture** — estimation accuracy depends on it
- **Use the prototype to sell** — clients buy what they can see
- **Track hours honestly** — the Reflect phase only works with real data
- **Update the EMPA template** — when you learn something that should apply to all future projects, update the template repo
