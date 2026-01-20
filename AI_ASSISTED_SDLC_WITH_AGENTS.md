# AI-Assisted SDLC Workflow with Role-Based Agents

This document describes the approved end-to-end **AI-assisted Software Development Lifecycle (SDLC)** using **role-based AI agents**.  
It reflects the final, corrected workflow where **QA participates both before and after implementation**, and where **AI supports—not replaces—human judgment**. :contentReference[oaicite:0]{index=0}

---

## Core Principle

**AI accelerates development and review, but all decisions, approvals, and accountability remain human-owned.**

---

## Roles and Agents

- **TPO / Product Owner Agent**  
  Owns intent, scope, and requirements

- **Developer Agent**  
  Owns implementation and code changes

- **QA Agent**  
  Owns testability, validation, and regression risk

- **PR Reviewer Agent**  
  Owns independent technical review and merge readiness

---

## End-to-End Workflow

### Step 1 – PRD Creation (Intent Definition)

**Owner:** TPO (with Developer support)  
**Agent:** TPO Agent  

**Activities**
- Enrich JIRA stories
- Define goals, non-goals, and acceptance criteria
- Capture assumptions, constraints, and open questions

**Output**
- Draft PRD

---

### Step 2 – QA PRD Review (Pre-Implementation)

**Owner:** QA  
**Agent:** QA Agent  

**Activities**
- Review PRD for testability
- Identify missing edge cases
- Surface ambiguous or untestable requirements

**Output**
- PRD feedback and required clarifications

---

### Step 3 – PRD Finalization

**Owner:** TPO  
**Agent:** TPO Agent  

**Activities**
- Resolve QA and Dev questions
- Approve final scope and behavior

**Output**
- Approved PRD (single source of truth)

---

### Step 4 – Implementation

**Owner:** Developer  
**Agent:** Developer Agent  

**Activities**
- Implement strictly according to PRD
- Make assumptions explicit
- Avoid scope expansion

**Output**
- Code changes

---

### Step 5 – Ralph Context Review

**Owner:** Developer  
**Agent:** Developer Agent  

**Activities**
- Explain code behavior
- Surface risks and assumptions

**Output**
- Explained implementation

---

### Step 6 – Ralph Auto Pipeline

**Owner:** Developer  
**Agent:** Developer Agent  

**Activities**
- Automatic risk assessment
- Depth-adjusted review (fast/deep internally)
- Fix material issues
- Converge safely

**Output**
- Merge recommendation and known risks

---

### Step 7 – QA Validation (Post-Implementation)

**Owner:** QA  
**Agent:** QA Agent  

**Activities**
- Execute test scenarios
- Perform exploratory testing
- Assess regression risk

**Output**
- QA findings

---

### Step 8 – QA Regression Gate

**Owner:** QA  
**Agent:** QA Agent  

**Activities**
- Decide release readiness
- Mark **Pass / Conditional / Block**

**Output**
- QA gate decision

---

### Step 9 – PR Review

**Owner:** PR Reviewer  
**Agent:** PR Reviewer Agent  

**Activities**
- Review PRD alignment
- Review Ralph and QA outputs
- Raise final concerns

**Output**
- Review comments

---

### Step 10 – Human Merge Decision

**Owner:** Human Reviewer  

**Activities**
- Explicitly accept or defer risks
- Approve and merge code

**Output**
- Merged PR

---

## Key Rules

- QA PRD review **must occur before implementation**
- PRD is the **single source of truth** for intent
- Developers **must run Ralph Auto Pipeline** for AI-assisted changes
- QA **does not write production code**
- AI recommendations are **advisory only**
- Final decisions are **always human-owned**
