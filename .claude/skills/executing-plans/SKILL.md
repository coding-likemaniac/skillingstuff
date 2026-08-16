---
name: executing-plans
description: Direct, linear execution of an approved implementation plan with TDD and continuous verification
---

# Executing Plans

Execute implementation plans in a structured, step-by-step sequence when not delegating to parallel subagents.

---

## 1. Execution Loop

For each task in the plan:
1. **Load Task Context**: Read targeted files and understand task boundaries.
2. **Apply Domain Conventions**:
   - For Vue/Vuetify code: Enforce `frontend-vue` rules (SFC order, script separation, strict equality, explicit refs, ESLint).
   - For Python/FastAPI code: Enforce `backend-python` rules (file docstring, 4 sections with spacing, 3-tier ABC imports, custom errors).
3. **Test-Driven Implementation**:
   - Write or update automated unit/integration tests first.
   - Implement minimum code required to pass.
   - Run tests and linters to verify green.
4. **Audit**: Dispatch `code-reviewer` agent or perform strict self-audit against the code review checklist.
5. **Mark Task Complete**: Update the plan file before moving to the next item.

---

## 2. Completion

When all tasks are complete, invoke `verification-before-completion` before declaring the feature done.
