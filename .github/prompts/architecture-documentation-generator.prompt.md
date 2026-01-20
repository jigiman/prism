## Uses
- Templates: templates/*
- Checklists: checklists/*
- Instructions: copilot-instructions (all)

# Architecture Generator Prompt

> **Estimated Time:** 5-15 minutes depending on project size  
> **Output:** 6-8 documentation files in detected docs directory  
> **Supports:** Any technology stack (auto-detected)

## Objective

Analyze any project workspace and generate minimal, accurate architecture documentation based on **actual code found** - never theoretical patterns.

## Core Principles

These principles apply to ALL tasks - do not repeat in individual sections:

1. **Real over Theory**: Extract from actual code only, never assume or use placeholders
2. **Detect, Don't Assume**: Auto-detect languages, frameworks, patterns, and conventions
3. **Minimal but Complete**: Essential information only, no verbose explanations
4. **Single Source of Truth**: No duplicate information across files
5. **Project Name**: Use `{PROJECT_NAME}` placeholder - replace with detected name from `.sln`, `package.json`, or root directory

---

## Pre-Execution Options

### Mode Selection

| Mode              | Description                                 |
| ----------------- | ------------------------------------------- |
| `--full`          | Generate all documentation (default)        |
| `--dry-run`       | Preview files to be created without writing |
| `--update`        | Update existing docs, preserve manual edits |
| `--backend-only`  | Generate backend documentation only         |
| `--frontend-only` | Generate frontend documentation only        |

**How to Use:**

When invoking this prompt (via GitHub Copilot, AI assistant, or automation script), specify the mode in your request:

**Examples:**

1. **Full generation (default):**

   ```
   "Generate architecture documentation for this project"
   "Use architecture_generator.prompt.md to create docs"
   ```

2. **Preview before creating files:**

   ```
   "Run architecture generator in --dry-run mode"
   "Preview what docs would be generated without writing files"
   ```

3. **Update existing docs:**

   ```
   "Update architecture docs using --update mode"
   "Regenerate docs but preserve my manual edits"
   ```

4. **Backend only:**

   ```
   "Generate backend architecture docs only (--backend-only)"
   "Document the backend using architecture_generator.prompt.md"
   ```

5. **Frontend only:**
   ```
   "Generate frontend architecture docs only (--frontend-only)"
   ```

### Output Format

Detect from existing project docs, or default to Markdown:

- `.md` - Markdown (default)
- `.adoc` - AsciiDoc (if found in project)
- `.rst` - reStructuredText (if found in project)

---

## Task 0: Discovery & Setup

**Run this first before any documentation generation.**

### 0.1 Detect Project Configuration

```
1. Project Name: Extract from .sln, package.json, Cargo.toml, go.mod, or root directory
2. Documentation Location: Check for existing docs/ doc/ documentation/ or create docs/architecture/
3. Existing Docs: List current documentation to avoid overwriting manual content
4. Output Format: Detect .md/.adoc/.rst from existing docs
```

### 0.2 Detect Technology Stack

| Check For                               | Technology | Backend/Frontend |
| --------------------------------------- | ---------- | ---------------- |
| `*.sln`, `*.csproj`                     | .NET/C#    | Backend          |
| `package.json` + `express/fastify/nest` | Node.js    | Backend          |
| `requirements.txt`, `pyproject.toml`    | Python     | Backend          |
| `pom.xml`, `build.gradle`               | Java       | Backend          |
| `go.mod`                                | Go         | Backend          |
| `Cargo.toml`                            | Rust       | Backend          |
| `package.json` + `react`                | React      | Frontend         |
| `package.json` + `vue`                  | Vue        | Frontend         |
| `angular.json`                          | Angular    | Frontend         |
| `package.json` + `svelte`               | Svelte     | Frontend         |

### 0.3 Detect Architecture Pattern

| Pattern            | Indicators                                                |
| ------------------ | --------------------------------------------------------- |
| Clean Architecture | Layers: Api/Application/Domain/Infrastructure             |
| DDD                | Aggregates, ValueObjects, DomainEvents folders            |
| MVC                | Controllers, Models, Views folders                        |
| Microservices      | Multiple service directories, docker-compose, API gateway |
| Feature-Based      | `features/` or `modules/` directory structure             |
| Layered            | Clear separation: presentation/business/data              |

### 0.4 Detect Existing Conventions

Check for and extract from:

- `CONTRIBUTING.md` - Git/code conventions
- `.gitmessage` - Commit message format
- `.editorconfig` - Code style
- `eslint/prettier/stylecop` configs - Linting rules
- Existing `README.md` - Project description

### 0.5 Set Generation Order

```
If both frontend and backend exist:
  1. Backend first (provides API contract context)
  2. Frontend second (references backend APIs)
  3. Integration examples last
```

---

## Task 1: Generate Backend Architecture

**Skip if no backend detected.**

Create: `{docs_path}/backend_architecture.md`

````markdown
# Backend Architecture - {PROJECT_NAME}

## Overview

[2-3 sentences describing the backend, extracted from README or inferred from structure]

## Technology Stack

| Category | Technology | Version |
| -------- | ---------- | ------- |

[Extract from project files - only include what's actually used]

## Architecture

[Detected pattern: Clean/DDD/MVC/Microservices/Layered/Custom]

```
[Actual directory structure - 2 levels deep max]
```

### Layer Responsibilities

[Only document layers that EXIST - adapt naming to project]

| Layer | Purpose | Key Components |
| ----- | ------- | -------------- |

[Extract from actual folder structure]

### Dependencies Flow

```mermaid
graph LR
    [Generate based on actual project references]
```

## Design Patterns Used

[List only patterns FOUND in code with file path examples]

## Database

| Aspect         | Details    |
| -------------- | ---------- |
| Provider       | [Detected] |
| ORM            | [Detected] |
| Migration Tool | [Detected] |

## API Design

| Aspect     | Approach             |
| ---------- | -------------------- |
| Style      | [REST/GraphQL/gRPC]  |
| Versioning | [Detected or "None"] |
| Auth       | [Detected method]    |

## Configuration

- Config files: [List actual files]
- Secrets: [Approach detected]
- Environments: [List detected environments]
````

---

## Task 2: Generate Frontend Architecture

**Skip if no frontend detected.**

Create: `{docs_path}/frontend_architecture.md`

````markdown
# Frontend Architecture - {PROJECT_NAME}

## Overview

[2-3 sentences from README or inferred]

## Technology Stack

| Category | Technology | Version |
| -------- | ---------- | ------- |

[Extract from package.json - only what's used]

## Architecture

[Detected pattern: Feature-based/Component-based/Atomic/Custom]

```
[Actual src/ structure - 2 levels deep max]
```

## State Management

| Type         | Solution                                           |
| ------------ | -------------------------------------------------- |
| Server State | [Detected: React Query/SWR/Apollo/etc. or "fetch"] |
| Client State | [Detected: Redux/Zustand/Context/Pinia/etc.]       |
| Form State   | [Detected: React Hook Form/Formik/etc.]            |

## Routing

| Aspect         | Details                |
| -------------- | ---------------------- |
| Library        | [Detected]             |
| Auth Routes    | [Pattern detected]     |
| Code Splitting | [Yes/No with approach] |

## Styling

| Aspect      | Approach                             |
| ----------- | ------------------------------------ |
| Framework   | [Tailwind/Bootstrap/Material/etc.]   |
| Methodology | [CSS Modules/Styled Components/etc.] |

## API Integration

- Client: [Axios/Fetch/etc.]
- Base Config: [File path]
- Type Generation: [Yes/No - approach if yes]
````

---

## Task 3: Generate Tech Stack Reference

Create: `{docs_path}/tech_stack.md`

```markdown
# Tech Stack - {PROJECT_NAME}

> Generated: {TIMESTAMP}  
> Source: Extracted from project configuration files

## Backend

[Only if backend exists]

| Technology | Version | Purpose | Config File |
| ---------- | ------- | ------- | ----------- |

[Extract ALL dependencies with purpose - group by category]

## Frontend

[Only if frontend exists]

| Technology | Version | Purpose | Config File |
| ---------- | ------- | ------- | ----------- |

[Extract from package.json - include devDependencies separately]

## Infrastructure

[Only if found in project]

| Tool | Purpose |
| ---- | ------- |

[Docker, K8s, Terraform, etc.]

## Development Tools

| Tool | Purpose | Config |
| ---- | ------- | ------ |

[Linters, formatters, type checkers with config file locations]
```

---

## Task 4: Generate Coding Standards

Create: `{docs_path}/coding_standards.md`

```markdown
# Coding Standards - {PROJECT_NAME}

> Extracted from: [List config files analyzed]

## Detected Conventions

### Naming

[Extract from linter configs and existing code patterns]

| Element | Convention | Example |
| ------- | ---------- | ------- |

[Only for detected language(s)]

### Code Organization

[Infer from actual project structure]

### Formatting

[Extract from prettier/editorconfig/stylecop]

| Rule | Value | Source |
| ---- | ----- | ------ |

[List actual configured rules]

## Git Conventions

[Only if CONTRIBUTING.md or .gitmessage exists, otherwise state "Not configured - team should define"]

## API Conventions

[Extract from actual API implementation]

| Aspect | Convention | Example |
| ------ | ---------- | ------- |

[URL patterns, response formats, error handling]

## Code Review Checklist

- [ ] Follows detected naming conventions
- [ ] Includes tests (if test directory exists)
- [ ] No debug statements
- [ ] Error handling present
      [Add project-specific items based on detected patterns]
```

---

## Task 5: Generate Testing Standards

Create: `{docs_path}/testing_standards.md`

````markdown
# Testing Standards - {PROJECT_NAME}

## Test Infrastructure

| Aspect        | Backend    | Frontend   |
| ------------- | ---------- | ---------- |
| Framework     | [Detected] | [Detected] |
| Runner        | [Detected] | [Detected] |
| Coverage Tool | [Detected] | [Detected] |
| Mocking       | [Detected] | [Detected] |

## Test Organization

```
[Actual test directory structure from project]
```

## Running Tests

### Backend

```bash
[Actual command from package.json/Makefile/scripts]
```

### Frontend

```bash
[Actual command from package.json]
```

## Coverage

[Extract from config if defined, otherwise "Not configured"]

| Metric | Target |
| ------ | ------ |

[Only if coverage thresholds are configured]

## Patterns Found

### Unit Test Example

**File:** `[actual test file path]`

```[language]
[Real test from project - shortest good example]
```

### Integration Test Example

[Only if integration tests exist]
**File:** `[actual test file path]`

```[language]
[Real test from project]
```
````

---

## Task 6: Generate Code Examples

Create: `{docs_path}/code_examples.md`

````markdown
# Code Examples - {PROJECT_NAME}

> Real examples extracted from this codebase

## Backend Patterns

### [Pattern Name - e.g., "Controller"]

**File:** `[path]`

```[lang]
[Actual code - keep under 30 lines, add comments if needed]
```

**Why:** [One sentence explaining the pattern]

[Repeat for 3-5 key patterns found: Controller, Service, Repository, etc.]

## Frontend Patterns

### [Pattern Name - e.g., "Component with Data Fetching"]

**File:** `[path]`

```[lang]
[Actual code - keep under 40 lines]
```

**Why:** [One sentence]

[Repeat for 3-5 key patterns: Component, Hook, API call, Form, etc.]

## Integration Flow

**Scenario:** [Common user action, e.g., "User creates a resource"]

```mermaid
sequenceDiagram
    [Generate from actual code flow]
```

| Step          | File   | Key Code      |
| ------------- | ------ | ------------- |
| 1. UI Action  | [path] | `[one-liner]` |
| 2. API Call   | [path] | `[one-liner]` |
| 3. Controller | [path] | `[one-liner]` |
| 4. Service    | [path] | `[one-liner]` |
| 5. Data       | [path] | `[one-liner]` |
````

---

## Task 7: Generate Index & Update Links

### 7.1 Create Index File

Create: `{docs_path}/README.md`

````markdown
# {PROJECT_NAME} Architecture Documentation

> Last Generated: {TIMESTAMP}  
> Codebase Version: {GIT_COMMIT_SHORT or "N/A"}

## Quick Links

| Document                                            | Description                        |
| --------------------------------------------------- | ---------------------------------- |
| [Backend Architecture](./backend_architecture.md)   | Server-side structure and patterns |
| [Frontend Architecture](./frontend_architecture.md) | Client-side structure and patterns |
| [Tech Stack](./tech_stack.md)                       | Complete dependency reference      |
| [Coding Standards](./coding_standards.md)           | Conventions and guidelines         |
| [Testing Standards](./testing_standards.md)         | Test patterns and commands         |
| [Code Examples](./code_examples.md)                 | Real-world code patterns           |

## Architecture Overview

```mermaid
graph TB
    subgraph Frontend
        [Component names]
    end
    subgraph Backend
        [Layer names]
    end
    Frontend --> Backend
```

## Key Decisions

| Decision | Choice | Rationale |
| -------- | ------ | --------- |

[Extract from ADRs if exist, or infer from stack choices]

---

_This documentation is auto-generated. Manual edits may be overwritten._
_To preserve changes, use `--update` mode or edit source code comments._
````

### 7.2 Update Copilot Instructions

Append to `.github/copilot-instructions.md`:

```markdown
## 📚 Architecture Documentation

| Document                                               | Purpose       |
| ------------------------------------------------------ | ------------- |
| [Architecture Index](docs/architecture/README.md)      | Start here    |
| [Backend](docs/architecture/backend_architecture.md)   | Server-side   |
| [Frontend](docs/architecture/frontend_architecture.md) | Client-side   |
| [Tech Stack](docs/architecture/tech_stack.md)          | Dependencies  |
| [Standards](docs/architecture/coding_standards.md)     | Conventions   |
| [Testing](docs/architecture/testing_standards.md)      | Test patterns |
| [Examples](docs/architecture/code_examples.md)         | Code samples  |

> Auto-generated from codebase. See individual files for details.
```

---

## Task 8: Validation

**Run after all files are generated.**

### 8.1 Link Validation

```
For each generated file:
  - Check all internal links resolve
  - Check all file path references exist
  - Report broken links
```

### 8.2 Content Validation

```
For each generated file:
  - Verify no {PLACEHOLDER} text remains
  - Verify no "TODO" or "[TBD]" markers
  - Verify code examples compile/parse
  - Verify version numbers are actual (not X.X)
```

### 8.3 Generate Validation Report

```markdown
## Generation Report

| File                     | Status | Issues        |
| ------------------------ | ------ | ------------- |
| backend_architecture.md  | ✅     | -             |
| frontend_architecture.md | ⚠️     | 1 broken link |
| ...                      | ...    | ...           |

### Issues Found

1. [Issue description and suggested fix]
```

---

## Error Handling

| Error                    | Action                                                   |
| ------------------------ | -------------------------------------------------------- |
| Cannot read source file  | Log warning, skip section, note in output                |
| Cannot detect technology | Ask user or skip component                               |
| Existing docs found      | In `--update` mode: merge; otherwise: backup and replace |
| No tests found           | Note "No tests detected" in testing_standards.md         |
| Empty project            | Generate minimal skeleton with TODOs                     |

---

## Output Checklist

Before completing, verify:

- [ ] Project name correctly detected and applied
- [ ] Only detected technologies documented (no theoretical examples)
- [ ] All code examples from actual source files with paths
- [ ] No duplicate information across files
- [ ] All links validated and working
- [ ] Index file created with navigation
- [ ] Copilot instructions updated
- [ ] Timestamps included for freshness tracking
- [ ] Git commit hash included if available
- [ ] Validation report clean or issues documented

---

## Maintenance Notes

### When to Regenerate

- Major dependency updates
- Architecture changes
- New major features added
- Quarterly review

### Manual Sections

To preserve manual content across regeneration:

1. Use `<!-- MANUAL_START -->` and `<!-- MANUAL_END -->` markers
2. Content between markers preserved in `--update` mode

### Extending This Prompt

To add new documentation types:

1. Add detection logic in Task 0
2. Create new Task with template
3. Add to index in Task 7
4. Add validation rules in Task 8


## REQUIRED ARTIFACTS
- Use appropriate template from /templates
- Validate output using relevant checklist
- Follow copilot-instructions rules
