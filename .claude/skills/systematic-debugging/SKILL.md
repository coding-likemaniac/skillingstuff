---
name: systematic-debugging
description: Root-cause debugging protocol - mandatory whenever investigating bugs, unexpected behaviors, or failing tests
---

# Systematic Debugging Protocol

Isolate the fundamental root cause before touching or modifying code. Never guess or apply speculative patches.

---

## 1. The 4-Phase Protocol

```
Phase 1: Reproduce ──> Phase 2: Isolate Root Cause ──> Phase 3: Surgical Fix ──> Phase 4: Regression Test
```

### Phase 1: Reproduce Deterministically
- Create an automated minimal reproduction script or failing unit/integration test.
- Do not proceed until the failure is reliably reproducible.

### Phase 2: Isolate Root Cause
- Trace the defect backwards from the symptom to the exact invalid state transition.
- Formulate a specific, falsifiable hypothesis and verify with targeted logs/assertions.
- Do not treat symptoms (e.g. adding `if (val)` checks to hide `TypeError`); find why the invalid state reached that point.

### Phase 3: Surgical Fix
- Implement the simplest, most minimal fix that resolves the root cause.
- Adhere strictly to domain conventions (`frontend-vue` for Vue, `backend-python` for Python).

### Phase 4: Regression Verification
- Verify that the reproduction test passes.
- Run the full test suite and linters to ensure zero regressions.

---

## 2. Red Flags (Stop & Re-evaluate)
- If you find yourself adding speculative `try/catch` or null guards without understanding why data was null $\rightarrow$ STOP.
- If you find yourself editing unrelated files during a bug fix $\rightarrow$ STOP.
