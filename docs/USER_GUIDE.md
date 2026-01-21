# User Guide — AI-Assisted SDLC

This guide explains **how each role should use AI** in day-to-day work.

---

## Developer Guide

### When to activate
Use the Developer agent when:
- Implementing features or enhancements
- Fixing bugs
- Explaining or modifying code

### Responsibilities
- Implement strictly based on the PRD
- Make assumptions explicit
- Run the Ralph auto pipeline for AI-assisted or risky changes

### What Developers must NOT do
- Do not invent requirements
- Do not skip PRD or Ralph
- Do not use QA prompts to justify code changes
- Do not approve PRs

---

## QA Guide

### When to activate
Use the QA agent:
- Before implementation (PRD review)
- After implementation (validation and regression)

### Responsibilities
- Review PRDs for testability
- Identify gaps, edge cases, and ambiguity
- Design test scenarios and exploratory testing
- Assess regression and release readiness

### What QA must NOT do
- Do not write or modify production code
- Do not approve implementation decisions

---

## TPO / Product Owner Guide

### When to activate
Use the TPO agent when:
- Stories are incomplete or unclear
- PRDs need creation or refinement

### Responsibilities
- Clarify intent and scope
- Define goals, non-goals, and acceptance criteria
- Confirm or reject inferred requirements

### What TPO must NOT do
- Do not write code
- Do not perform QA validation
- Do not approve implementation details

---

## PR Reviewer Guide

### When to activate
Use the PR Reviewer agent during PR review.

### Responsibilities
- Assess correctness and risk
- Review Ralph and QA outputs
- Raise concerns and questions
- Support an informed merge decision

### What Reviewers must NOT do
- Do not implement fixes
- Do not bypass QA
- Do not treat AI output as approval

---

## Role Handoffs

If a request crosses role boundaries:
- Politely refuse
- Use agent handoffs to redirect
- Preserve context when switching roles
