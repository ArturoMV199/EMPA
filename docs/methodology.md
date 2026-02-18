# EMPA Methodology

## What is EMPA?

**Estimation Methodology Plus Assessments** is an AI-assisted framework for small consulting and analysis teams (2-5 people). EMPA uses **Claude as an active team member** to drive discovery, architecture decisions, estimation, tracking, and documentation through conversation.

You bring the context. Claude asks the questions, recommends the tech stack, flags the risks, and generates the documents.

---

## How EMPA Works

```
+-----------+   +-----------+   +-----------+   +-----------+   +-----------+
| 1.DISCOVER| > |2.ARCHITECT| > | 3.ESTIMATE| > | 4.EXECUTE | > | 5.REFLECT |
|           |   |           |   |           |   |           |   |           |
| Understand|   | Define the|   | Break down|   | Track     |   | Analyze   |
| the WHAT  |   | HOW and   |   | tasks for |   | progress  |   | results & |
|           |   | the WHO   |   | the WHAT  |   | & flag    |   | improve   |
|           |   |           |   | with WHO  |   | drift     |   | factors   |
+-----------+   +-----------+   +-----------+   +-----------+   +-----------+
     WHAT?       HOW? WHO?        HOW LONG?       IS IT ON        WHAT DID
                 WHERE?           HOW MUCH?       TRACK?          WE LEARN?
```

---

## Phase 1: Discover (Claude-Led)

**Goal:** Understand the business problem, define scope, and align expectations.

**How it works:** You tell Claude what you know. Upload documents, emails, briefs — anything. Claude asks the questions needed to fully understand the scope.

**Claude asks about:**
- Business problem and objectives
- Client expectations and deliverables
- Stakeholders and decision makers
- Constraints (time, budget, resources)
- Success criteria
- Scope boundaries (in and out)
- Assumptions and prior work

**Output:** `project-charter.md`

**Start with:** "Claude, we have a new EMPA project. Here's what we know: [context]"

---

## Phase 2: Architect (Claude-Led Discussion)

**Goal:** Define the complete technical solution — not just the framework, but the full picture: platform, stack, infrastructure, environments, CI/CD, team roles, and integrations.

**Why this phase exists:** A React app with 2 devs on Azure with 3 environments is a completely different estimation than the same React app with 4 devs on AWS with 2 environments. Architecture decisions change hours, cost, complexity, and timeline. You cannot estimate accurately without this.

**What Claude considers (not everything becomes a question):**

Claude has comprehensive internal checklists covering:

**Team & Resources**
- Team size, roles, and availability (devs, QA, designer, DevOps)
- Who owns CI/CD, infrastructure, database admin
- Skill levels per technology
- Part-time or shared team members
- Skill gaps requiring training

**Platform & Frontend**
- Web, mobile, desktop, or combination
- Framework, UI library, state management
- Real-time, offline, accessibility, i18n needs

**Backend & API**
- Architecture pattern and framework
- API style, auth strategy, authorization model
- Background jobs, file storage, email, logging, error tracking

**Database**
- SQL vs NoSQL vs both
- Caching, search, ORM choice
- Data volume, migration needs, backup strategy

**Infrastructure & Environments**
- Cloud provider and specific services
- Number of environments (Dev / Test / Staging / Production)
- App Services or compute instances per environment
- Deployment slots and swap strategies
- Containerization and orchestration
- Networking, DNS, SSL, CDN

**CI/CD**
- Pipeline platform and stages
- Who builds and maintains pipelines
- Branch strategy and deployment strategy
- Environment promotion (auto vs manual gates)
- Rollback strategy
- Infrastructure as Code
- Secret management

**Integrations**
- Payments, notifications, analytics, monitoring
- External APIs and webhooks

**Security & Compliance**
- Data sensitivity and compliance requirements
- Encryption, WAF, rate limiting, audit logs

**Cost**
- Monthly infrastructure budget
- Licensing and per-environment costs

