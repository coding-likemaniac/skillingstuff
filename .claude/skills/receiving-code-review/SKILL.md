---
name: receiving-code-review
description: Guidelines for ingesting, addressing, and verifying code review feedback without defensive rationalization
---

# Receiving Code Review

Process and apply review feedback rigorously and objectively.

---

## 1. Principles of Receiving Feedback

- **No Defensive Rationalizations**: Do not defend violations of conventions (e.g., "it's obvious so comments weren't needed" or "any was just temporary").
- **Fix at the Root**: Address the underlying structural issue, not just the symptom.
- **Maintain Invariants**: Ensure fixes adhere strictly to `frontend-vue` (script separation, no `any`, explicit checks) and `backend-python` (docstrings, section spacing, custom errors).

---

## 2. Remediation Workflow

1. **Categorize Feedback**:
   - **Critical / Blocker**: Fix immediately before any other work.
   - **Important / Convention Violation**: Fix and re-verify tests.
   - **Minor / Optimization**: Address cleanly or note for follow-up.
2. **Implement Fixes**: Apply minimal, surgical corrections.
3. **Re-Verify**: Run test suites and ESLint / linters to ensure green status.
4. **Re-Review**: If major changes were made, request verification from `code-reviewer`.
