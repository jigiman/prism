# PRISM Changelog

All notable changes to the PRISM framework are documented here.

This changelog tracks changes to:
- Agents
- Prompts
- Templates
- Checklists
- Gates and workflow rules

PRISM = Purpose-driven Requirements & Intelligent Software Method

---

## [v1.2.0] – Branch Management & Workflow Enforcement

### Added

#### Git Branch Management
- Mandatory git branch creation step added to PRD generation workflow
- Branch naming convention enforcement: `<prefix><JIRA-ID>-<short-kebab-case-name>`
- Automatic branch prefix selection based on MODE (feature/ or bug/)
- Branch checkout validation before PRD documentation creation
- Prevention of PRD creation on main/master/develop branches

#### Agent Enhancements
- **Developer Agent:** Added rules to prevent JIRA ticket ID invention or auto-increment
- **TPO Agent:** Added rules to prevent JIRA ticket ID invention or auto-increment
- **PR Reviewer Agent:** Added comprehensive PR gate for Branch ↔ JIRA ↔ Specs alignment
  - Branch naming validation
  - JIRA ID consistency checks
  - Specs directory alignment verification
  - Prompt ownership rules enforcement

#### Prompt Updates
- **prd.of.feature:** Added mandatory git branch creation pre-step
- **prism.self-check:** Added git branch validation step
- **ralph.auto.pipeline:** Added branch creation validation
- **architecture-documentation-generator:** Simplified and clarified output location rules to enforce `docs/architecture/` only

#### Workflow Governance
- Enforced strict alignment between git branch, JIRA ticket ID, and specs directory
- Added blocking PR gate for misaligned artifacts
- Clarified prompt ownership (prd.of.feature creates, others reuse existing branches)

### Changed
- **architecture-documentation-generator:** Reduced complexity and enforced strict output location to `docs/architecture/` only
- **prd.of.feature:** Updated output location documentation to include full JIRA ID prefix in directory naming

---

## [v1.1.0] – Governance & Enforcement Hardening

### Added

#### Framework Governance
- PRISM self-check prompt to evaluate end-to-end compliance before merge
- Explicit `## Uses` section added to all prompts, binding:
  - required templates
  - required checklists
  - governing copilot-instructions
- PRISM versioning via `PRISM_VERSION` file

#### Agents
- Hardened role definitions for:
  - Developer
  - QA
  - TPO / Product Owner
  - PR Reviewer
- Explicit agent responsibilities for:
  - PRD gates
  - QA gates
  - Ralph pipeline usage
  - ADR creation
  - Role boundary enforcement
- Integrated checklist usage directly into agent rules
- Added help & discovery behavior to Developer agent

#### Prompts
- PRISM self-check prompt (pre-merge governance gate)
- PR description lint prompt
- Commit message lint prompt
- Embedded template + checklist enforcement in all prompts
- Ralph pipeline prompts aligned with standard Ralph output template

#### Templates
- PR template (`ralph.pr.template.md`) updated to enforce PRISM:
  - PRD compliance
  - QA gates
  - Ralph gates
  - AI vs Human contribution transparency
- Optional ADR template for architectural decisions
- Optional incident / postmortem template for production issues

#### Checklists
- QA PRD review checklist formalized as a pre-implementation gate
- PR review checklist aligned with PRISM merge readiness

---

## [v1.0.0] – Initial Release

### Added
- Standard PRD template with explicit assumptions, risks, and acceptance criteria
- PRD lint prompt as a quality gate before implementation
- Mandatory QA PRD review step (pre-implementation)
- Role-based AI agents: Developer, QA, TPO, PR Reviewer
- Ralph auto pipeline with convergence rules
- Templates for:
  - PR descriptions (including AI vs human contribution)
  - Commit messages
  - QA test scenarios
  - Bug reports
  - Ralph review outputs
- Checklists for:
  - QA PRD review
  - PR review readiness
- Explicit template, checklist, and instruction binding in prompts
- PRD → Implementation hard gate

### Principles Locked In
- AI is advisory, not authoritative
- Humans own decisions and approvals
- If it is not in the PRD, it is not a requirement
- Role boundaries must be respected
- Risk must be explicit, not hidden

---

## [Unreleased]

### Planned
- PRISM compliance badge or status line in PRs
- Additional lint prompts (QA scenarios, ADR completeness)
- CONTRIBUTING.md for PRISM usage expectations
- Visual workflow diagram for onboarding
- Minor wording clarifications based on pilot feedback
