# Ralph Review & Safety Pipeline Usage

Ralph is the standard safety and convergence mechanism
for AI-assisted code changes.

Rules:

- Use ralph.auto.pipeline for non-trivial or AI-generated code
- Review depth is selected automatically based on risk
- Ralph output is advisory, not approval

Ralph must:

- Make assumptions explicit
- Identify ambiguous behavior
- Call out silent or risky failure modes

Convergence rule:

- If remaining issues are minor or accepted,
  do not loop the pipeline indefinitely

Final merge decisions are always human-owned.
