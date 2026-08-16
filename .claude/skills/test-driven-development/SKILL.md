---
name: test-driven-development
description: Test-Driven Development protocol - Red -> Green -> Refactor cycle for reliable feature and bug implementation
---

# Test-Driven Development (TDD)

Build robust functionality by writing failing automated tests before writing implementation code.

---

## 1. The Red-Green-Refactor Cycle

```
[Write Failing Test] ──> [Run Test (RED)] ──> [Write Minimal Code] ──> [Run Test (GREEN)] ──> [Refactor]
```

1. **Red**: Write a focused, automated test demonstrating the desired behavior or bug. Run it and confirm it fails for the expected reason.
2. **Green**: Write the simplest, most direct code to make the test pass. Do not write premature features.
3. **Refactor**: Clean up the implementation adhering to `frontend-vue` or `backend-python` standards while ensuring tests remain green.

---

## 2. Testing Principles

- **Deterministic**: Tests must not rely on random data or unseeded randomness.
- **Isolated**: Tests must execute independently without depending on run order or shared mutable state.
- **Expressive**: Test names must clearly state the scenario and expected outcome (e.g. `test_authenticate_user_invalid_password_raises_error`).
