---
name: "EMPA Project"
description: "Active EMPA project context — tracks current phase, project state, and wires all skills"
owner: "Tech Lead"
skills:
  - "run-discovery"
  - "run-architecture"
  - "build-prototype"
  - "run-estimation"
  - "track-scope-changes"
  - "run-execution"
  - "run-retrospective"
---

# Context: EMPA Project

## What This Area Covers

The full lifecycle of an EMPA project — from discovery to retrospective. This context tracks which phase the project is in and routes to the correct skill.

## Phase Flow

```
1. Discover      → skills/run-discovery.md
2. Architect     → skills/run-architecture.md
2B. Prototype    → skills/build-prototype.md
3. Estimate      → skills/run-estimation.md
3B. Scope Changes → skills/track-scope-changes.md  (ongoing after estimation)
4. Execute       → skills/run-execution.md
5. Reflect       → skills/run-retrospective.md
```

## Current Project State

<!-- Update this section when using the template for a real project -->

**Status:** Template — no active project
**Project Name:** —
**Client:** —
**Current Phase:** —
**Last Updated:** —

### Phase Completion
- [ ] Phase 1: Discover → `project-charter.md`
- [ ] Phase 1B: Discovery Q&A → `discovery-questions.md`
- [ ] Phase 2: Architect → `architecture-decision.md`
- [ ] Phase 2B: Prototype → `prototype/`
- [ ] Phase 3: Estimate → `estimation.md`
- [ ] Phase 4: Execute → `weekly-status-wXX.md`
- [ ] Phase 5: Reflect → `lessons-learned.md`

### Decisions Made
| Date | Decision | Why |
|------|----------|-----|

### Current Totals
| Metric | Value |
|--------|-------|
| MVP Hours | — |
| Full Scope Hours | — |
| Scope Changes Applied | 0 |
| Current Week | — |

## Key Files and Locations

| What | Where |
|------|-------|
| Project Charter | `project-charter.md` |
| Discovery Questions | `discovery-questions.md` |
| Architecture Decision | `architecture-decision.md` |
| Prototype | `prototype/` |
| Estimation | `estimation.md` |
| Scope Changes | `docs/SC_XXX/` |
| Scope Change Generator | `docs/gen-scope-changes.js` |
| Estimation Generator | `docs/gen-estimation.js` |
| Weekly Status Reports | `weekly-status-wXX.md` |
| Lessons Learned | `lessons-learned.md` |

## How Work Flows Here

1. **Start a new project** → Load `run-discovery` skill, gather context, generate charter
2. **Charter approved** → Load `run-architecture` skill, define stack and infrastructure
3. **Architecture decided** → Load `build-prototype` skill, build clickable HTML screens
4. **Prototype reviewed** → Load `run-estimation` skill, break down all work with hours
5. **Estimation approved, work begins** → Load `run-execution` skill weekly
6. **Client answers questions** → Load `track-scope-changes` skill (anytime after estimation)
7. **Project delivered** → Load `run-retrospective` skill, analyze and improve

**Only one skill needs to be loaded at a time.** Claude reads this context to know which phase is active, then loads only the relevant skill.

## Roles

| Role | Responsibility |
|------|---------------|
| **Claude** | Discovery, architecture analysis, prototypes, estimation, documentation, risk flagging, retrospective |
| **Lead** | Client communication, final decisions, project ownership |
| **Developer(s)** | Code, implementation, unit testing |
| **QA** | Test planning, manual/automated testing, bug tracking |
| **Designer** | UI/UX design, prototypes, design system |
| **DevOps** | Infrastructure, CI/CD, deployments, monitoring |

In small teams, roles overlap. Claude adapts to whatever team composition exists. Claude also acts as Data Architect, UI/UX Designer, and Technical Architect when the team doesn't have dedicated resources.

## Rules

- **Language:** Documents and deliverables in English. Conversation can be in Spanish.
- **EMPA is internal only:** Never include "EMPA" in client-facing deliverables. Use only the project name and company name.
- **Never change hours silently:** Always verify against official documents, flag discrepancies, and get explicit approval before modifying estimation figures.
- **Prototypes use fictional data:** Never use real client data unless explicitly provided.
- **Evidence-based:** Every decision, estimation, and scope change traces back to documented evidence.

## What To Watch Out For

- Scope creep during execution — every change must go through `track-scope-changes`
- Skipping Phase 5 (Reflect) — this is where EMPA gets smarter for next time
- Loading all skills at once — only load what the current phase needs
- Forgetting to update this context file after phase transitions
