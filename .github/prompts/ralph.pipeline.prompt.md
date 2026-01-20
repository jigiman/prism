## Uses
- Template: templates/ralph.review.output.template.md
- Checklist: checklists/pr-review-checklist.md
- Instructions: copilot-instructions (all)

DEPRECATED — use ralph.auto.pipeline

# Run Ralph Pipeline

MODE: PIPELINE

This is a review-and-repair workflow for existing code.
The goal is to surface risk, fix material issues, and converge safely.

GLOBAL RULES:

- Execute phases in strict order
- Do NOT skip or merge phases
- Do NOT modify code until the Fixer phase
- Clearly separate output with headings
- Carry forward findings between phases
- Avoid perfection chasing

STOP CONDITION:
If remaining issues are minor, hypothetical, or accepted,
DO NOT require further pipeline runs.
Proceed to Final Ralph Gate.

====================================================
PHASE 1 — BUILDER (Intent Clarification / Read-Only)
====================================================
You are a senior software engineer establishing intent.

Rules:

- Do NOT modify code
- Do NOT propose fixes
- Focus on understanding, not critique

Tasks:

- Restate what the code is trying to accomplish
- Identify responsibilities of each major function/class/module
- Describe expected inputs, outputs, and side effects

Output:

## Intent Summary

## Responsibilities Breakdown

====================================================
PHASE 2 — RALPH REVIEWER (Ralph Mode)
====================================================
You are reviewing this code in **Ralph Mode**.

Rules:

- Assume the reader may misunderstand the code
- Restate behavior in plain English
- Make hidden assumptions explicit
- Identify ambiguous behavior
- Call out silent or non-obvious failure modes
- Identify anything that works “by accident”

Do NOT suggest fixes yet.

Output:

## Plain-English Explanation

## Assumptions

## Ambiguities

## Silent or Risky Failure Modes

====================================================
PHASE 3 — FAILURE HUNTER (Destructive Tester)
====================================================
You are now trying to break this code.

Rules:

- Assume careless, hostile, or incorrect usage
- Prefer realistic production failures
- Focus on partial, silent, or delayed failures
- Consider observability gaps (logs, metrics, alerts)

Tasks:

- Identify edge cases
- Identify invalid or unexpected inputs
- Identify misuse scenarios
- Identify failures that would not be detected

Output:

## Edge Cases

## Invalid or Unexpected Inputs

## Misuse Scenarios

## Undetected / Poorly Observed Failures

====================================================
PHASE 4 — FIXER (Targeted Repair)
====================================================
You are now fixing the code.

Rules:

- Address every _material_ issue identified above
- Prefer small, explicit, readable changes
- Avoid refactors unless strictly necessary
- Do NOT change public contracts unless explicitly required
- Add comments only where intent is non-obvious

Tasks:

- Update the code
- Explain each change
- Explicitly reference which issue it resolves

Output:

## Updated Code

## Change Log (Issue → Fix Mapping)

====================================================
CONVERGENCE RULE
====================================================
If newly identified issues are:

- Minor or cosmetic
- Repetitive or previously addressed in spirit
- Hypothetical edge cases with low likelihood
- Already mitigated by monitoring, validation, or process

Then:

- Call them out briefly
- Mark them as accepted or deferred
- Do NOT require additional pipeline iterations

The goal is convergence, not perfection.

====================================================
FINAL RALPH GATE
====================================================
Summarize the final state of the code.

Output:

## Remaining Known Issues (if any)

## Accepted or Deferred Risks (with rationale)

## Overall Risk Assessment

## Merge Recommendation

Explicitly answer:
“Is this code safe to merge given its context and constraints?”


## REQUIRED ARTIFACTS
- Use appropriate template from /templates
- Validate output using relevant checklist
- Follow copilot-instructions rules
