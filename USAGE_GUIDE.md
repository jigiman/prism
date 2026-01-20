# Usage Guide — End-to-End AI-Assisted Workflow

This guide describes the **canonical SDLC flow** using AI agents and prompts.

---

## Step 1 — PRD Creation

Owner: TPO (or Dev with TPO confirmation)

Prompts:
- user-story-analyzer
- prd.of.feature

Outcome:
- Clear goals, non-goals, acceptance criteria
- Explicit assumptions and constraints

---

## Step 2 — QA PRD Review (Pre-Implementation)

Owner: QA

Prompt:
- qa.prd.review

Outcome:
- Testable requirements
- Identified gaps and ambiguity
- PRD updated before coding starts

---

## Step 3 — Implementation

Owner: Developer

Prompt:
- prd.to.implementation

Rules:
- Implement strictly from PRD
- Stop if information is missing
- Avoid scope expansion

---

## Step 4 — Ralph Context Review

Owner: Developer

Prompts:
- ralph.greenfield (new code)
- ralph.brownfield (existing code)

Outcome:
- Clear explanation of behavior
- Surfaced assumptions and risks

---

## Step 5 — Ralph Auto Pipeline

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

## Step 6 — QA Validation (Post-Implementation)

Owner: QA

Prompts:
- qa.test.scenarios
- qa.exploratory.testing
- qa.regression.gate

Outcome:
- Behavior validated against PRD
- Regression risk assessed

---

## Step 7 — PR Review

Owner: PR Reviewer

Prompts:
- ralph.final-gate
- pr-description-from-changes

Outcome:
- Independent technical review
- Explicit concerns or acceptance of risk

---

## Step 8 — Human Merge Decision

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
