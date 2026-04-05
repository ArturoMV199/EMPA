---
name: "Run Estimation"
description: "Break down all project work into estimated tasks, map to team members, define MVP with MoSCoW, and produce the estimation document"
version: "1.0"
phase: "3"
contexts:
  - "empa-project"
triggers:
  - "architecture is decided"
  - "prototype is done"
  - "user says 'let's estimate'"
inputs:
  - "Approved project-charter.md"
  - "Approved architecture-decision.md"
  - "Discovery question answers (if available)"
outputs:
  - "estimation.md"
---

# Skill: Run Estimation

## Purpose

Produce an accurate estimation based on WHAT (charter), HOW (architecture), and WHO (team). EMPA estimates ALL real work — not just code, but infrastructure, CI/CD, DevOps, QA, learning curve, and bug buffer.

## Prerequisites

- [ ] `project-charter.md` exists and is approved
- [ ] `architecture-decision.md` exists and is approved
- [ ] Team composition and availability is known

## Process

### Step 1: Identify All Work Areas

Estimate everything. No area gets skipped:

- Frontend development
- Backend development
- Database design and setup
- API development and integration
- Infrastructure setup (per environment — multiply by number of environments)
- CI/CD pipeline creation
- DevOps configuration
- UI/UX design implementation
- QA testing (manual and automated)
- Documentation
- Deployment and go-live
- Knowledge transfer
- Bug buffer (10-15%)
- Learning curve (new tech for team)

### Step 2: Apply Estimation Factors

| Complexity | When to Use | Factor |
|-----------|------------|--------|
| Low | Team knows the tech, clear requirements, done before | x1.2 |
| Medium | Some unknowns, moderate research or learning needed | x1.5 |
| High | New tech for team, many unknowns, external dependencies | x2.0 |

Every task gets a base estimate (ideal hours) multiplied by its complexity factor.

### Step 3: Define MVP with MoSCoW

| Priority | Meaning | Rule |
|----------|---------|------|
| **Must Have** | MVP — project fails without this | If client explicitly requested it, it goes here. Always. |
| **Should Have** | Post-MVP — important, can wait | |
| **Could Have** | Backlog — nice to have | |
| **Won't Have** | Out of scope | |

**Critical rule:** If the client explicitly requested a feature (in a transcript, scoping call, or requirements doc), it goes in **Must Have** — even if it's complex. Features suggested by the team go in **Should Have** or **Could Have**.

Label every item with its source:
- `Client-requested` — Feature explicitly asked for by client
- `Suggested enhancement` — Added by team as value-add, not requested

### Step 4: Map Tasks to Team Members

Assign every task to a person. Show:
- What can run in parallel vs sequential
- Critical path (what blocks what)
- Per-person workload balance

### Step 5: Generate Estimation Document

Generate `estimation.md` in the project root:

```markdown
# Estimation: EMPA-[ProjectName]

## Scope Summary
[From charter]

## Architecture Summary
[Stack, environments, team — from architecture decision]

## MVP Definition
**Core question:** [The ONE question this must answer]
**MVP goal:** [Minimum deliverable]

### MVP Scope (Must Have)
| # | Module | Task | Owner | Complexity | Est. Hours | Factor | Adjusted | Source |
|---|--------|------|-------|------------|------------|--------|----------|--------|

### Post-MVP (Should Have)
| # | Module | Task | Owner | Complexity | Est. Hours | Factor | Adjusted | Source |
|---|--------|------|-------|------------|------------|--------|----------|--------|

### Backlog (Could Have)
| # | Task | Source |
|---|------|--------|

### Out of Scope (Won't Have)
- [Item]

## Infrastructure & DevOps Estimation
| Task | Owner | Est. Hours | Factor | Adjusted |
|------|-------|------------|--------|----------|
| Environment setup (Dev) | | | | |
| Environment setup (Test) | | | | |
| Environment setup (Staging) | | | | |
| Environment setup (Prod) | | | | |
| CI/CD pipeline | | | | |
| Monitoring setup | | | | |
| DNS / SSL / CDN | | | | |

## Learning Curve Buffer
| Technology | Who | Hours | Justification |
|-----------|-----|-------|---------------|

## Bug Buffer
[10-15% of total adjusted hours]

## Team Allocation & Timeline
| Week | [Dev 1] | [Dev 2] | [QA] | [DevOps] |
|------|---------|---------|------|----------|
| 1 | [Task] | [Task] | [Task] | [Task] |
| 2 | [Task] | [Task] | [Task] | [Task] |

## Summary
| Concept | Value |
|---------|-------|
| MVP Hours | |
| Post-MVP Hours | |
| Infra/DevOps Hours | |
| Learning Curve Hours | |
| Bug Buffer Hours | |
| Full Scope Hours | |
| Estimated Working Days | |
| Target Delivery | |

## Monthly Operational Cost (post-launch)
| Item | Cost |
|------|------|
| Infrastructure | $ |
| Third-party services | $ |
| **Total** | **$** |

## Risks
| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|

## Past Project Comparison
| Project | Stack | Estimated | Actual | Deviation |
|---------|-------|-----------|--------|-----------|
```

### Step 6: Review and Validate

Present the estimation. Walk through:
- Are the hours realistic?
- Is the MVP correctly scoped?
- Is the team allocation balanced?
- Are there missing tasks?

Iterate until the team lead confirms.

## Verification

- [ ] ALL work areas are estimated (not just code — infra, CI/CD, QA, learning curve, bug buffer)
- [ ] Every task has an owner assigned
- [ ] Complexity factors are applied and justified
- [ ] MoSCoW prioritization is complete with source labels (client-requested vs suggested)
- [ ] Infrastructure is estimated per environment (not just once)
- [ ] Team allocation timeline shows parallel vs sequential work
- [ ] Summary totals are correct
- [ ] Team lead has approved the estimation

## Common Mistakes

- Estimating only code — forgetting infra per environment, CI/CD, DevOps, QA, documentation
- Not applying complexity factors — ideal hours are not real hours
- Putting team suggestions in Must Have — only client-requested features belong there
- Estimating infrastructure once instead of per environment — 4 environments = 4x setup
- Not mapping tasks to people — "the team will do it" is not a plan
- Silently changing hours after approval — always flag discrepancies and get explicit approval
