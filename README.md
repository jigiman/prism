# AI-Assisted Development System

This repository uses a **governed, role-based AI-assisted SDLC** powered by
GitHub Copilot, prompts, and agents.

AI is used to accelerate analysis, implementation, review, and testing —
**not** to replace human judgment.

---

## Core Principles

- AI is advisory, not authoritative
- Humans own requirements, code, reviews, and merge decisions
- If it is not in the PRD, it is not a requirement
- Role boundaries are enforced (Dev, QA, TPO, Reviewer)

---

## How the System Is Structured

.github/
copilot-instructions/ # Always-on AI behavior rules
agents/ # Role-based AI personas
prompts/ # Task-specific workflows


Each layer has a single responsibility:

- **Instructions** define how AI behaves all the time
- **Agents** define who AI is acting as
- **Prompts** define what AI is asked to do

---

## Supported Roles

- Developer
- QA Engineer
- TPO / Product Owner
- PR Reviewer

Each role has:
- Clear responsibilities
- Clear boundaries
- Explicit handoffs to other roles

---

## When to Use AI

AI is expected to be used for:
- PRD creation and enrichment
- Code implementation and explanation
- Risk analysis and safety review (Ralph)
- Test design and regression assessment
- PR summaries and reviewer context

AI must NOT be used as an approval authority.

---

## Getting Started

1. Read the instructions in `.github/copilot-instructions/`
2. Activate the appropriate agent in Copilot Chat
3. Use the allowed prompts for that role
4. Follow the SDLC flow documented below

See:
- `USER_GUIDE.md` for role-based guidance
- `USAGE_GUIDE.md` for step-by-step workflows
