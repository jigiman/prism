# Ralph Pipeline Mode Selector Rules

Ralph is mandatory for ALL commits and PRs.

This document defines which pipeline mode is allowed
and prevents misuse of FAST mode for risky changes.

====================================================
DEFAULT RULE
====================================================

- FAST mode is allowed ONLY when explicitly permitted
- DEEP mode is the default for anything uncertain

When in doubt → use DEEP.

====================================================
FAST MODE — ALLOWED ONLY IF ALL ARE TRUE
====================================================

ALL of the following conditions must be met:

- Change is LOW risk
- No changes to:
  - Authentication or authorization
  - Security controls
  - Billing, payments, or quotas
  - Data models or migrations
  - External integrations
- No new public APIs or contracts
- No significant logic changes
- Code area is well-understood and previously reviewed

Examples:

- Refactoring without behavior change
- Comments or documentation
- Tests only
- Formatting or lint fixes
- Small bug fix with obvious cause and fix

If ANY condition is not met → FAST is NOT allowed.

====================================================
DEEP MODE — REQUIRED IF ANY ARE TRUE
====================================================

Use DEEP mode if ANY of the following apply:

- Brownfield or legacy code
- Medium or High risk change
- Business logic changes
- Authentication / authorization
- Security-sensitive paths
- Billing, payments, quotas, or limits
- Database schema or migrations
- Infrastructure or configuration changes
- First-time AI usage in a module
- Ralph FAST mode finds repeated or unclear issues
- Ralph FAST mode does not converge quickly

====================================================
ESCALATION RULE
====================================================

If FAST mode:

- Fails to converge after 2 iterations
- Surfaces unclear intent
- Reveals hidden assumptions

Then:

- STOP using FAST
- Escalate to DEEP mode
- Document escalation in commit or PR

====================================================
ACCOUNTABILITY RULE
====================================================

Using FAST mode incorrectly is a process violation.

Pipeline choice does NOT transfer responsibility.
The author remains fully accountable.
