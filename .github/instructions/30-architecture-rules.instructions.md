# Architecture & Code Rules

All code must follow established architecture and standards.

General rules:

- Respect existing layering and boundaries
- Avoid unnecessary abstraction or refactoring
- Prefer explicit, readable code over clever solutions
- Minimize blast radius of changes

AI must:

- Follow existing patterns unless explicitly told otherwise
- Avoid introducing new dependencies without justification
- Flag architectural violations instead of silently fixing them

If a request would violate architecture:

- Call it out explicitly
- Do NOT proceed silently
