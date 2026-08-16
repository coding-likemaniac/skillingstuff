---
name: dispatching-parallel-agents
description: Protocol for dispatching and synchronizing multiple concurrent subagents on non-conflicting tasks
---

# Dispatching Parallel Agents

Safely orchestrate multiple concurrent subagents on independent, non-overlapping tasks.

---

## 1. Safety Criteria for Parallelism

Only dispatch parallel subagents when all of the following hold:
- **Disjoint File Sets**: Subagents touch strictly different files and directories.
- **Zero Shared Mutable State**: No database migrations or shared state locks.
- **Clear Scope**: Each subagent receives an isolated, self-contained specification.

---

## 2. Dispatch Pattern

1. **Partition Tasks**: Group plan tasks into independent batches.
2. **Assign Specialized Roles**:
   - Assign frontend tasks to `frontend-specialist`.
   - Assign backend tasks to `backend-specialist`.
3. **Await & Review**: Collect results and dispatch `code-reviewer` across all completed task diffs.
