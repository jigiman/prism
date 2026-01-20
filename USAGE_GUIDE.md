# Usage Guide — End-to-End AI-Assisted Workflow

This guide describes the **canonical SDLC flow** using AI agents and prompts.

---

## Step 1 — PRD Creation

Owner: TPO or Developer (with TPO confirmation)

Prompts:
- user-story-analyzer
- prd.of.feature

Outcome:
- PRD created using the standard PRD template

---
## Step 2 — PRD Lint (Quality Gate)

Owner: TPO or Developer

Prompt:
- prd.lint

Purpose:
- Validate PRD structure, clarity, and testability
- Catch missing sections and ambiguous requirements early

Rules:
- If result is FAIL → PRD must be updated
- If result is CONDITIONAL → issues must be reviewed and accepted
- If result is PASS → proceed to QA PRD review


## Step 3 — QA PRD Review (Pre-Implementation)

Owner: QA

Prompt:
- qa.prd.review

Outcome:
- Testable, unambiguous PRD
- Gaps resolved before coding begins


---

## Step 4 — Implementation

Owner: Developer

Prompt:
- prd.to.implementation

Rules:
- Implement strictly from PRD
- Stop if information is missing
- Avoid scope expansion

---

## Step 5 — Ralph Context Review

Owner: Developer

Prompts:
- ralph.greenfield (new code)
- ralph.brownfield (existing code)

Outcome:
- Clear explanation of behavior
- Surfaced assumptions and risks

---

## Step 6 — Ralph Auto Pipeline

Owner: Developer

Prompt:
- ralph.auto.pipeline

What it does:
- Assesses risk automatically
- Adjusts review depth (fast/deep internally)
- Fixes material issues
- Applies convergence rules

Outcome:
- Known risks
- Merge recommendation (advisory)

---

## Step 7 — QA Validation (Post-Implementation)

Owner: QA

Prompts:
- qa.test.scenarios
- qa.exploratory.testing
- qa.regression.gate

Outcome:
- Behavior validated against PRD
- Regression risk assessed

---

## Step 8 — PR Review

Owner: PR Reviewer

Prompts:
- ralph.final-gate
- pr-description-from-changes

Outcome:
- Independent technical review
- Explicit concerns or acceptance of risk

---

## Step 9 — Human Merge Decision

Owner: Human Reviewer

Rules:
- AI does not approve PRs
- Risks must be explicitly accepted
- Accountability remains human-owned

---

## Common Rules

- If it is not in the PRD, it is not a requirement
- AI recommendations are advisory
- Role boundaries must be respected
- Do not loop Ralph indefinitely for minor issues
