---
name: writing-plans
description: Translates approved architectural specifications into granular, bite-sized implementation plans with automated verification
---

# Writing Implementation Plans

Create structured, executable implementation plans where each task is small, test-driven, and verifiable.

---

## 1. Plan Structure

Save every implementation plan to `docs/plans/YYYY-MM-DD-<topic>-plan.md`.

Each plan must include:
1. **Overview & Goal**: Brief statement of the target outcome.
2. **Domain Conventions**:
   - Frontend tasks must explicitly state adherence to `frontend-vue` (Vue 3, Vuetify, strict TS, SFC layout, loadable API composables, ESLint).
   - Backend tasks must explicitly state adherence to `backend-python` (Python/FastAPI, 4 sections with spacing rules, 3-tier ABC imports, docstrings, custom errors).
3. **Task Breakdown**: Numbered, sequential tasks.

---

## 2. Granular Task Specification

Every task in the plan must specify:
- **Files Modified / Created**: Explicit file paths.
- **Implementation Details**: What exact changes/methods are added.
- **Verification / Test Criteria**: The exact automated command to verify correctness (e.g. `npm run test`, `pytest tests/test_auth.py`, `npm run lint`).
- **Dependencies**: Prerequisites needed before this task can start.

---

## 3. Plan Review & Handoff

1. Conduct a self-check for gaps, contradictions, or missing tests.
2. Request human approval for the written plan file.
3. Upon approval, invoke **`subagent-driven-development`** (or `executing-plans`) to begin implementation.
