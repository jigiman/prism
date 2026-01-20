DEPRECATED — use ralph.auto.pipeline

# Run Ralph Pipeline — DEEP MODE

MODE: PIPELINE (DEEP)

This is a deep diagnostic + convergence pipeline.
It is optimized for **brownfield code**, **PR review**, and **high-risk changes**.

The goal is to understand intent, surface risk,
fix material issues, and converge safely.

NOTE:
This mode is slower and more exhaustive.
Use only when risk justifies depth.

STOP CONDITION:
If remaining issues are minor, hypothetical, or accepted,
DO NOT require further pipeline runs.
Proceed to Final Ralph Gate.

====================================================
GLOBAL RULES
====================================================

- Execute phases in strict order
- Do NOT skip or merge phases
- Do NOT modify code until the Fixer phase
- Clearly separate outputs with headings
- Carry forward findings between phases
- Avoid perfection chasing

====================================================
PHASE 1 — BUILDER (Intent Clarification / Read-Only)
====================================================
You are a senior engineer establishing intent.

Rules:

- Do NOT modify code
- Do NOT propose fixes
- Focus on understanding, not critique

Tasks:

- Restate what the code is trying to do
- Identify responsibilities of major components
- Describe inputs, outputs, and side effects

Output:

## Intent Summary

## Responsibilities Breakdown

====================================================
PHASE 2 — RALPH REVIEWER
====================================================
You are reviewing this code in **Ralph Mode**.

Rules:

- Assume future readers may misunderstand the code
- Restate behavior in plain English
- Make assumptions explicit
- Identify ambiguities
- Identify silent or risky behavior
- Identify anything that works “by accident”

Do NOT suggest fixes yet.

Output:

## Plain-English Explanation

## Assumptions

## Ambiguities

## Risky or Silent Failures

====================================================
PHASE 3 — FAILURE HUNTER
====================================================
You are attempting to break the code.

Rules:

- Assume hostile, careless, or incorrect usage
- Prefer realistic production failures
- Focus on undetected or poorly observed failures

Tasks:

- Identify edge cases
- Identify invalid or unexpected inputs
- Identify misuse scenarios
- Identify observability gaps

Output:

## Edge Cases

## Invalid or Unexpected Inputs

## Misuse Scenarios

## Undetected Failures

====================================================
PHASE 4 — FIXER
====================================================
Fix all **material issues** identified above.

Rules:

- Address every Blocker and High issue
- Prefer small, readable changes
- Avoid refactors unless strictly necessary
- Do NOT change public contracts unless required
- Add comments only where intent is non-obvious

Output:

## Updated Code

## Change Log (Issue → Fix Mapping)

====================================================
PHASE 5 — RALPH RE-REVIEW (MANDATORY LOOP)
====================================================
Re-run **PHASE 2 and PHASE 3**
on the UPDATED code only.

If new Blocker or High issues are found:

- Return to PHASE 4
- Repeat PHASE 4 → PHASE 5

This loop is EXPECTED.
Fixes often introduce new risks.

====================================================
CONVERGENCE RULE
====================================================

Converge when:

- No Blocker issues remain
- No High severity issues remain

If remaining issues are:

- Minor
- Repetitive
- Low-likelihood
- Mitigated by process or monitoring

Then:

- Explicitly document them
- Mark them as accepted or deferred
- Do NOT require further loops

====================================================
FINAL RALPH GATE
====================================================

Output:

## Remaining Known Issues

## Accepted or Deferred Risks (with rationale)

## Overall Risk Assessment

## Merge Recommendation

Explicitly answer:
“Is this code safe to merge given its context and constraints?”
