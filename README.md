# PRISM  
**Purpose-driven Requirements & Intelligent Software Method**

PRISM is a **governed, role-based AI-assisted SDLC framework** designed to help
teams build software with **clarity, safety, and speed**.

It standardizes how AI is used across requirements, implementation, review,
and testing — without replacing human judgment.

> **AI is a multiplier. Accountability remains human-owned.**

---

## Why PRISM Exists

Modern teams use AI every day, but without structure it leads to:
- Ambiguous requirements
- Inconsistent code quality
- Review churn
- QA feedback arriving too late
- Unclear ownership of decisions

PRISM solves this by making **intent explicit**, **roles clear**, and
**AI usage predictable** across the SDLC.

---

## Core Principle

> **If it is not in the PRD, it is not a requirement.**

PRISM is built around this rule.

---

## What PRISM Is (and Is Not)

### PRISM IS
- A lightweight framework for AI-assisted development
- A set of templates, agents, and prompts
- A way to reduce rework and review friction
- A safety net for AI-generated code

### PRISM IS NOT
- A replacement for engineers or reviewers
- A rigid process or bureaucracy
- An approval system
- A mandate to use AI everywhere

---

## How PRISM Is Structured

.github/
├── copilot-instructions/ # Always-on AI behavior and governance rules
agents/ # Role-based AI personas (Dev, QA, TPO, Reviewer)
prompts/ # Task-specific AI workflows
templates/ # Standardized artifacts (PRD, PR, etc.)
checklists/ # Quality and readiness checks


Each layer has a single responsibility:

- **Instructions** define how AI behaves all the time
- **Agents** define who AI is acting as
- **Prompts** define what AI is asked to do
- **Templates** reduce ambiguity across roles

---

## Supported Roles

PRISM enforces clear role boundaries:

- **Developer** — implementation and code changes
- **QA Engineer** — PRD review, testing, regression risk
- **TPO / Product Owner** — intent, scope, and requirements
- **PR Reviewer** — independent technical review

Each role:
- Has explicit responsibilities
- Has explicit constraints
- Can hand off work to other roles cleanly

---

## The PRISM Workflow (High Level)

1. **PRD Creation** using a standard template  
2. **PRD Lint** (AI quality check)  
3. **QA PRD Review** (before implementation)  
4. **Implementation** (PRD is the source of truth)  
5. **Ralph Auto Pipeline** (risk-based AI review)  
6. **QA Validation** (post-implementation)  
7. **PR Review & Human Merge Decision**

PRISM shifts thinking **left**, where it is cheaper and safer.

---

## When to Use PRISM

PRISM is especially valuable for:
- AI-assisted code changes
- Medium to high-risk features
- Teams with frequent review churn
- Environments with strong QA or compliance needs

---

## Getting Started

1. Read the files in `.github/copilot-instructions/`
2. Activate the appropriate agent in GitHub Copilot Chat
3. Use the standard templates and prompts
4. Follow the PRISM workflow described in `USAGE_GUIDE.md`

Additional documentation:
- `USER_GUIDE.md` — role-based guidance
- `USAGE_GUIDE.md` — step-by-step workflow

---

## Final Note

PRISM does not slow teams down.  
It removes ambiguity so teams can move faster — safely.

AI helps you build.  
Humans decide what ships.
