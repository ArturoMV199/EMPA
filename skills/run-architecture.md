---
name: "Run Architecture"
description: "Drive the architecture phase — define stack, infrastructure, environments, CI/CD, team roles, and produce the architecture decision document"
version: "1.0"
phase: "2"
contexts:
  - "empa-project"
triggers:
  - "charter is approved"
  - "user says 'let's decide the architecture'"
  - "user asks about tech stack or infrastructure"
inputs:
  - "Approved project-charter.md"
  - "Technical docs, API docs, system diagrams (if available)"
  - "Discovery questions answers (if available)"
outputs:
  - "architecture-decision.md"
---

# Skill: Run Architecture

## Purpose

Define the complete technical solution — not just the framework, but the full picture: platform, stack, infrastructure, environments, CI/CD, team roles, integrations, and cost. Architecture decisions change hours, cost, complexity, and timeline. You cannot estimate accurately without this.

## Prerequisites

- [ ] `project-charter.md` exists and is approved by the team lead
- [ ] Team lead available for discussion and decisions

## Process

### Step 1: Analyze Existing Context

Read the charter, uploaded docs, and any discovery question answers. Extract every technical fact, constraint, and inference before asking anything.

### Step 2: Run Internal Checklists

Go through ALL checklists below. For each item: mark it as known (from context), inferred (reasonable assumption), or unknown (needs a question). Only ask about critical unknowns.

#### Team & Resources
- How many developers? Frontend? Backend? Fullstack?
- Dedicated QA? Manual? Automated? Both?
- Designer? UI/UX? Figma/Sketch deliverables or wireframes?
- DevOps engineer? Dedicated or shared?
- Who owns CI/CD setup and maintenance?
- Who owns infrastructure provisioning?
- Who owns database administration?
- Experience level per team member with proposed tech?
- Skill gaps requiring training?
- Part-time or shared team members?
- Working hours and timezone?

#### Platform & Frontend
- Web, mobile, desktop, or combination?
- If web: SPA, MPA, or SSR?
- If mobile: Native, cross-platform (React Native, Flutter), or hybrid?
- PWA as alternative to native mobile?
- Framework: React, Angular, Vue, Next.js, Nuxt, Svelte, Blazor?
- UI library: Tailwind, MUI, Bootstrap, Ant Design, custom?
- State management: Redux, Zustand, Pinia, NgRx, Context API?
- Real-time needs: WebSockets, SSE, polling?
- Offline support, browser/device support, accessibility (WCAG), i18n?

#### Backend & API
- Pattern: MVC, microservices, serverless, modular monolith?
- Framework: Node/Express/Nest, .NET/C#, Python/Django/FastAPI, Java/Spring, Go?
- API: REST, GraphQL, gRPC, or combination?
- Auth: JWT, OAuth2, SSO, SAML? Provider: Auth0, Clerk, Azure AD, Cognito, custom?
- Authorization: RBAC, ABAC, custom?
- Background jobs: queues, workers, scheduled tasks?
- File storage, email service, logging, error tracking?

#### Database
- SQL: PostgreSQL, MySQL, SQL Server?
- NoSQL: MongoDB, DynamoDB, CosmosDB?
- Need both? Caching: Redis? Search: Elasticsearch, Algolia?
- ORM/ODM, data volume, read/write patterns, migrations, backup strategy?

#### Infrastructure & Environments
- Cloud: AWS, Azure, GCP?
- Specific services: App Services, Functions, ECS, Lambda, Container Apps?
- How many environments: 2 (Dev, Prod), 3 (Dev, Test, Prod), 4 (Dev, Test, Staging, Prod)?
- Deployment slots / swap slots?
- How many App Services or compute instances per environment?
- Database per environment or shared?
- Docker? Kubernetes? Container registry?
- Networking: VNet/VPC, load balancers, API gateway?
- DNS, SSL, CDN?

