---
name: "Run Retrospective"
description: "Analyze project results — compare estimated vs actual, evaluate architecture decisions, update estimation factors for future projects"
version: "1.0"
phase: "5"
contexts:
  - "empa-project"
triggers:
  - "project is delivered"
  - "user says 'project is done, let's reflect'"
  - "user provides final hours data"
inputs:
  - "estimation.md (original baseline)"
  - "All weekly-status-wXX.md files"
  - "Final actual hours by module and person"
  - "Scope change history (docs/SC_XXX/)"
outputs:
  - "lessons-learned.md"
---

# Skill: Run Retrospective

## Purpose

Analyze everything that happened during the project and improve future estimations. This is where EMPA gets smarter — estimation factors, architecture choices, and process decisions are evaluated against real data.

## Prerequisites

- [ ] Project is delivered (or a major milestone is complete)
- [ ] Final actual hours are available by module and person
- [ ] Weekly status reports exist (or at minimum, total actual hours)

## Process

### Step 1: Gather Final Data

Collect:
- Actual hours per module
- Actual hours per team member
- All scope changes applied
- Original estimation baseline vs final scope
- Timeline: planned vs actual delivery date

### Step 2: Calculate Key Metrics

| Metric | Formula | Target |
|--------|---------|--------|
| Deviation | (Actual - Estimated) / Estimated x 100 | < 20% |
| Accuracy | 100 - abs(Deviation) | > 80% |
| Adjustment Factor | Avg(Actual / Estimated) over last N projects | Evolves |
| MVP Delivery Rate | MVP tasks done / MVP tasks planned x 100 | 100% |
| Architecture Fit | Team assessment (1-5) | > 4 |

### Step 3: Analyze by Module

For each module:
- Was it over or under estimated?
- Why? (complexity was higher, scope changed, team was faster, etc.)
- What factor should have been used?

### Step 4: Analyze by Person

For each team member:
- Were they over or under budget?
- Were they assigned appropriate work for their skill level?
- Did learning curve estimates hold?

### Step 5: Evaluate Architecture

| Aspect | Score (1-5) | Notes |
|--------|-------------|-------|
| Tech stack fit | | Was it the right choice? |
| Team readiness | | Did the team ramp up fast enough? |
| Infrastructure | | Were environments sufficient? |
| CI/CD | | Did pipelines work smoothly? |
| Overall | | |

Key questions:
- Would we use this stack again?
- Would we use the same environment setup?
- What would we change?

### Step 6: Evaluate Prototype Impact

- Did the prototype help sell/align the project?
- Was the CSS approach effective?
- Which screens impressed most?
- What would we add next time?

### Step 7: Update Estimation Factors

Based on actual data, propose updated factors:

| Complexity | Previous Factor | Recommended Factor | Based On |
|-----------|----------------|-------------------|----------|
| Low | x1.2 | x?.? | [evidence] |
| Medium | x1.5 | x?.? | [evidence] |
| High | x2.0 | x?.? | [evidence] |

These updated factors should be used in the next EMPA project.

### Step 8: Generate Lessons Learned

Generate `lessons-learned.md` in the project root:

```markdown
# Lessons Learned: EMPA-[ProjectName]

## Project Summary
| Item | Value |
|------|-------|
| Duration | |
| Stack | |
| Environments | |
| Team Size | |
| Total Estimated | |
| Total Actual | |
| Deviation | |
| Accuracy | |

## Analysis by Module
| Module | Estimated | Actual | Deviation % | Notes |
|--------|-----------|--------|-------------|-------|

## Analysis by Team Member
| Member | Role | Estimated | Actual | Deviation % | Notes |
|--------|------|-----------|--------|-------------|-------|

## Architecture Assessment
| Aspect | Score (1-5) | Notes |
|--------|-------------|-------|
| Tech stack fit | | |
| Team readiness | | |
| Infrastructure | | |
| CI/CD | | |
| Overall | | |

Would we use this stack again? [Yes / No / With changes]
Would we use the same environment setup? [Yes / No / With changes]

## Prototype Assessment
- Did it help win/align the project? [Yes / No]
- Was the CSS approach effective? [Yes / No]
- Screens that impressed most: [list]
- What would we add next time: [list]

## Scope Change Summary
| Batch | Net Impact | Key Changes |
|-------|-----------|-------------|

## Updated Estimation Factors
| Complexity | Previous | New | Based On |
|-----------|----------|-----|----------|

## What Went Well
1. [Item]

## What To Improve
1. [Item]

## Recommendations for Next Project
1. [Item]
```

## Verification

- [ ] All metrics are calculated with real data (not estimates of estimates)
- [ ] Module-level analysis identifies over/under estimation patterns
- [ ] Person-level analysis is fair and constructive
- [ ] Architecture assessment is honest (not just "it was fine")
- [ ] Estimation factors are updated based on evidence
- [ ] Lessons learned document is complete and actionable
- [ ] Team lead has reviewed and agreed with the assessment

## Common Mistakes

- Skipping this phase entirely — "we're already on the next project" kills learning
- Using estimated hours instead of actual hours — the whole point is comparing real data
- Being too generous in the architecture assessment — honest scores improve future decisions
- Not updating estimation factors — if you don't update them, the next project repeats the same errors
- Writing vague lessons like "communicate better" — be specific: what, when, how
