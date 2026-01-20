# PRISM in 5 Minutes

**PRISM = Purpose-driven Requirements & Intelligent Software Method**

PRISM helps teams use AI safely by making intent explicit and risk visible —
without slowing development down.

---

## The One Rule to Remember

> **If it is not in the PRD, it is not a requirement.**

---

## The 5 Things You Actually Do

### 1️⃣ Start with a PRD
- Use the standard PRD template
- Fill all sections
- Mark unknowns as questions, not assumptions

**Use**
- `prd.template.md`
- `prd.of.feature.prompt.md`

---

### 2️⃣ Run PRD Lint (2 minutes)
- Checks completeness and clarity
- Catches gaps before coding

**Use**
- `prd.lint.prompt.md`

---

### 3️⃣ Get QA PRD Review (before code)
- QA reviews for testability and edge cases
- Fix issues early

**Use**
- `qa.prd.review.prompt.md`
- `qa-prd-review-checklist.md`

---

### 4️⃣ Implement + Run Ralph (safety check)
- Code strictly from PRD
- Run Ralph for AI-assisted or risky changes

**Use**
- `prd.to.implementation.prompt.md`
- `ralph.auto.pipeline.prompt.md`

---

### 5️⃣ Use the PR Template
- Link PRD
- Show QA + Ralph status
- Disclose AI vs Human contribution

**Use**
- `ralph.pr.template.md`

---

## Who Does What (Fast)

- **TPO** → owns PRD and scope
- **Dev** → implements from PRD
- **QA** → reviews PRD + validates behavior
- **Reviewer** → checks risk and readiness

AI helps everyone.  
Humans make decisions.

---

## When PRISM Matters Most

- New features
- AI-assisted changes
- Risky or complex code
- Cross-team work

---

## If You Only Do 3 Things

If you’re short on time:
1. Use the PRD template
2. Run PRD lint
3. Use the PR template

That alone removes most confusion.

---

## Final Reminder

PRISM is not extra process.  
It’s **clarity up front** to avoid rework later.

**Intent before code.**