#### CI/CD
- Platform: GitHub Actions, Azure DevOps, GitLab CI, Jenkins?
- Who builds and maintains pipelines?
- Pipeline stages: build, test, lint, deploy?
- Branch strategy: GitFlow, trunk-based, GitHub Flow?
- Deployment: manual trigger, auto on merge, scheduled?
- Environment promotion: auto or manual approval gates?
- Rollback strategy?
- IaC: Terraform, Bicep, CloudFormation, Pulumi?
- Secrets: Azure Key Vault, AWS Secrets Manager, HashiCorp Vault?

#### Integrations, Security & Cost
- Payments, SMS, analytics, monitoring, external APIs, webhooks?
- Compliance: GDPR, HIPAA, SOC2, PCI-DSS?
- Encryption, WAF, rate limiting, audit logs?
- Monthly infra budget, licensing, per-environment cost?

### Step 3: Ask Critical Unknowns (2-3 at a time)

Only ask what you cannot infer. Prioritize high-impact unknowns — decisions that change the estimation by 20+ hours or affect the architecture fundamentally.

**Do NOT default to the most popular tech.** Recommend based on: project needs, team skills, timeline, budget, client constraints, and infrastructure reality.

### Step 4: Propose Architecture Options

Present 2-3 options with:
- Stack summary
- Pros and cons
- Team familiarity (Low / Medium / High)
- Estimated monthly infrastructure cost
- Best-for scenario
- Recommendation with reasoning

### Step 5: Document Third-Party Libraries

Every architecture decision MUST include a clear table of third-party libraries. For each:

| Field | What to Include |
|-------|----------------|
| Library name | The actual package/service name |
| Purpose | What it does in plain language (not everyone knows what "AG Grid" means) |
| License | MIT, Apache 2.0, GPL, Commercial, Freemium |
| Cost | $0, per-dev/year, per-project, enterprise pricing |
| Alternative | What to use if primary doesn't work |

### Step 6: Map Team to Responsibilities

| Area | Owner | Backup |
|------|-------|--------|
| Frontend | [Name] | [Name] |
| Backend | [Name] | [Name] |
| Database | [Name] | [Name] |
| CI/CD | [Name] | [Name] |
| Infrastructure | [Name] | [Name] |
| QA | [Name] | [Name] |

### Step 7: Generate Architecture Decision Document

Generate `architecture-decision.md` in the project root:

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
...

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
- Pipeline: build > test > lint > deploy
- Deployment: [auto on merge to main / manual gates]
- Rollback: [strategy]
- IaC: [Terraform / Bicep / none]
- Secrets: [Key Vault / Secrets Manager]

### Team Responsibility Map
| Area | Owner | Backup |
|------|-------|--------|

### Third-Party Services & Libraries
| Service/Library | Purpose (plain language) | License | Cost | Alternative |
|-----------------|------------------------|---------|------|-------------|

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

### Step 8: Discuss and Confirm

Present the document. Team discusses. Iterate until the team lead confirms the architecture.

## Verification

- [ ] All checklist areas were considered (even if some were inferred, not asked)
- [ ] 2-3 options were presented with pros, cons, and cost
- [ ] One option was recommended with clear reasoning
- [ ] Third-party libraries are documented with license, cost, and plain-language purpose
- [ ] Team members are mapped to responsibilities
- [ ] Infrastructure cost per month is estimated
- [ ] Skill gaps are identified with action plans
- [ ] Team lead has approved the architecture

## Common Mistakes

- Defaulting to the most popular stack instead of what fits the team and project
- Forgetting infrastructure cost per environment — 4 environments is 4x compute cost
- Listing libraries without explaining what they do — "AG Grid Enterprise" means nothing to a manager
- Not mapping team to responsibilities — estimation depends on WHO does WHAT
- Skipping CI/CD and DevOps — these are real hours that must be estimated later
- Asking too many questions when the answer is inferable from context
