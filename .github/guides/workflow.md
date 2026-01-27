# AI Agent & CI Workflow (Authoritative)

> ⚠️ This document defines mandatory rules for AI agents and CI pipelines.
> Humans should not treat this as a how-to guide.

---

## Default Behavior

- Do NOT implement by default
- Do NOT create or modify files unless explicitly instructed
- Assume discovery or design mode unless stated otherwise

---

## Implementation Gate

Implementation is allowed ONLY when the user explicitly requests it using terms such as:

- implement
- write the code
- generate code
- apply changes

If not explicitly requested, STOP before implementation.

---

## File Creation Rules

- File creation is opt-in, never implicit
- Only one file may be created per documentation prompt
- Output paths must match allowed mappings
- Non-generating prompts MUST NOT create files

When in doubt, create no files.

---

## Prompt Execution Order

1. Discovery / clarification
2. Design / planning
3. Validation / review
4. Implementation (explicit approval only)
5. Final checks

Skipping steps is not allowed unless explicitly instructed.

---

## CI Expectations

CI may fail if:

- Unauthorized files are created
- Multiple files are generated
- Output paths do not match expectations
- Non-generating prompts produce files

Compliance with this workflow is mandatory.
