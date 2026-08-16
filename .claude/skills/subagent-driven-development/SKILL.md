---
name: subagent-driven-development
description: Orchestrates plan execution by dispatching specialized domain agents per task and auditing diffs with code-reviewer
---

# Subagent-Driven Development

Execute approved implementation plans task-by-task using specialized domain agents and continuous code review audits.

---

## 1. Orchestration Workflow

For each sequential task in the plan:

```
[Plan Task N]
      │
      ▼
1. Dispatch Specialized Agent:
   - Frontend task ──> agent: frontend-specialist (enforces frontend-vue)
   - Backend task  ──> agent: backend-specialist (enforces backend-python)
      │
      ▼
2. Agent Implements with TDD:
   - Write failing test ──> Implement code ──> Pass test & run lint
      │
      ▼
3. Dispatch Code Reviewer:
   - agent: code-reviewer audits diff against Karpathy & stack rules
      │
      ▼
4. Remediate & Complete:
   - Apply fixes if requested ──> Mark Task N done ──> Proceed to Task N+1
```

---

## 2. Agent Dispatch Rules

- **Frontend Tasks**: Pass task context to **`frontend-specialist`**. The agent must enforce `<template>` $\rightarrow$ `<script>` $\rightarrow$ `<style>`, `<script lang="ts">` for interfaces, strict equality, no falsy ambiguity, typed refs, and run ESLint.
- **Backend Tasks**: Pass task context to **`backend-specialist`**. The agent must enforce file docstrings, 4 sections with exact spacing, 3-tier ABC imports, class/func docstring formatting, custom errors, and strict typing.

---

## 3. Mandatory Review Gate

After an agent finishes a task:
1. Capture git diff or commit hash.
2. Invoke `requesting-code-review` / dispatch **`code-reviewer`**.
3. Do NOT proceed to the next task until the review verdict is `APPROVED`.

---

## 4. Final Completion

When all tasks in the plan are completed:
- Invoke **`verification-before-completion`** for the full suite check.
- Invoke **`finishing-a-development-branch`** to merge and clean up.
