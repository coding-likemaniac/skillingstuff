---
name: requesting-code-review
description: Dispatches the code-reviewer agent on completed tasks or diffs to audit against Karpathy and stack conventions
---

# Requesting Code Review

Dispatch the **`code-reviewer`** agent to evaluate diffs against Karpathy principles, `frontend-vue` conventions, and `backend-python` conventions.

---

## 1. When to Request Review

- **Mandatory**:
  - After completing each task in an implementation plan.
  - After finishing any major feature or refactor.
  - Before merging into the main branch.
- **Optional**:
  - When debugging complex issues or checking architectural baselines.

---

## 2. Dispatching the Reviewer

Dispatch the **`code-reviewer`** agent (`.claude/agents/code-reviewer.md`) providing:
1. **Description**: What was built or modified.
2. **Context / Plan Reference**: Task requirements and expected behavior.
3. **Diff / Commits**: Base commit SHA to Head commit SHA (or modified file list).

---

## 3. Evaluation

The reviewer outputs a structured verdict:
- **`APPROVED`**: Proceed to the next task.
- **`CHANGES REQUIRED`**: Address all reported violations before proceeding.
- **`BLOCKED`**: Major architectural breach; re-align with human partner.
