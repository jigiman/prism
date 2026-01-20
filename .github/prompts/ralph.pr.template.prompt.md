# Generate Ralph PR Summary (Selector + Gate)

You are acting as a **PR documentation generator**.

Your job is to generate a **copy-ready PR section**
based on the most recent Ralph Pipeline run.

====================================================
INPUT
====================================================

Use:

- The most recent Ralph selector decision
- The executed pipeline mode (FAST or DEEP)
- The final Ralph Gate result
- Any remaining issues or accepted risks

If information is missing, call it out explicitly.

====================================================
OUTPUT RULES
====================================================

- The output MUST be copy-paste ready in code block
- Use clear headings
- Be concise but complete
- Do NOT include analysis or commentary outside the template

====================================================
OUTPUT FORMAT (FOLLOW EXACTLY)
====================================================

## Ralph Pipeline Summary

**Pipeline Mode Selected:** FAST | DEEP

**Selection Rationale:**

- Bullet list explaining why this mode was required

---

## Ralph Gate Result

**Gate Status:** PASS | BLOCK

**Blocking Issues:** Yes | No  
(If yes, briefly summarize)

---

## Remaining Issues / Accepted Risks

(List any remaining Medium / Low issues or explicitly say “None”)

---

## AI Attribution

- Changed by: AI | Human | AI-assisted
- AI contribution: \_\_\_%
- Human contribution: \_\_\_%
- Basis for estimate:

---

## Merge Confidence Statement

One sentence answering:
“Why is this safe (or unsafe) to merge given the context and constraints?”

---

## PR Checklist

- [ ] **Ralph Pipeline Summary (Selector + Gate output) is attached and Gate = PASS**
- [ ] Ralph Gate result is **PASS**
- [ ] Remaining Medium / Low risks (if any) are explicitly documented
- [ ] Risk level (Low / Medium / High) is correctly classified
