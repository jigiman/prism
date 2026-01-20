## Uses
- Templates: templates/*
- Checklists: checklists/*
- Instructions: copilot-instructions (all)

# Generate Git Commit Message from Staged Changes

You are acting as a senior software engineer preparing a high-quality Git commit.

## Task

- Inspect **ONLY** the currently staged git changes.
- Do **NOT** infer or include unstaged or untracked changes.
- Generate a **single**, well-structured git commit message.

## CRITICAL OUTPUT INSTRUCTIONS

- Output ONLY the commit message
- Do NOT add explanations, commentary, or prefaces
- Wrap the entire commit message inside a single fenced code block
- The result must be immediately copy-pasteable into git commit -m or a commit editor

## Output Format (follow exactly)

<type>(<scope>): <concise summary>

WHAT CHANGED

- Bullet list of concrete code changes (files, behavior, APIs, configs)

WHY

- Explain the motivation or problem being solved
- If refactoring, explain what was improved and why

AUTHORSHIP

- Changed by: [AI | Human | AI-assisted]
- AI contribution: <percentage estimate>%
- Human contribution: <percentage estimate>%
- Basis for estimate: brief explanation (e.g., logic design vs implementation vs edits)

NOTE FOR PR REVIEWER

- What reviewers should pay attention to
- Any risks, assumptions, or non-obvious decisions
- Suggested areas for extra scrutiny or testing

## Rules

- Be factual; do not exaggerate AI contribution
- If the user mainly guided logic and decisions, reflect that
- Prefer clarity over clever wording
- Do not include markdown beyond bullets and headings
- Do not mention unstaged changes


## REQUIRED ARTIFACTS
- Use appropriate template from /templates
- Validate output using relevant checklist
- Follow copilot-instructions rules
