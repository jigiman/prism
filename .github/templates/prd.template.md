# Product Requirements Document (PRD)

## 1. Overview

### Problem Statement
What problem is being solved?
Who is impacted and why does this matter now?

### Goals
- What this change is intended to achieve
- Observable or measurable outcomes (if applicable)

### Non-Goals
- Explicitly state what is out of scope
- What this PRD does NOT attempt to solve

---

## 2. Background & Context

- Relevant background information
- Links to JIRA stories, incidents, or prior discussions
- Current behavior (for enhancements or bug fixes)

---

## 3. Requirements

### Functional Requirements
List clear, testable requirements.

Example:
- The system SHALL retry failed requests up to 3 times.
- The system SHALL surface an error after retries are exhausted.

### Non-Functional Requirements
Include constraints such as:
- Performance
- Reliability
- Security
- Compliance
- Accessibility (if applicable)

---

## 4. User Experience / API Behavior

Describe expected behavior from the user or client perspective.

Include:
- Success scenarios
- Failure scenarios
- Edge cases
- Error handling expectations

---

## 5. Acceptance Criteria

Each criterion must be testable.

Example:
- Given X, when Y happens, then Z occurs.
- When retries fail, a user-visible error is returned.

---

## 6. Assumptions & Open Questions

### Assumptions
List anything being assumed.

Example:
- Assumes downstream service is idempotent.

### Open Questions
Questions that must be resolved before or during implementation.

---

## 7. Risks & Mitigations

- Known risks (technical, UX, performance, rollout)
- Proposed mitigations or follow-ups

---

## 8. Dependencies & Rollout

### Dependencies
- External services
- Feature flags
- Data migrations
- Configuration changes

### Rollout Considerations
- Backward compatibility
- Incremental rollout or flags
- Monitoring and rollback plan

---

## 9. QA Notes

- Areas that may be difficult to test
- Suggested test scenarios
- Known coverage gaps

---

## 10. Change Log

- Version
- Date
- Summary of changes
- Author

### PRD Readiness Checklist
- [ ] PRD exists and follows the standard template
- [ ] PRD lint result: PASS / CONDITIONAL (accepted)
- [ ] QA PRD review completed
- [ ] PRD version/link referenced below

PRD Link:
PRD Lint Result:
QA Reviewer:

