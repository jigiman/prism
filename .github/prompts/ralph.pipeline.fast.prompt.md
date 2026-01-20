DEPRECATED — use ralph.auto.pipeline

# Run Ralph Pipeline — FAST MODE

MODE: PIPELINE (FAST)

This is a fast, repeatable review-and-fix loop.
It is optimized for **pre-commit checks** and **small-to-medium changes**.

The goal is to catch material defects quickly and block unsafe commits.

NOTE:
This mode may miss edge cases.
Do not use for high-risk or production-critical changes.

====================================================
GLOBAL RULES
====================================================

- Review ONLY the staged or changed code
- Assume the first version is flawed
- Prefer false positives over false negatives
- Do NOT skip review after fixes
- Do NOT chase perfection

====================================================
PHASE 1 — RALPH REVIEWER
====================================================
You are reviewing this code in **Ralph Mode**.

Rules:

- Restate behavior in plain English
- Make hidden assumptions explicit
- Identify ambiguous behavior
- Identify silent or non-obvious failure modes
- Identify violations of best practices
- Identify security, data, or reliability risks

Do NOT suggest fixes yet.

Output:

## Issues Found

For each issue:

- Issue
- Severity: Blocker | High | Medium | Low
- Why it matters

If no issues are found, explicitly say:
“No issues found.”

====================================================
PHASE 2 — FAILURE HUNTER
====================================================
You are trying to break the code.

Rules:

- Assume careless or incorrect usage
- Focus on realistic production failures
- Look for partial, silent, or delayed failures
- Consider observability gaps

Output:

## Failure Scenarios

====================================================
PHASE 3 — FIXER
====================================================
Fix all **Blocker** and **High** severity issues.

Rules:

- Do NOT introduce new features
- Do NOT refactor unless required
- Keep changes minimal and explicit
- Preserve public contracts unless unsafe

Output:

## Updated Code

## Issue → Fix Mapping

====================================================
PHASE 4 — RE-REVIEW (MANDATORY)
====================================================
Re-run **Ralph Reviewer** and **Failure Hunter**
on the UPDATED code.

If new Blocker or High issues are found:

- Return to PHASE 3
- Repeat until convergence

====================================================
CONVERGENCE RULE
====================================================

Converge when:

- No Blocker issues remain
- No High severity issues remain

Medium and Low issues may remain but MUST be listed.

====================================================
FINAL RALPH GATE
====================================================

Output:

## Final Issue Summary

## Gate Result: PASS | BLOCK

## Rationale

Explicitly answer:
“Is this safe to commit?”
