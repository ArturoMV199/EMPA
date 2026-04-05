---
name: "Build Prototype"
description: "Build a clickable HTML prototype that shows the client what the application will look and feel like — a sales and alignment tool"
version: "1.0"
phase: "2B"
contexts:
  - "empa-project"
triggers:
  - "architecture is decided"
  - "user says 'let's build the prototype'"
  - "user wants to show the client what the app will look like"
inputs:
  - "Approved architecture-decision.md"
  - "Brand assets if available (logo, colors, fonts)"
outputs:
  - "prototype/ folder with HTML + CSS files"
---

# Skill: Build Prototype

## Purpose

Deliver a clickable HTML prototype that shows the client what the application will look and feel like before writing any functional code. This is a sales and alignment tool — de la vista nacen grandes proyectos. A polished prototype closes deals, aligns expectations, and gives the team a visual north star.

## Prerequisites

- [ ] `architecture-decision.md` exists and is approved
- [ ] Brand info available (or defaults will be used)

## Process

### Step 1: Define Screens

Based on the charter and architecture, identify which screens to build. Typical set:

| Screen | Purpose |
|--------|---------|
| Login / Sign-in | First impression, sets brand tone |
| Dashboard / Home | Shows main value of the application |
| Navigation / Menu | Demonstrates information architecture |
| Core Feature #1 | The primary thing the app does |
| Core Feature #2 | Secondary key feature (if applicable) |
| Settings / Profile | Shows depth and completeness |

Confirm the screen list with the team lead before building.

### Step 2: Set Up Brand Variables

Every prototype starts with CSS custom properties:

```css
:root {
    --brand-primary: #1a2634;
    --brand-primary-light: #2c3e50;
    --brand-accent: #3498db;
    --brand-accent-hover: #5dade2;
    --brand-white: #ffffff;
    --brand-gray-100: #f8fafc;
    --brand-gray-200: #e2e8f0;
    --brand-gray-400: #94a3b8;
    --brand-gray-600: #64748b;
    --brand-success: #10b981;
    --brand-warning: #f59e0b;
    --brand-danger: #ef4444;
}

body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
```

Replace values with actual brand colors if provided.

### Step 3: Choose CSS Approach

Pick based on project fit:

| Approach | Best For | Vibe |
|----------|----------|------|
| Custom CSS + CSS Variables | Full control, any brand | Tailored, professional |
| Bootstrap 5 (CDN) | Fast prototyping, corporate | Standard, familiar |
| Tailwind CSS (CDN) | Modern look, utility-first | Startup, modern |
| Pure.css (CDN) | Minimal, lightweight | Clean, elegant |
| Bulma (CDN) | Flexbox-based, easy | Clean, modern |
| Pico CSS (CDN) | Classless, semantic HTML | Ultra-minimal |

### Step 4: Build Screens

Build each screen following these mandatory rules:

**HTML:**
- Each screen is its own HTML file
- Every navigation link between screens MUST work (real hrefs, not #)
- Consistent navbar/header on every page
- Footer with copyright and version number on every page

**Icons — INLINE SVG ONLY:**
- NEVER use Font Awesome, Lucide CDN, Feather CDN, or any external icon library
- Every icon is an inline SVG element directly in the HTML
- Use stroke-based SVGs: `viewBox="0 0 24 24"`, `fill="none"`, `stroke="currentColor"`, `stroke-width="2"`

```html
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
     stroke-linecap="round" stroke-linejoin="round">
    <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/>
</svg>
```

**Data:**
- ALL placeholder data must look real — real names, dates, amounts, statuses
- NEVER use Lorem ipsum, "John Doe", "test@test.com", or obviously fake data
- Data should tell a story that makes sense for the application domain
- Use fictional/invented data — never real client data unless explicitly provided

**Quality:**
- A client should believe it's a working application at first glance
- Not a wireframe, not a mockup — it looks like a real app
- Transitions and hover states where appropriate (CSS only)
- Consistent spacing, typography, and color usage throughout
- Responsive if the project requires it

### Step 5: Organize File Structure

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

### Step 6: Review and Iterate

Present the prototype to the team lead. Walk through each screen. Iterate on:
- Look and feel
- Navigation flow
- Data realism
- Missing screens or features

## Verification

- [ ] All planned screens are built
- [ ] Every navigation link works (no broken links, no # placeholders)
- [ ] Every icon is an inline SVG (zero external icon dependencies)
- [ ] Brand colors are in CSS :root variables
- [ ] Placeholder data looks real and domain-appropriate
- [ ] Consistent header/footer across all pages
- [ ] `prototype/index.html` is the entry point
- [ ] Team lead has reviewed and approved

## Common Mistakes

- Using Font Awesome or any external icon CDN — breaks the zero-dependency rule
- Using Lorem ipsum or "John Doe" — kills the illusion of a real app
- Links that go to `#` instead of actual pages — client clicks and nothing happens
- Inconsistent colors — using hardcoded hex instead of CSS variables
- Building too many screens — 4-6 key screens is enough, don't build the whole app
- Forgetting mobile responsiveness when the project requires it
