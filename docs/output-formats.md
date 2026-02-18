# Document Output Formats

These are the formats Claude uses when generating project documents.
They are NOT templates to fill manually — Claude produces them from conversations.

---

## 1. Project Charter

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

---

## 2. Architecture Decision

```markdown
# Architecture Decision: EMPA-[ProjectName]

## Project Context
[Summary from charter]

## Team
| Member | Role | Availability | Key Skills |
|--------|------|-------------|------------|

## Requirements Summary
### Functional
- [Requirement]

### Non-Functional
- Performance: [needs]
- Scalability: [needs]
- Security: [needs]

## Options Evaluated

### Option A: [Name]
**Stack:** [e.g., React + Node.js + PostgreSQL + AWS]
- Pros: ...
- Cons: ...
- Team familiarity: Low/Medium/High
- Estimated infra cost: $/mo
- Best for: [scenario]

### Option B: [Name]
**Stack:** [e.g., Angular + .NET + SQL Server + Azure]
- Pros: ...
- Cons: ...
- Team familiarity: Low/Medium/High
- Estimated infra cost: $/mo
- Best for: [scenario]

## Recommendation
**Selected:** Option [X]
**Reasoning:** [Why this fits best]

## Final Architecture

### Platform
[Web / Mobile / Both / PWA]

### Frontend
- Framework: [e.g., React 18]
- UI Library: [e.g., Tailwind CSS]
- State: [e.g., Zustand]

### Backend
- Pattern: [e.g., MVC]
- Framework: [e.g., Express.js]
- API: [REST / GraphQL]
- Auth: [e.g., JWT + OAuth2 via Auth0]

### Database
- Primary: [e.g., PostgreSQL]
- Cache: [e.g., Redis]
- ORM: [e.g., Prisma]

### Environments
| Environment | Purpose | App Services | Database | Swap Slots |
|-------------|---------|-------------|----------|------------|
| Dev | Development and testing | 1 | Shared | No |
| Test | QA validation | 1 | Dedicated | No |
| Staging | Pre-production | 1 | Dedicated | Yes |
| Production | Live | 1-N | Dedicated | Yes |

### CI/CD
- Platform: [e.g., GitHub Actions]
- Branch Strategy: [e.g., GitHub Flow]
- Pipeline: build → test → lint → deploy
- Deployment: [auto on merge to main / manual gates]
- Rollback: [strategy]
- IaC: [Terraform / Bicep / none]
- Secrets: [Key Vault / Secrets Manager]

### Team Responsibility Map
| Area | Owner | Backup |
|------|-------|--------|
| Frontend | [Name] | [Name] |
| Backend | [Name] | [Name] |
| Database | [Name] | [Name] |
| CI/CD | [Name] | [Name] |
| Infrastructure | [Name] | [Name] |
| QA | [Name] | [Name] |

### Third-Party Services
| Service | Provider | Purpose | Cost |
|---------|----------|---------|------|

### Architecture Diagram
[ASCII diagram of components]

## Risks
| Risk | Impact | Mitigation |
|------|--------|------------|

## Skill Gaps
| Technology | Team Level | Action |
|-----------|-----------|--------|

## Estimated Monthly Infrastructure Cost
| Item | Cost |
|------|------|
| Compute | $ |
| Database | $ |
| Storage | $ |
| Other | $ |
| **Total** | **$** |
```

---

## 3. Prototype Structure

```
prototype/
    index.html          <- Login or landing (entry point)
    dashboard.html      <- Main dashboard / home
    feature-1.html      <- Core feature screen
    feature-2.html      <- Secondary feature
    settings.html       <- Settings / profile
    css/
        prototype.css   <- Custom styles with CSS variables
    img/
        logo.png        <- Brand assets if available
```

**Technical standards:**
- Raw HTML + custom CSS (or lightweight framework via CDN)
- Inline SVG icons ONLY — no Font Awesome or external icon CDNs
- CSS custom properties (:root) for all brand colors
- Google Fonts via CDN for typography
- Working navigation links between all screens
- Realistic placeholder data (never Lorem ipsum)
- Professional quality — should look like a real application

---

## 4. Estimation

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
| # | Module | Task | Owner | Complexity | Est. Hours | Factor | Adjusted |
|---|--------|------|-------|------------|------------|--------|----------|

### Post-MVP (Should Have)
| # | Module | Task | Owner | Complexity | Est. Hours | Factor | Adjusted |
|---|--------|------|-------|------------|------------|--------|----------|

### Backlog (Could Have)
| # | Task |
|---|------|

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

---

## 5. Weekly Status

```markdown
# Week [#] Status: EMPA-[ProjectName]
## [Date Range]

## Status: On Track / At Risk / Blocked

## Summary
[What happened]

## Completed
| Task | Owner | Est. Hours | Actual Hours |
|------|-------|------------|--------------|

## Next Week
| Task | Owner | Est. Hours |
|------|-------|------------|

## Blockers
| Blocker | Impact | Action |
|---------|--------|--------|

## Estimation Health
| Metric | Value |
|--------|-------|
| Cumulative estimated | |
| Cumulative actual | |
| Current deviation | |
| Projected final hours | |

## Notes
- [Decisions, changes, architecture notes]
```

---

## 6. Lessons Learned

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
| Module | Estimated | Actual | Deviation % |
|--------|-----------|--------|-------------|

## Analysis by Team Member
| Member | Role | Estimated | Actual | Deviation % |
|--------|------|-----------|--------|-------------|

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

## Updated Estimation Factors
| Complexity | Previous | New |
|-----------|----------|-----|

## Recommendations
1. [Item]
```
