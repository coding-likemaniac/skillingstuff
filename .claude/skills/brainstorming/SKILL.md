---
name: brainstorming
description: Mandatory skill before creative or architectural work - turns ideas into validated designs before implementation
---

# Brainstorming Ideas Into Designs

Explore user intent, requirements, and design approaches before writing code or plans.

---

## 1. The Three Paths

Before asking questions or taking action, classify the request into one of three paths and state the classification:

1. **Spike (Feasibility Probe)**:
   - *Scope*: Quick feasibility check ("Can we do X?", "Is library Y compatible?").
   - *Action*: Present question and probe plan in 2–3 sentences. Get user nod. Run probe cheaply.
   - *Output*: Recommendation report in chat. Code is labeled throwaway. No spec doc or plan file.

2. **Bounded (Isolated, In-Flow Modification)**:
   - *Scope*: Well-scoped change to existing, established flows in the repo (e.g., adding a button/dialog to a Vue view, adding a CRUD route to an existing FastAPI router, a small utility).
   - *Action*: Check context $\rightarrow$ ask 1–2 essential clarifying questions $\rightarrow$ present short 2–3 paragraph design in chat (approach, files touched, test strategy).
   - *Gate*: **STOP and wait for user approval**.
   - *Output*: Once approved, proceed directly to implementation via `frontend-vue` or `backend-python`. No plan document.

3. **Architectural (New Subsystems & Structural Changes)**:
   - *Scope*: New projects, major subsystems, cross-cutting state/data models, or API contract changes.
   - *Action*: Check context $\rightarrow$ ask clarifying questions (one per message) $\rightarrow$ propose **2–3 distinct approaches** with trade-offs and recommendation $\rightarrow$ present sectioned design in chat.
   - *Output*: Write approved design doc to `docs/specs/YYYY-MM-DD-<topic>-design.md`. After user reviews and approves spec, invoke `writing-plans`.

---

## 2. Hard Approval Gates

- **Never skip approval**: Even for the simplest bounded task, state the approach in chat and receive confirmation before writing code.
- **Upward ratchet**: If a bounded task turns out to have hidden architectural complexity, stop immediately, announce the upgrade to Architectural, and follow the full spec process.

---

## 3. Collaborative Dialogue Rules

- **One question at a time**: Keep questions focused and concise (prefer multiple-choice when feasible).
- **YAGNI ruthlessly**: Eliminate speculative abstractions or unneeded helper libraries.
- **Clear mental model**: Present components with defined interfaces and boundaries so each can be understood and tested in isolation.

---

## 4. Handoff

- **Bounded Path** $\rightarrow$ Direct implementation enforcing `frontend-vue` or `backend-python`.
- **Architectural Path** $\rightarrow$ Spec file approved $\rightarrow$ Transition to `writing-plans`.
