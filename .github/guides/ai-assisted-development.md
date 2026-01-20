# AI-Assisted Development Guide (Ralph Pipeline)

This document explains how developers must use the Ralph pipeline for
AI-assisted and human-only development.

**Ralph is mandatory for ALL changes.**

---

## 1. Core Principles

- AI is a tool, not an authority
- All changes must be reviewed
- Humans remain fully accountable
- Trust is earned through verification

> If it’s not reviewed by Ralph, it doesn’t ship.

---

## 2. Main Entry Point: `ralph.auto.pipeline.prompt.md`

### What it does

This is the **default and recommended prompt**.

When run in Copilot Chat, it:

1. Analyzes the current changes
2. Selects FAST or DEEP mode automatically
3. Runs the selected pipeline
4. Enforces convergence
5. Produces a final **Ralph Gate** result (PASS / BLOCK)

Developers must NOT choose the mode manually.

---

### When to use it

- Before every commit
- Before opening or updating a PR
- Whenever unsure which mode to use

---

### How to use it

1. Open Copilot Chat
2. Paste `ralph.auto.pipeline.prompt.md`
3. Fix issues if Gate = BLOCK
4. Re-run until Gate = PASS

---

## 3. Pipeline Modes

### FAST Mode

**Purpose:**  
Quick defect detection for low-risk changes.

**Allowed only when ALL are true:**

- Low-risk change
- No auth, security, billing, quota, data, infra, or schema changes
- No new public APIs
- No significant logic changes
- Code area is well-understood

**Typical usage:**

- Pre-commit checks
- Small refactors
- Tests, comments, formatting
- Obvious bug fixes

**Behavior:**

- Reviews staged changes only
- Fixes Blocker and High issues
- Mandatory re-review
- Fast convergence

---

### DEEP Mode

**Purpose:**  
Safe convergence for complex or risky changes.

**Required when ANY are true:**

- Brownfield or legacy code
- Medium or High risk
- Business logic changes
- Auth, security, billing, data, infra, migrations
- Unfamiliar code
- FAST mode fails to converge

**Behavior:**

- Clarifies intent before critique
- Surfaces assumptions and ambiguities
- Hunts realistic failure scenarios
- Fixes material issues
- Mandatory re-review loop
- Ends with a merge recommendation

---

## 4. Escalation Rule

FAST mode MUST escalate to DEEP if:

- It fails to converge after 2 iterations
- Intent is unclear
- Repeated or systemic issues appear

> FAST is a privilege.  
> DEEP is the default.

---

## 5. Ralph Gate (Final Authority)

Every pipeline ends with a Ralph Gate:

- **PASS** → change may proceed
- **BLOCK** → change must not proceed

### Gate blocks if:

- Any Blocker or High issues remain
- Security, privacy, or data integrity risks exist
- Requirements are incomplete
- Risks are undocumented

There are no exceptions.

---

## 6. PR Documentation: `ralph.pr.template.prompt.md`

### What it does

Generates a **copy-ready PR section** containing:

- Selected pipeline mode
- Selection rationale
- Ralph Gate result
- Remaining risks
- AI attribution
- PR checklist

---

### When to use it

- After Ralph Gate = PASS
- Before submitting or updating a PR

---

### How to use it

1. Open Copilot Chat
2. Paste `ralph.pr.template.prompt.md`
3. Copy the output
4. Paste it into the PR description

---

## 7. PR Checklist (Mandatory)

Every PR must include the following checklist:

- Ralph Pipeline was executed (AUTO / FAST / DEEP)
- Ralph Pipeline Summary (Selector + Gate output) is included
- Ralph Gate result is **PASS**
- Remaining Medium / Low risks are documented or marked “None”
- Risk level is correctly classified

Reviewers must not approve PRs missing this section.

---

## 8. AI Attribution (Always Required)

Every commit and PR must disclose:

- Changed by: AI | Human | AI-assisted
- Approximate contribution percentages
- Basis for estimate

This applies even if no AI was used.

---

## 9. Human Accountability

AI assistance does not transfer responsibility.

The author of the change is fully accountable for:

- Correctness
- Safety
- Compliance
- Production impact

> “The AI did it” is not an acceptable explanation.

---

## 10. What Ralph Does NOT Replace

Ralph does not replace:

- Human judgment
- Code reviews
- Testing
- Architecture decisions

Ralph supports humans; it does not replace them.

---

## 11. If Something Feels Wrong

If you:

- Disagree with a pipeline decision
- Experience non-convergence
- Feel blocked by Ralph

Then:

1. Stop
2. Escalate to human review
3. Document the concern

Do not bypass the system.

---

## 12. One Rule to Remember

> If it’s not reviewed by Ralph, it doesn’t ship.
