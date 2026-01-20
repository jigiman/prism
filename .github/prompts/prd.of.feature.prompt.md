## Uses
- Templates: templates/prd.template
- Checklists: checklists/*
- Instructions: copilot-instructions (all)

# Feature / Change PRD Generation

MODE: ONE OF [NEW_FEATURE | ENHANCEMENT | CHANGE_REQUEST | BUG_FIX]

INPUTS:

- JIRA ticket ID (REQUIRED, e.g., ABC-123)
- JIRA story title, description, and acceptance criteria (if any)
- Additional context from conversation or comments

You are a senior software engineer and product-minded architect.

---

## Pre-Step: Git Branch Creation (MANDATORY)

Before creating any PRD documentation, perform the following steps:

1. Determine the git branch prefix based on MODE:
   - `NEW_FEATURE` → `feature/`
   - `ENHANCEMENT` → `feature/`
   - `CHANGE_REQUEST` → `feature/`
   - `BUG_FIX` → `bug/`

2. Construct the branch name using: `<prefix><JIRA-ID>-<short-kebab-case-name>`
  Example: 
    `feature/ABC-347-star-rating-system`
    `bug/ABC-412-fix-null-pointer`

3. Create and checkout the branch:
- If the branch already exists, checkout the existing branch
- Otherwise, create and checkout the new branch

4. ONLY AFTER the correct branch is checked out:
- Proceed with generating the PRD documentation
- Create files in the specified `specs/` directory

Rules:
- Do NOT generate PRD documentation on `main`, `master`, or `develop`
- Do NOT invent or modify the JIRA ticket ID
- Do NOT proceed if branch creation or checkout fails


## Output Location (STRICT)

- The `NNN` value MUST be derived from the numeric portion of the JIRA ticket ID
  - Example: ABC-347 → `347`
- If no JIRA ticket ID is provided, STOP and request it
- ALL generated documentation MUST be written under: `specs/<XXX-NNN-short-feature-name>/`
  Example: `specs/ABC-347-star-rating-system/` where ABC is the prefix before number
- Use **kebab-case** for the feature or change name
- Exactly ONE feature/change directory must be used
- Do NOT write files directly under `specs/`
- Do NOT create files outside the feature/change directory

---  


Task:
Create a lightweight PRD / design brief appropriate to the selected MODE
before any code is written.

General Goals:

- Clarify intent
- Surface assumptions early
- Define scope boundaries
- Reduce rework during implementation and review

Additional Responsibility:

- Identify missing or implicit requirements in the JIRA story
- Make assumptions explicit rather than guessing silently
- Highlight unclear areas as questions instead of filling them creatively

REQUIREMENT:
Clearly label all inferred requirements.
Do NOT present inferred behavior as confirmed.

MODE-SPECIFIC GUIDANCE:

- NEW_FEATURE:

  - Define the problem space clearly
  - Expect incomplete information
  - Emphasize goals, non-goals, and user scenarios

- ENHANCEMENT / CHANGE_REQUEST:

  - Preserve existing behavior unless stated otherwise
  - Call out backward compatibility explicitly
  - Highlight what changes vs what stays the same

- BUG_FIX:
  - Focus on current vs expected behavior
  - Identify minimal correction needed
  - Emphasize regression risk and detection

Rules:

- Ask clarifying questions only if absolutely necessary
- Prefer explicit decisions over vague options
- Optimize for engineering clarity, not marketing language
- Do NOT write code

## JIRA Coverage & Gaps

- What was explicitly stated in the JIRA story
- What was inferred
- What is missing or unclear

Notes:

- Mark any Open Questions that require TPO confirmation explicitly.
- Keep the document lightweight
- Sections may be brief for BUG_FIX or small changes
- This PRD will guide implementation and Ralph review


## REQUIRED ARTIFACTS
- Use appropriate template from /templates
- Validate output using relevant checklist
- Follow copilot-instructions rules
