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

## Step 2: Open in Claude Code

Open the repo directory in Claude Code. Claude reads `CLAUDE.md` automatically and knows:
- What EMPA is
- What phases and skills are available
- What rules to follow

No additional setup needed. No Claude.ai Projects, no custom instructions to paste.

---

## Step 3: Upload Context

Have everything about the project ready:
- Client emails or briefs
- SOW (Statement of Work) if available
- Technical documents, API docs, existing system diagrams
- Meeting notes
- Any reference material

The more context Claude has, the better the discovery and architecture phases will be.

---

## Step 4: Start Discovery

Tell Claude:

> "We have a new EMPA project. Here's what we know: [paste or describe everything you know about the project]"

Claude loads the `run-discovery` skill and starts asking questions (2-3 at a time). When Claude has enough info, it generates:
- **`project-charter.md`** — the scope, stakeholders, constraints, risks
- **`discovery-questions.md`** — open questions that need client answers

Review with your team. When approved, move to architecture.

---

## Step 5: Architecture Discussion

Tell Claude:

> "Charter is approved. Let's decide the architecture."

Claude loads `run-architecture`, runs through internal checklists (team, stack, infra, environments, CI/CD, cost), asks what it needs, and proposes 2-3 options.

Team discusses, decides, and Claude generates **`architecture-decision.md`**.

---

## Step 6: Visual Prototype

Tell Claude:

> "Architecture is decided. Let's build the prototype."

Claude loads `build-prototype` and builds a clickable HTML prototype with:
- Key screens (login, dashboard, core features)
- Inline SVG icons (zero external dependencies)
- CSS variables for brand colors
- Working navigation between screens
- Realistic placeholder data

Review, iterate, and use it to impress the client.

---

## Step 7: Estimation

Tell Claude:

> "Architecture and prototype are done. Let's estimate."

Claude loads `run-estimation` and breaks down ALL work (frontend, backend, infra per environment, CI/CD, QA, learning curve, bug buffer), maps tasks to team members, and defines MVP with MoSCoW.

Output: **`estimation.md`**

---

## Step 8: Execute

During the project, check in weekly:

> "Here's what we did this week: [summary of completed tasks and hours]"

Claude loads `run-execution` and generates **`weekly-status-wXX.md`** with estimated vs actual hours, drift tracking, and risk flags.

For scope changes triggered by client answers:

> "Client answered questions X-Y. Let's update the estimation."

Claude loads `track-scope-changes` and handles the audit trail.

---

## Step 9: Reflect

After delivery:

> "Project is done. Final hours: [data by module and person]. Let's reflect."

Claude loads `run-retrospective` and generates **`lessons-learned.md`** with updated estimation factors for future projects.

---

## Conversation Starters by Phase

| Phase | What to Say |
|-------|------------|
| Discover | "We have a new EMPA project. Here's what we know: [context]" |
| Architect | "Charter is approved. Let's decide the architecture." |
| Prototype | "Architecture is decided. Let's build the prototype." |
| Estimate | "Architecture and prototype are done. Let's estimate." |
| Execute | "Here's what we did this week: [summary]" |
| Scope Change | "Client answered questions [X-Y]. Let's update." |
| Reflect | "Project is done. Final hours: [data]. Let's reflect." |

---

## Tips

- **Upload everything** — the more context Claude has, the better it performs
- **Don't skip Architecture** — estimation accuracy depends on it
- **Use the prototype to sell** — clients buy what they can see
- **Track hours honestly** — the Reflect phase only works with real data
- **Update the EMPA template** — when you learn something that should apply to all future projects, update the template repo
