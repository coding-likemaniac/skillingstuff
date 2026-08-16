---
name: using-git-worktrees
description: Guidelines for setting up and working within isolated git worktrees for parallel branches and tasks
---

# Using Git Worktrees

Isolate development work across distinct branches without altering the primary working directory.

---

## 1. When to Use Worktrees

- Working on multiple independent features or bug fixes simultaneously.
- Running long-running background tasks or subagent sessions in isolation.
- Testing a risky refactor without disturbing the active branch.

---

## 2. Standard Commands

```bash
# Create and switch to a new worktree branch
git worktree add -b feature/my-feature ../worktrees/my-feature main

# List active worktrees
git worktree list

# Remove a worktree after branch is merged
git worktree remove ../worktrees/my-feature
```

---

## 3. Best Practices

- Always initialize fresh dependencies (e.g. `npm install` or virtual environment) within the isolated worktree directory if required.
- Clean up completed worktrees to prevent disk sprawl.
