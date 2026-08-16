---
name: verification-before-completion
description: Final quality gate - mandatory checks across tests, linters, types, and git diff before claiming completion
---

# Verification Before Completion

Perform comprehensive verification before closing any task, PR, or session. Never assume code works without executing automated verification.

---

## 1. Mandatory Checklist

Before declaring any feature or fix complete, execute and confirm:

- [ ] **Automated Tests**: Run the relevant test suite (e.g. `npm test` / `pytest`) and ensure 100% passing tests.
- [ ] **Linters & Formatters**: Run ESLint (`npm run lint`) for frontend code and ensure zero remaining warnings/errors.
- [ ] **Type Checks**: Run TypeScript compiler (`npx vue-tsc --noEmit` or `npx tsc --noEmit`) and Python type checker (`mypy` or `pyright`).
- [ ] **Git Diff Inspection**: Review `git diff` to ensure no accidental changes, leftover debug logs, or unauthorized comments exist.

---

## 2. Gate Enforcement

If any check fails:
1. Do not mark the task complete.
2. Fix the violation immediately.
3. Re-run the full verification command until clean.
