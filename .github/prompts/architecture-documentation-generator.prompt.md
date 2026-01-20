## Uses
- Templates: templates/*
- Checklists: checklists/*
- Instructions: copilot-instructions (all)

# Architecture Documentation Generator Prompt

> **Estimated Time:** 5–15 minutes depending on project size  
> **Output:** 6–8 architecture documentation files  
> **Supports:** Any technology stack (auto-detected)

---

## Output Location (STRICT)

- ALL generated documentation MUST be written **only** under: `docs/architecture/`
- `{docs_path}` MUST always resolve to `docs/architecture`
- If the directory does not exist, assume it should be created
- Do NOT write files to:
    - `docs/`
    - `doc/`
    - `documentation/`
    - any other directory
- Ignore any non-architecture documentation locations found in the repo

---

## Objective

Analyze the project workspace and generate **minimal, accurate architecture documentation** based strictly on **actual code found** — never theoretical patterns.

---

## Core Principles

These principles apply to ALL tasks and MUST be followed consistently:

1. **Real over Theory** – Extract only from existing code and configuration
2. **Detect, Don’t Assume** – Auto-detect technologies, patterns, and structure
3. **Minimal but Complete** – Essential information only, no fluff
4. **Single Source of Truth** – No duplicated information across files
5. **Correct Naming** – Replace `{PROJECT_NAME}` using `.sln`, `package.json`, or root directory

---

## Formatting Rules (GLOBAL)

Apply to **every generated file**:

- Use **Markdown** (`.md`)
- One logical document per file
- One `#` H1 heading per file
- Prefer tables over long prose
- Diagrams allowed only if they reflect real structure
- No emojis
- No marketing language
- No placeholders (`TODO`, `TBD`, `{example}`)
- No speculative or “recommended” architectures

---

## Pre-Execution Options

### Mode Selection

| Mode              | Description                                 |
| ----------------- | ------------------------------------------- |
| `--full`          | Generate all documentation (default)        |
| `--dry-run`       | Preview files without writing               |
| `--update`        | Update existing docs, preserve manual edits |
| `--backend-only`  | Generate backend docs only                  |
| `--frontend-only` | Generate frontend docs only                 |

---

## Task 0: Discovery & Setup

### 0.1 Detect Project Configuration

1. Project Name (from real config files)
2. Documentation path → **force `docs/architecture/`**
3. Existing architecture docs (to avoid duplication)
4. Output format → Markdown

---

## Task 1: Backend Architecture

**Skip if no backend detected**

Create: `docs/architecture/backend_architecture.md`

Include:
- Overview (2–3 sentences)
- Technology stack (actual versions)
- Architecture pattern detected
- Directory structure (max 2 levels)
- Layer responsibilities
- Dependency flow (Mermaid allowed)
- Database details (if present)
- API design (auth, versioning, style)
- Configuration approach

---

## Task 2: Frontend Architecture

**Skip if no frontend detected**

Create: `docs/architecture/frontend_architecture.md`

Include:
- Overview
- Technology stack
- Architecture pattern
- Source structure
- State management
- Routing
- Styling
- API integration

---

## Task 3: Tech Stack Reference

Create: `docs/architecture/tech_stack.md`

Include:
- Backend dependencies (if any)
- Frontend dependencies (if any)
- Infrastructure tools (Docker, K8s, etc.)
- Development tooling (linters, formatters)

---

## Task 4: Coding Standards

Create: `docs/architecture/coding_standards.md`

Include:
- Naming conventions
- Code organization patterns
- Formatting rules (from configs)
- Git conventions (only if detected)
- API conventions
- Code review checklist (derived)

---

## Task 5: Testing Standards

Create: `docs/architecture/testing_standards.md`

Include:
- Test frameworks
- Test structure
- Commands to run tests
- Coverage configuration (if any)
- Real test examples (short, extracted)

---

## Task 6: Code Examples

Create: `docs/architecture/code_examples.md`

Include:
- Backend patterns (controllers, services, etc.)
- Frontend patterns (components, hooks, etc.)
- Integration flow (sequence diagram allowed)
- Use **real code only**, short excerpts

---

## Task 7: Architecture Index

Create: `docs/architecture/README.md`

Include:
- Overview
- Links to all generated documents
- High-level architecture diagram
- Key architectural decisions inferred from code

---

## Constraints (STRICT)

- Do NOT generate:
  - PRDs
  - Feature specs
  - Governance documentation
  - Pipeline documentation
- Do NOT modify source code
- Do NOT invent technologies or patterns
- Do NOT duplicate content across files
- Do NOT write files outside `docs/architecture/`

---

## Final Check (MANDATORY)

Before completing, verify:

- [ ] Every file path starts with `docs/architecture/`
- [ ] No files created elsewhere
- [ ] No theoretical or assumed content
- [ ] No placeholders remain
- [ ] Diagrams reflect real structure
- [ ] Links between docs resolve correctly
- [ ] Project name correctly detected
- [ ] Only detected technologies documented

If **any check fails**, fix it before returning output.

---

## Maintenance Notes

Regenerate documentation when:
- Architecture changes
- Major dependencies change
- New frontend/backend added
- Quarterly review

To preserve manual edits:
- Respect `<!-- MANUAL_START -->` / `<!-- MANUAL_END -->` blocks in `--update` mode









