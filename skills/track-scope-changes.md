---
name: "Track Scope Changes"
description: "Log every scope change with client evidence, impact analysis, and before/after totals — generate Word/PDF documents"
version: "1.0"
phase: "3B"
contexts:
  - "empa-project"
triggers:
  - "client answers discovery questions"
  - "client makes a decision that affects scope"
  - "stakeholder changes requirements"
  - "user says 'client answered questions'"
inputs:
  - "Approved estimation.md"
  - "Client answers or decisions (with exact quotes)"
outputs:
  - "Updated estimation.md"
  - "docs/SC_XXX/scope-changes.json"
  - "docs/SC_XXX/scope-changes.docx (generated)"
  - "docs/SC_XXX/scope-changes.pdf (generated)"
---

# Skill: Track Scope Changes

## Purpose

Maintain a living record of every scope change with full traceability to the client answer or decision that caused it. Without this, hours creep silently and no one can explain why the project grew from 800 to 1,200 hours.

## Prerequisites

- [ ] `estimation.md` exists and is approved (baseline)
- [ ] Client answers or decisions available (with exact quotes)

## Process

### Step 1: Receive Client Answers

Get the batch of client answers. Each answer must include:
- The question it responds to
- The exact client response (verbatim — this is the evidence trail)

### Step 2: Evaluate Impact Per Answer

For each client answer, determine:

| Type | Badge | Meaning | Example |
|------|-------|---------|---------|
| `confirmed` | Blue | Validates existing assumption | "Yes, 5 roles as described" → 0 hrs |
| `added` | Green | New scope from client answer | "We need bid revision tracking" → +15 hrs |
| `modified` | Orange | Existing scope changed | "Thresholds visual only" → -9 hrs |
| `removed` | Red | Scope removed by client decision | "Drop email notifications" → -18 hrs |

**Every answer gets an entry — even if impact is 0 hrs.** Use `confirmed` for zero-impact validations. This creates a complete audit trail.

### Step 3: Update Estimation

Modify `estimation.md` with:
- New line items (for `added`)
- Changed hours (for `modified`)
- Removed items (for `removed`)
- No changes needed (for `confirmed`)

### Step 4: Create Scope Change Entry

Create a new folder `docs/SC_XXX/` and add `scope-changes.json`:

```json
{
  "project": "EMPA-[ProjectName] — [Description]",
  "option": "[Selected architecture option]",
  "baseline": {
    "date": "YYYY-MM-DD",
    "mvpHours": 0,
    "postMvpHours": 0,
    "learningHours": 0,
    "fullScopeHours": 0,
    "note": "Initial estimation before client Q&A."
  },
  "changes": [
    {
      "id": "SC-001",
      "date": "YYYY-MM-DD",
      "batch": "Client Q&A — Answers A1-A10",
      "items": [
        {
          "trigger": "A1 — [Question Topic]",
          "clientAnswer": "[Exact client response — serves as evidence]",
          "changeType": "confirmed | added | modified | removed",
          "description": "[What changed in the estimation]",
          "estimationItems": ["#N Task name (X hrs)"],
          "hoursAdded": 0,
          "hoursRemoved": 0,
          "netImpact": 0,
          "module": "[Module name from estimation]"
        }
      ],
      "summary": {
        "totalAdded": 0,
        "totalRemoved": 0,
        "netImpact": 0,
        "mvpBefore": 0,
        "mvpAfter": 0,
        "fullScopeBefore": 0,
        "fullScopeAfter": 0,
        "note": "[Summary of batch impact]"
      }
    }
  ]
}
```

### Step 5: Generate Documents

Run the generator to produce Word and PDF:

```bash
node docs/gen-scope-changes.js SC_001
```

Convert to PDF:
```bash
libreoffice --headless --convert-to pdf docs/SC_001/scope-changes.docx --outdir docs/SC_001/
```

### Step 6: Update Project State

Update `CLAUDE.md` or `contexts/empa-project.md` with new totals:
- Current MVP hours
- Current full scope hours
- Number of scope change batches processed

## Folder Structure

```
docs/
├── gen-scope-changes.js     <- Shared generator (Node.js)
├── SC_001/
│   ├── scope-changes.json   <- Data for batch 1
│   ├── scope-changes.docx   <- Generated Word
│   └── scope-changes.pdf    <- Generated PDF
├── SC_002/                  <- Next batch
│   ├── scope-changes.json
│   ├── scope-changes.docx
│   └── scope-changes.pdf
```

## Verification

- [ ] Every client answer has an entry (even 0-impact confirmations)
- [ ] `clientAnswer` contains the verbatim client response
- [ ] `estimationItems` reference specific line items from `estimation.md`
- [ ] Before/after totals are calculated correctly
- [ ] `estimation.md` is updated to reflect changes
- [ ] Word/PDF documents are generated
- [ ] Project state is updated with new totals

## Common Mistakes

- Skipping zero-impact confirmations — these prove the assumption was correct, not that nothing happened
- Paraphrasing the client answer — always use exact quotes as evidence
- Updating estimation without logging the scope change — creates untraceable drift
- Forgetting to regenerate the PDF/Word after changes
- Not referencing specific estimation line items — "affects backend" is not traceable, "#14 User CRUD (8 hrs)" is
