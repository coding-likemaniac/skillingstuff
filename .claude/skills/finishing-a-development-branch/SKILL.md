---
name: finishing-a-development-branch
description: Safe and clean workflow for finalizing, merging, and cleaning up development branches and worktrees
---

# Finishing a Development Branch

Safely conclude a development branch, verify integration, and clean up temporary workspaces.

---

## 1. Pre-Merge Verification

Before merging or concluding:
1. Ensure all tasks in the implementation plan are marked complete.
2. Confirm `verification-before-completion` checks (tests, ESLint, type checks) pass cleanly.
3. Confirm code review was approved by `code-reviewer`.

---

## 2. Merge & Cleanup Workflow

1. **Commit All Changes**: Ensure git status is clean with a meaningful commit message.
2. **Rebase or Merge**: Rebase or merge cleanly onto the target branch (`main` / `develop`).
3. **Run Integration Verification**: Verify the full test suite on the integrated branch.
4. **Clean Worktree / Temporary Branch**: Remove temporary git worktrees or delete the merged feature branch if applicable.
