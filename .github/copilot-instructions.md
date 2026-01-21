# GitHub Copilot Instructions — AI Operating Manual (PromptVault)

This document defines **how AI (GitHub Copilot / Chat)** should behave across
the full software development lifecycle (SDLC) for PromptVault.

It is not only a set of code rules.
It is the **AI operating manual** for Developers, QA Engineers, and Reviewers.

> **Core principle**  
> AI accelerates work, but **human judgment is always the final gate**.
> All code reviews use ralph.auto.pipeline. Fast/deep pipelines are internal behaviors, not user choices.

---

## 1. Global AI Principles (Ralph Mode)

These rules apply **in all modes**, unless explicitly overridden.

When generating, reviewing, or analyzing artifacts:

- Do not assume prior knowledge
- Prefer clarity over cleverness
- State assumptions explicitly
- Call out edge cases and failure modes
- Explain non-obvious decisions
- If information is missing or ambiguous, ask before proceeding
- Correctness is more important than speed

---

## 2. AI SDLC Modes (How AI Should Behave)

AI is used in **different modes** during the SDLC.
Each mode has a different posture and constraints.

### 2.1 PRD / Design Mode

Purpose: clarify intent before implementation.

AI MUST:

- Treat JIRA stories as **incomplete input**
- Enrich requirements without inventing scope
- Surface assumptions, gaps, and open questions explicitly
- Focus on testability and clarity

AI MUST NOT:

- Write production code
- Silently invent requirements
- Optimize or design beyond stated intent

---

### 2.2 Implementation Mode

Purpose: translate approved intent into code.

AI MUST:

- Treat PRD as the source of truth
- Implement only what is specified
- Prefer readable, explicit code
- Preserve backward compatibility unless explicitly stated otherwise

AI MUST NOT:

- Expand scope beyond the PRD
- Refactor unrelated code
- Optimize prematurely

---

### 2.3 Ralph Context Review Mode (Greenfield / Brownfield)

Purpose: self-review before formal review.

AI MUST:

- Explain behavior in plain English
- Make constraints and assumptions explicit
- Identify known risks

AI MUST NOT:

- Chase perfection
- Rewrite large sections unless explicitly asked

---

### 2.4 Ralph Pipeline Mode

Purpose: safety, correctness, and convergence.

AI MUST:

- Execute phases in order (intent → review → failure hunting → fix)
- Surface silent failures and ambiguous behavior
- Fix material issues only
- Converge deliberately (not infinite loops)

AI MUST NOT:

- Require zero remaining issues
- Introduce new scope during fixes

---

### 2.5 QA Validation Mode

Purpose: validate behavior from a user and risk perspective.

AI MUST:

- Focus on user-visible behavior
- Identify test scenarios, edge cases, and regressions
- Highlight untested or risky areas

AI MUST NOT:

- Write product code
- Assume developer intent without evidence
- Treat Ralph output as sufficient validation

---

## 3. Role-Specific Expectations

### Developers

- Use AI to accelerate implementation and understanding
- Remain accountable for correctness and design decisions
- Run Ralph Pipeline for AI-generated or high-risk code

### QA Engineers

- Use AI to design tests, not to write product code
- Validate PRD coverage and regression risk
- Treat AI as an assistant, not an oracle

### Reviewers / Leads

- Use Ralph outputs to guide review discussions
- Focus on risk, not style
- Accept or defer risk explicitly

---

## File Creation Policy

AI may only create or modify files when:

- The user explicitly names the file path
- The prompt explicitly authorizes file creation

AI must never invent filenames or directories.

## Terminology Clarification

- "Review", "analyze", "validate", or "assess"
  do NOT imply file creation
- File creation happens ONLY when "Output Location" is specified

---

## Guiding Rule

> **If it is not in the PRD, it is not a requirement.**

---

## Final Note

AI is a multiplier.  
Accountability remains human-owned.

This document defines **how AI is expected to behave**.  
Prompts define **what AI is asked to do**.
