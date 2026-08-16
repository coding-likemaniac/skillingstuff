# CLAUDE.md

> "Think before coding. Keep solutions minimal, direct, and strictly typed. Zero bloat."

---

## 1. Operating Philosophy (Karpathy Mode)

- **Think First**: Establish a clear mental model of the system and constraints before modifying code.
- **Radical Simplicity**: Write flat, readable, unambiguous logic. Avoid premature abstractions or bloated wrappers.
- **Surgical Changes**: Make minimal, focused diffs. Never rewrite working files or cause unrelated churn.
- **High Signal-to-Noise**: Code must be self-explanatory. No obvious restatements, decorative comments, or conversational chatter.
- **Deterministic Verification**: Verify code with automated tests, type checks, and linters before completing tasks.

---

## 2. Universal Standards

- **Strict Equality**: Always use `===` and `!==`. Never `==` or `!=`.
- **Zero Falsy Ambiguity**: Never use `(!val)` or implicit truthy/falsy coercion. Always use explicit checks (`val !== null && val !== undefined`, `str !== ''`, `arr.length === 0`).
- **Strict Typing**: Enforce strict types. Never use `any`. Use `unknown` with narrowing only when strictly necessary.
- **Modularity**: Small, reusable components and functions with clear indicative names.

---

## 3. Skill & Agent Lifecycle

### The Direct Path (Primary Feature Pipeline)

```
[User Request]
  ──> 1. using-superpowers (Skill Gateway)
  ──> 2. brainstorming (Spike / Bounded / Architectural)
  ──> 3. writing-plans (Architectural path -> granular TDD plan)
  ──> 4. subagent-driven-development (Orchestrates implementation)
        ├── frontend-specialist (enforces frontend-vue)
        └── backend-specialist (enforces backend-python)
  ──> 5. requesting-code-review (Dispatches code-reviewer agent)
  ──> 6. receiving-code-review (Applies audit fixes)
  ──> 7. verification-before-completion (Tests, ESLint, type checks)
  ──> 8. finishing-a-development-branch (Git merge & cleanup)
```

| Lifecycle Stage | Skill / Tool | Role |
|---|---|---|
| **Gateway** | [using-superpowers](skills/using-superpowers/SKILL.md) | Routes requests and enforces using skills before action. |
| **Design** | [brainstorming](skills/brainstorming/SKILL.md) | Classifies path (Spike / Bounded / Architectural) and secures design approval. |
| **Planning** | [writing-plans](skills/writing-plans/SKILL.md) | Breaks architectural specs into bite-sized TDD tasks. |
| **Execution** | [subagent-driven-development](skills/subagent-driven-development/SKILL.md) | Dispatches `frontend-specialist` or `backend-specialist` per task. |
| **Review** | [requesting-code-review](skills/requesting-code-review/SKILL.md) | Dispatches `code-reviewer` agent on diffs. |
| **Remediation** | [receiving-code-review](skills/receiving-code-review/SKILL.md) | Ingests and applies review feedback without excuses. |
| **Verification** | [verification-before-completion](skills/verification-before-completion/SKILL.md) | Pre-completion checklist (tests, ESLint, types). |
| **Completion** | [finishing-a-development-branch](skills/finishing-a-development-branch/SKILL.md) | Merges branch and cleans up worktrees. |

---

### Side Skills (On-Demand)

| Side Skill | Trigger Condition |
|---|---|
| [systematic-debugging](skills/systematic-debugging/SKILL.md) | Triggered whenever investigating bugs, unexpected behaviors, or test failures. |
| [using-git-worktrees](skills/using-git-worktrees/SKILL.md) | Triggered when isolating tasks or branches in separate worktrees. |
| [dispatching-parallel-agents](skills/dispatching-parallel-agents/SKILL.md) | Triggered when orchestrating multiple independent, non-conflicting tasks. |
| [writing-skills](skills/writing-skills/SKILL.md) | Triggered only when authoring or refining skills (comprehensive reference suite). |

---

## 4. Technology Stack Conventions

### Frontend (Vue 3 + Vuetify + TypeScript)
- Refer to [frontend-vue](skills/frontend-vue/SKILL.md) and [frontend-specialist](agents/frontend-specialist.md).
- SFC order: `<template>` $\rightarrow$ `<script>` $\rightarrow$ `<style scoped>`.
- Isolate interfaces in `<script lang="ts">` (never exported from `.vue`; shared models go to `models/`).
- Logic & imports in `<script setup lang="ts">` (shared functions go to `utils/`).
- API requests live in `requests/` and are consumed via loadable composables (`loading`, `error`, `data`).
- Explicit refs: `ref<Type>(val)`. Prefer `watch(props)` over `onMounted` for prop-dependent state.
- Always run `eslint` and fix all lint errors before declaring frontend work complete.

### Backend (Python + FastAPI)
- Refer to [backend-python](skills/backend-python/SKILL.md) and [backend-specialist](agents/backend-specialist.md).
- File header docstring with `:author:` and `:date:` without mentioning file, class, or function names.
- 4 fixed sections: `# ----- IMPORTS ----- #`, `# ----- CONSTS ----- #`, `# ----- CLASSES ----- #`, `# ----- FUNCTIONS ----- #`.
- Spacing: Imports banner directly after docstring (0 blank lines above, 1 below); Classes & Functions banners require exactly 2 blank lines above.
- 3-tier ABC-sorted imports (Standard library $\rightarrow$ Third-party $\rightarrow$ Internal project).
- Strict docstrings (class role without names; function summary, `:param:`, immediate `:return:`, `:raises:`).
- Custom exceptions defined in `errors.py`. Full strict type annotations.
