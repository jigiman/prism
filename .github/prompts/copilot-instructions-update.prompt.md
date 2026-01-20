## Uses
- Templates: templates/*
- Checklists: checklists/*
- Instructions: copilot-instructions (all)

You are updating an existing `copilot-instructions.md` file.

CRITICAL PRESERVATION RULES:

- Do NOT change, rewrite, reformat, summarize, or move ANY content above the heading:
  `## 4. Stack Overview`
- Do NOT change, rewrite, reformat, summarize, or move the following sections in ANY way:

  ## Guiding Rule

  > **If it is not in the PRD, it is not a requirement.**

  ***

  ## Final Note

  AI is a multiplier.  
  Accountability remains human-owned.

  This document defines **how AI is expected to behave**.  
  Prompts define **what AI is asked to do**.

- Preserve all text, headings, spacing, wording, and order of these protected sections exactly as-is.
- Any deviation from the preserved sections is not allowed.

TASK:

- Rewrite ONLY the section starting at:
  `## 4. Stack Overview`
- You may update content up until, but NOT INCLUDING, `## 9. Guiding Rule`.
- Do not add, remove, or reorder sections.

STACK OVERVIEW REQUIREMENTS:
In `## 4. Stack Overview`, include:

- High-level system architecture
- Backend technologies and frameworks
- Frontend technologies (if applicable)
- Database and storage
- Messaging / asynchronous components (if any)
- Infrastructure / hosting / CI/CD
- External integrations and dependencies

STYLE RULES:

- Use clear bullet points and short explanations
- Be factual and explicit
- Prefer clarity over cleverness
- Avoid marketing or promotional language
- Avoid assumptions — if something is unknown, mark it explicitly as “Project-specific” or “To be confirmed”

AI BEHAVIOR RULES:

- Do NOT invent technologies that are not present in the repository or context
- If information is insufficient or ambiguous, ask clarifying questions BEFORE updating the section
- Do NOT modify any other section under any circumstances

OUTPUT RULE:

- Output the FULL updated `copilot-instructions.md` file
- Ensure that:
  - Everything above `## 4. Stack Overview` is byte-for-byte identical
  - Sections `## 9. Guiding Rule` and `## 10. Final Note` are byte-for-byte identical


## REQUIRED ARTIFACTS
- Use appropriate template from /templates
- Validate output using relevant checklist
- Follow copilot-instructions rules
