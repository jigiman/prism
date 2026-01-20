# Reviewer Guide: Ralph Pipeline

This document defines how reviewers must evaluate PRs
that use the Ralph pipeline.

This guide is for **reviewers only**.

---

## 1. Reviewer Role (Read First)

Reviewers are not responsible for re-running Ralph.

Reviewers are responsible for:

- Enforcing that Ralph was run
- Evaluating risk and intent
- Applying human judgment where required

> Reviewers verify trust.  
> They do not regenerate it.

---

## 2. First Check: Ralph Evidence (Mandatory)

Before reviewing any code, verify that the PR contains:

- A **Ralph Pipeline Summary**
- A **Ralph Gate result**
- The **PR checklist**, completed

### If any are missing

- ❌ Do NOT review the PR
- ❌ Do NOT comment on code
- Request changes:
  > “Ralph Pipeline Summary and Gate result are required.”

---

## 3. Validate the Ralph Gate Result

### If Gate = BLOCK

- ❌ Do NOT approve
- ❌ Do NOT suggest workarounds
- Require the author to fix issues and re-run Ralph

### If Gate = PASS

- Proceed to risk-based review

---

## 4. Validate Pipeline Mode Selection

Check:

- Pipeline mode selected (FAST or DEEP)
- Selection rationale

### FAST mode is acceptable ONLY if:

- Change is clearly low risk
- No auth, security, billing, data, infra, or schema changes
- No significant logic change

If FAST was used incorrectly:

- Request escalation to DEEP
- Do NOT approve

---

## 5. Review the Selection Rationale

Ensure the rationale:

- Matches the files changed
- Matches the risk level
- Does not minimize impact

If rationale is weak or vague:

- Request clarification
- Do NOT approve

---

## 6. Review Remaining Issues / Accepted Risks

Check whether:

- Remaining issues are Medium or Low only
- They are explicitly listed
- Acceptance rationale is reasonable

### Red flags

- “None” with clearly complex changes
- Vague acceptance (“acceptable for now”)
- Risk deferred without explanation

---

## 7. AI Attribution Review

Ensure the PR includes:

- AI | Human | AI-assisted
- Contribution percentages
- Basis for estimate

If attribution is missing or misleading:

- Request correction
- Do NOT approve

This is required even for human-only changes.

---

## 8. Human Review Is Still Required When

Reviewers MUST apply deeper scrutiny when:

- Risk level = High
- Security, auth, billing, data, or infra paths are involved
- Schema or migrations are present
- This is first-time AI usage in a module
- Ralph reports Medium issues affecting correctness

Ralph assists review; it does not replace it.

---

## 9. Non-Convergence Handling

If the PR shows:

- Multiple Ralph runs with unresolved issues
- Signs of “loop fatigue”
- Overuse of accepted risks

Then:

- Pause the PR
- Request human escalation
- Do NOT approve

---

## 10. What Reviewers Must NOT Do

- Do NOT approve PRs with Gate ≠ PASS
- Do NOT override Ralph findings
- Do NOT accept undocumented risks
- Do NOT say “LGTM” without Ralph evidence
- Do NOT treat Ralph output as optional

---

## 11. Reviewer Decision Checklist

Before approving, confirm:

- Ralph Pipeline Summary is present
- Pipeline mode is appropriate
- Ralph Gate = PASS
- Risks are understood and acceptable
- AI attribution is complete
- Human judgment has been applied where required

If any item fails → do not approve.

---

## 12. Accountability Reminder

Approval means:

- You understand the risk
- You agree the change is safe to merge
- You accept shared responsibility

> Ralph improves safety.  
> Re
