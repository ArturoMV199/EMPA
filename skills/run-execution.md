---
name: "Run Execution"
description: "Track weekly progress during project execution — generate status reports, flag drift, and help with decisions"
version: "1.0"
phase: "4"
contexts:
  - "empa-project"
triggers:
  - "estimation is approved and work begins"
  - "user says 'here's what we did this week'"
  - "user provides weekly progress update"
inputs:
  - "Approved estimation.md"
  - "Weekly progress data (tasks completed, hours spent, blockers)"
outputs:
  - "weekly-status-wXX.md (per week)"
---

# Skill: Run Execution

## Purpose

Track progress during project execution. Generate weekly status reports, compare estimated vs actual hours, flag drift early, and help the team make informed decisions when things change.

## Prerequisites

- [ ] `estimation.md` exists and is approved
- [ ] Team is actively working on the project
- [ ] Weekly progress data is available

## Process

### Step 1: Collect Weekly Data

Ask the team lead for:
- Tasks completed this week (with who did them)
- Actual hours per task
- Tasks started but not finished
- Blockers or issues encountered
- Decisions made during the week
- Scope changes (if any — route to `track-scope-changes` skill)

### Step 2: Compare Estimated vs Actual

For each completed task:
- Find the task in `estimation.md`
- Compare estimated hours vs actual hours
- Calculate deviation per task

For the project overall:
- Cumulative estimated hours (for completed work)
- Cumulative actual hours
- Current deviation percentage
- Projected final hours based on current pace

### Step 3: Flag Drift Early

| Deviation | Status | Action |
|-----------|--------|--------|
| < 10% | On Track | Continue as planned |
| 10-20% | Watch | Note in status report, monitor next week |
| 20-30% | At Risk | Flag to team lead, suggest adjustments |
| > 30% | Critical | Recommend scope cuts or timeline extension |

Drift signals to watch:
- A module consistently over-estimating or under-estimating
- One team member significantly over or under budget
- Infrastructure/DevOps tasks taking longer than expected (common)
- Learning curve eating more hours than buffered

### Step 4: Generate Weekly Status Report

Generate `weekly-status-wXX.md` in the project root:

```markdown
# Week [#] Status: EMPA-[ProjectName]
## [Date Range]

## Status: On Track / At Risk / Blocked

## Summary
[What happened this week in 2-3 sentences]

## Completed
| Task | Owner | Est. Hours | Actual Hours | Deviation |
|------|-------|------------|--------------|-----------|

## In Progress
| Task | Owner | Est. Hours | Hours Spent | % Complete |
|------|-------|------------|-------------|------------|

## Next Week
| Task | Owner | Est. Hours |
|------|-------|------------|

## Blockers
| Blocker | Impact | Action | Owner |
|---------|--------|--------|-------|

## Estimation Health
| Metric | Value |
|--------|-------|
| Cumulative estimated (completed tasks) | X hrs |
| Cumulative actual | X hrs |
| Current deviation | X% |
| Projected final hours | X hrs |
| Budget remaining | X hrs |

## Per-Person Tracking
| Member | Est. Hours (completed) | Actual Hours | Deviation |
|--------|----------------------|--------------|-----------|

## Per-Module Tracking
| Module | Est. Hours (completed) | Actual Hours | Deviation |
|--------|----------------------|--------------|-----------|

## Decisions Made This Week
- [Date] [Decision and reasoning]

## Notes
- [Architecture changes, risks identified, lessons learned]
```

### Step 5: Weekly Rhythm

| Day | Activity | What Claude Does |
|-----|----------|-----------------|
| Monday | Plan the week | Help prioritize tasks, suggest order based on dependencies |
| Tue-Thu | Execute | Available for technical questions, architecture decisions |
| Friday | Review the week | Generate status report, calculate drift, flag risks |

### Step 6: Help With Decisions During Execution

Claude assists with:
- Architecture questions that come up during development
- Evaluating scope change requests vs original estimation
- Suggesting scope cuts when timeline is at risk
- Rebalancing work across team members
- Technical tradeoff decisions

## Verification

- [ ] Weekly status report is generated with all sections
- [ ] Estimated vs actual hours are compared per task
- [ ] Deviation percentage is calculated correctly
- [ ] Per-person and per-module tracking is included
- [ ] Drift is flagged with appropriate severity (On Track / At Risk / Critical)
- [ ] Blockers are documented with action items and owners
- [ ] Decisions made during the week are logged

## Common Mistakes

- Generating status reports without actual hours data — estimates alone tell you nothing
- Not tracking per-person and per-module — drift hides in averages
- Waiting until deviation is > 30% to flag it — by then it's too late
- Not logging decisions made during execution — future sessions lose context
- Treating scope changes during execution as informal — always route through `track-scope-changes`
