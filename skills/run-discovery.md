---
name: "Run Discovery"
description: "Drive the discovery phase — understand the business problem, define scope, generate project charter and discovery questions"
version: "1.0"
phase: "1"
contexts:
  - "empa-project"
triggers:
  - "new EMPA project starts"
  - "user says 'we have a new project'"
  - "user uploads project context, briefs, or SOWs"
inputs:
  - "Any available context: emails, briefs, SOWs, meeting notes, technical docs"
outputs:
  - "project-charter.md"
  - "discovery-questions.md (living backlog of open questions)"
---

# Skill: Run Discovery

## Purpose

Understand the business problem, define scope, and align expectations before any technical decisions. This is the foundation — everything else (architecture, estimation, execution) depends on a solid charter.

## Prerequisites

- [ ] Project context provided (emails, briefs, SOWs, meeting notes, or verbal description)
- [ ] Team lead available for back-and-forth

## Process

### Step 1: Gather Context

Read everything the user provides — uploads, descriptions, links, existing documents. Extract every fact before asking a single question.

### Step 2: Ask Discovery Questions (2-3 at a time)

Ask about the following, adapting based on answers. Never dump all questions at once.

1. What is the business problem? Why does this project exist?
2. Who is the client? What do they expect to receive?
3. What are the concrete deliverables?
4. Who are the stakeholders and their decision-making roles?
5. What are the constraints? (time, budget, people, technology)
6. What does success look like? How will we measure it?
7. What is in scope and what is explicitly NOT in scope?
8. What assumptions are we making?
9. Is there prior work, existing systems, or migration needs?
10. Any known risks or external dependencies?

**Critical rule:** Not everything needs to be a direct question. Some things you infer from context, some you flag as recommendations. If you don't have enough info, THEN you ask.

### Step 3: Generate Project Charter

When you have enough information, generate `project-charter.md` in the project root:

```markdown
# Project Charter: EMPA-[ProjectName]

## General Information
- **Project:** EMPA-[Name]
- **Client:** [Name]
- **Lead:** [Name]
- **Team:** [Names and roles]
- **Date:** [Date]

## Business Problem
[What problem are we solving and why]

## Objectives
1. [Objective]

## Scope
### In Scope
- [Item]

### Out of Scope
- [Item]

## Deliverables
| # | Deliverable | Description | Format |
|---|-------------|-------------|--------|

## Stakeholders
| Name | Role | Involvement |
|------|------|-------------|

## Timeline
| Milestone | Target Date |
|-----------|-------------|

## Assumptions
- [Assumption]

## Constraints
- [Constraint]

## Success Criteria
1. [Criterion]

## Known Risks
| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
```

### Step 4: Discovery Q&A Backlog (Phase 1B)

After the charter, generate `discovery-questions.md` — a living backlog of open questions that need client answers before architecture can be finalized.

Categorize questions by area:
- **Business / Scope** — clarifications on what the client wants
- **Technical** — constraints, integrations, existing systems
- **Data** — volumes, migration, formats
- **Users / Access** — roles, permissions, user flows
- **Timeline / Priority** — deadlines, MVP vs full scope

Format each question with:
- Question number (Q1, Q2, ...)
- The question
- Why it matters (what decision it unblocks)
- Default assumption if unanswered

```markdown
# Discovery Questions: EMPA-[ProjectName]

## Status: [X] of [Y] answered

## Business / Scope
| # | Question | Why It Matters | Default Assumption | Answer |
|---|----------|---------------|-------------------|--------|
| Q1 | [Question] | [Impact] | [Assumption] | — |

## Technical
| # | Question | Why It Matters | Default Assumption | Answer |
|---|----------|---------------|-------------------|--------|

## Data
...
```

### Step 5: Present and Iterate

Present the charter to the team lead. Iterate until approved. Do not move to Architecture until the charter is confirmed.

## Verification

- [ ] Business problem is clearly stated — anyone can read it and understand why this project exists
- [ ] Scope has explicit "In Scope" and "Out of Scope" sections
- [ ] All known stakeholders are identified with roles
- [ ] Assumptions are documented (not left implicit)
- [ ] Discovery questions backlog exists with prioritized open questions
- [ ] Team lead has approved the charter

## Common Mistakes

- Asking all 10 questions at once instead of 2-3 at a time — overwhelms the user
- Generating the charter too early with gaps — better to ask one more question than guess
- Not documenting "Out of Scope" — this causes scope creep later
- Treating discovery questions as optional — unanswered questions become wrong assumptions in architecture
- Assuming the client said something they didn't — always trace back to evidence
