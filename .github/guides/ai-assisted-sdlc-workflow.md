# AI-Assisted SDLC Workflow (Team Guide)

This document defines how we use AI responsibly across the full software
development lifecycle (SDLC).

The goal is to:

- Move faster **without sacrificing correctness**
- Reduce ambiguity early
- Make AI output explainable and reviewable
- Clearly separate responsibilities between Product, Dev, and QA

> **Key principle:**  
> AI accelerates work, but **human judgment remains the final gate**.

---

## Overview: The 6-Step Workflow

1. PRD / Design Brief
2. Implementation
3. Ralph Context Review (Greenfield / Brownfield)
4. Ralph Pipeline (Safety & Convergence)
5. QA AI Validation
6. QA Regression Gate & Release Decision

Each step answers a different question and has a clear owner.

---

## STEP 1 — PRD / Design Brief (Intent)

**Owner:** TPO + Developer (with AI)  
**Prompt:** `feature.prd.prompt.md`

### Purpose

- Capture intent clearly
- Enrich incomplete JIRA stories
- Surface assumptions and gaps early
- Prevent scope creep

### Inputs

- JIRA story (title, description, acceptance criteria)
- Comments, links, or context (if any)

### Output

A lightweight PRD containing:

- Summary
- Current vs desired behavior
- Goals and non-goals
- Functional and non-functional requirements
- Assumptions and constraints
- Failure modes and edge cases
- Open questions
- **JIRA coverage & gaps**

### Gate

- PRD reviewed and agreed (lightweight)
- Open questions identified before coding starts

---

## STEP 2 — Implementation (Execution)

**Owner:** Developer (with AI)  
**Prompt:** `prd.to.implementation.prompt.md`  
(or a simple implementation prompt for small work)

### Purpose

- Translate PRD → code
- Implement exactly what was agreed
- Avoid inventing requirements

### Rules

- PRD is the source of truth
- No creative expansion
- Keep code readable and reviewable

### Output

- Code changes
- Explicit assumptions (if PRD was ambiguous)

---

## STEP 3 — Ralph Context Review (Self-Review)

**Owner:** Developer  
**Prompts:**

- `ralph.greenfield` → new feature
- `ralph.brownfield` → existing code / enhancement / bug fix

### Purpose

- Make AI explain what it did
- Clarify behavior and constraints
- Reduce noise before formal review

### Output

- Explained behavior
- Identified constraints
- Known risks

> This is **self-review**, not a gate.

---

## STEP 4 — Ralph Pipeline (Safety & Convergence)

**Owner:** Developer / Reviewer  
**Prompt:** `ralph.pipeline.prompt.md`

### Purpose

- Surface hidden assumptions
- Identify silent failures
- Fix material risks
- Converge safely (not chase perfection)

### What Happens

1. Builder — intent clarification
2. Ralph Reviewer — assumptions, ambiguity, silent failures
3. Failure Hunter — edge cases, misuse, observability gaps
4. Fixer — targeted repairs
5. Convergence Rule — stop infinite loops
6. Final Ralph Gate — merge recommendation

### Output

- Updated code (if needed)
- Known and accepted risks
- Explicit merge recommendation

---

## STEP 5 — QA AI Validation (Independent)

**Owner:** QA Engineer  
**Prompts used as needed:**

- `qa.prd.review`
- `qa.test.scenarios`
- `qa.exploratory.testing`
- `qa.automation.candidates`
- `qa.bug.triage`

### Purpose

- Validate user-visible behavior
- Identify gaps Ralph may miss
- Design manual and automated tests

### Output

- Test scenarios
- Bugs or risks
- Automation recommendations

> QA does **not** rely solely on Ralph, but may use its output as input.

---

## STEP 6 — QA Regression Gate & Release Decision

**Owner:** QA (with Dev input)  
**Prompt:** `qa.regression.gate.prompt.md`

### Purpose

- Final readiness decision
- Ensure coverage matches PRD
- Make residual risk explicit

### Output

- Tested vs untested areas
- Regression risk assessment
- Final QA recommendation:
  - ✅ Pass
  - ⚠️ Conditional
  - ❌ Block

---

## Recommended Flows by Work Type

### New Feature

PRD → Implementation → ralph.greenfield → ralph.pipeline → QA → QA Gate

### Enhancement / Change Request

PRD → Implementation → ralph.brownfield → ralph.pipeline → QA → QA Gate

### Bug Fix

PRD (BUG_FIX) → Fix → ralph.brownfield → ralph.pipeline → QA → QA Gate

---

## What Each Role Owns

| Role      | Primary Responsibility          |
| --------- | ------------------------------- |
| TPO       | Business intent, priorities     |
| Developer | Correct implementation          |
| Ralph     | Code safety and convergence     |
| QA        | User impact and regression risk |

---

## Non-Negotiable Rules

- AI-written code **must** go through Ralph Pipeline
- PRD is the source of truth for intent
- Zero issues is **not** the goal — informed decisions are
- Human judgment is the final gate

---

## Key Mindset to Remember

> **AI helps us think wider and faster —  
> but we stay accountable for what ships.**