**Claude's process:**
1. Analyze everything from the charter and uploaded docs
2. Run through internal checklists — identify knowns, inferences, and critical unknowns
3. Ask only what's needed (2-3 questions at a time, prioritizing high-impact unknowns)
4. Propose 2-3 architecture options with pros, cons, cost, and trade-offs
5. Map team members to responsibilities
6. Recommend one option with reasoning
7. Team discusses and decides

**Output:** `architecture-decision.md`

**Start with:** "Charter is approved. Let's decide the architecture." (upload technical docs if you have them)

---

## Phase 2B: Visual Prototype (Claude-Built)

**Goal:** Deliver a clickable HTML prototype that shows the client what the application will look and feel like before writing any functional code. This is a sales and alignment tool — de la vista nacen grandes proyectos.

**Why this matters:** A polished prototype closes deals, aligns expectations, and gives the team a visual north star before writing functional code. It's not a wireframe — it looks like a real app.

**What the prototype IS:**
- Raw HTML + custom CSS (or lightweight framework via CDN)
- Inline SVG icons only — no Font Awesome, no external icon CDNs, no icon dependencies
- CSS custom properties (variables) for all brand colors, easy to swap later
- Google Fonts via CDN for typography
- Key screens connected with working navigation (real links, not #)
- Realistic placeholder data (real-looking names, numbers, dates — never Lorem ipsum)
- Polished enough to show a client and impress them

**What the prototype is NOT:**
- Not functional (no real auth, no API calls, no JavaScript logic beyond basic navigation)
- Not the final design (but close enough to set the right expectations)
- Not production code (it exists to sell the idea and align the team)

**Technical standards (based on our proven approach):**

```css
/* Every prototype starts with brand variables */
:root {
    --brand-primary: #1a2634;
    --brand-accent: #3498db;
    --brand-white: #ffffff;
    --brand-gray-100: #f8fafc;
    --brand-gray-200: #e2e8f0;
    --brand-gray-400: #94a3b8;
    --brand-gray-600: #64748b;
    --brand-success: #10b981;
    --brand-warning: #f59e0b;
    --brand-danger: #ef4444;
}
```

```html
<!-- Icons are always inline SVG — no external dependencies -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
     stroke-linecap="round" stroke-linejoin="round">
    <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/>
</svg>
```

**CSS approach — pick based on project fit:**

| Approach | Best For | Vibe |
|----------|----------|------|
| Custom CSS + CSS Variables | Full control, any brand | Tailored, professional |
| Bootstrap 5 (CDN) | Fast prototyping, corporate | Standard, familiar |
| Tailwind CSS (CDN) | Modern look, utility-first | Startup, modern |
| Pure.css (CDN) | Minimal, lightweight | Clean, elegant |
| Bulma (CDN) | Flexbox-based, easy | Clean, modern |
| Pico CSS (CDN) | Classless, semantic HTML | Ultra-minimal |

**Screens Claude typically builds:**

| Screen | Purpose |
|--------|---------|
| Login / Sign-in | First impression, sets brand tone |
| Dashboard / Home | Shows main value of the application |
| Navigation / Menu | Demonstrates information architecture |
| Core Feature #1 | The primary thing the app does |
| Core Feature #2 | Secondary key feature (if applicable) |
| Settings / Profile | Shows depth and completeness |

**Prototype file structure:**

```
prototype/
    index.html          <- Login or landing (entry point)
    dashboard.html      <- Main dashboard / home
    feature-1.html      <- Core feature screen
    feature-2.html      <- Secondary feature
    settings.html       <- Settings / profile
    css/
        prototype.css   <- Custom styles or overrides
    img/
        logo.png        <- Brand assets if available
```

**Rules:**
- Every link between screens must work
- Every icon is an inline SVG
- Brand colors live in CSS :root variables
- Data looks real (names, dates, amounts, statuses)
- Responsive if the project requires it
- Quality level: a client should believe it's a working app at first glance

**Output:** `prototype/` folder with HTML + CSS files

**Start with:** "Architecture is decided. Let's build the prototype." (or Claude may suggest it after architecture)

---

## Phase 3: Estimate (Claude-Led)

**Goal:** Produce an accurate estimation based on WHAT (charter), HOW (architecture), and WHO (team).

**What makes EMPA estimations different:** Claude estimates ALL real work:

- Frontend development
- Backend development
- Database design and setup
- API development and integration
- Infrastructure setup (per environment)
- CI/CD pipeline creation
- DevOps configuration
- UI/UX design implementation
- QA testing (manual and automated)
- Documentation
- Deployment and go-live
- Knowledge transfer
- Bug buffer (10-15%)
- Learning curve (new tech for team)

**Estimation factors:**

| Complexity | When to use | Factor |
|-----------|------------|--------|
| Low | Team knows the tech, clear requirements, done before | x1.2 |
| Medium | Some unknowns, moderate research or learning needed | x1.5 |
| High | New tech for team, many unknowns, external dependencies | x2.0 |

**Team allocation matters:** Claude maps tasks to people and shows what can run in parallel vs sequential. Timeline depends on this.

**MVP defined using MoSCoW:**
- **Must have** = MVP (project fails without this)
- **Should have** = Post-MVP (important, can wait)
- **Could have** = Backlog (nice to have)
- **Won't have** = Out of scope

**Output:** `estimation.md` with MVP, team allocation, and timeline

**Start with:** "Architecture and prototype are done. Let's estimate."

---

## Phase 4: Execute (Claude-Assisted)

**Goal:** Team executes while Claude tracks progress, flags drift, and helps with decisions.

**Weekly rhythm:**

| Day | Activity | Claude's Role |
|-----|----------|---------------|
| Monday | Plan the week | Helps prioritize, suggests task order based on dependencies |
| Tue-Thu | Execute | Available for technical questions, architecture decisions |
| Friday | Review the week | Generates status report, calculates drift, flags risks |

**Claude also helps with:**
- Architecture questions during development
- Evaluating scope change requests vs original estimation
- Suggesting scope cuts when timeline is at risk
- Tracking per-person and per-module hours

**Output:** `weekly-status.md` (per week)

**Start with:** "Here's what we did this week: [summary]"

---

## Phase 5: Reflect (Claude-Led)

**Goal:** Analyze everything and improve future estimations.

**Claude analyzes:**
- Actual vs estimated hours (by module, by person, by tech area)
- Was the architecture the right choice?
- Were environments sufficient?
- Did CI/CD work smoothly?
- Which complexity levels were under/over estimated?
- Did the prototype help sell/align the project?
- What should change for next time?

**Output:** `lessons-learned.md` with updated factors

**Start with:** "Project is done. Final hours: [data]. Let's reflect."

---

## Key Metrics

| Metric | Formula | Target |
|--------|---------|--------|
| Deviation | (Actual - Estimated) / Estimated x 100 | < 20% |
| Accuracy | 100 - abs(Deviation) | > 80% |
| Adjustment Factor | Avg(Actual / Estimated) over last N projects | Evolves |
| MVP Delivery Rate | MVP tasks done / MVP tasks planned x 100 | 100% |
| Architecture Fit | Team assessment (1-5) | > 4 |

---

## Roles

| Role | Responsibility |
|------|---------------|
| **Claude** | Discovery, architecture analysis, prototypes, estimation, documentation, risk flagging, retrospective |
| **Lead** | Client communication, final decisions, project ownership |
| **Developer(s)** | Code, implementation, unit testing |
| **QA** | Test planning, manual/automated testing, bug tracking |
| **Designer** | UI/UX design, prototypes, design system |
| **DevOps** | Infrastructure, CI/CD, deployments, monitoring |

Note: In small teams, roles overlap. Claude adapts to whatever team composition exists.

---

## Where to Work

| Tool | Use For |
|------|---------|
| **Claude.ai (Project)** | Discovery, architecture, estimation, status reports, retrospectives |
| **Claude Code (Terminal)** | Prototype generation, file management, repo management, pushing to GitHub |
| **GitHub (EMPA-ProjectName)** | Documentation, prototype hosting, version control, project archive |
