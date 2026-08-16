---
name: using-superpowers
description: Master skill gateway - establishes how to route tasks through the skill pipeline before taking action
---

# Skill Router & Gateway

Establish the active workflow and invoke relevant skills BEFORE taking any implementation action or making assumptions.

---

## 1. The Direct Path (Standard Feature Lifecycle)

When building new features, components, or making code modifications, follow the sequential pipeline:

```
[User Request] 
  ──> 1. brainstorming (Spike / Bounded / Architectural)
  ──> 2. writing-plans (Architectural path -> granular TDD plan)
  ──> 3. subagent-driven-development (Dispatches specialized agents)
        ├── frontend-specialist (Vue 3, Vuetify, TypeScript, ESLint)
        └── backend-specialist (Python, FastAPI, docstrings, sections)
  ──> 4. requesting-code-review (Dispatches code-reviewer agent)
  ──> 5. receiving-code-review (Applies audit fixes)
  ──> 6. verification-before-completion (ESLint, tests, types)
  ──> 7. finishing-a-development-branch (Git merge & cleanup)
```

---

## 2. Side Skills (On-Demand / Context-Specific)

Invoke these skills whenever specific non-linear scenarios occur:

- **Bugs / Test Failures / Regressions**: $\rightarrow$ Invoke `systematic-debugging`.
- **Isolated Feature Work / Branch Isolation**: $\rightarrow$ Invoke `using-git-worktrees`.
- **Parallel Independent Tasks**: $\rightarrow$ Invoke `dispatching-parallel-agents`.
- **Authoring / Modifying Skills**: $\rightarrow$ Invoke `writing-skills`.

---

## 3. Invocation Rule

- If a task involves **new creative work, feature design, or behavior changes**: ALWAYS invoke `brainstorming` before writing code or making plans.
- If a task is **fixing a bug or test failure**: ALWAYS invoke `systematic-debugging` to isolate root causes before altering code.
- Announce `"Using [skill] to [purpose]"` and adhere strictly to the skill's directives.
