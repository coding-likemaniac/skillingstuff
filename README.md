# Claude Code Configuration Kit

A copy-pastable `.claude` configuration combining Andrej Karpathy's software engineering principles with your custom Vue 3 / Vuetify frontend conventions, Python / FastAPI backend conventions, and a full suite of streamlined skills and specialized subagents.

---

## Directory Architecture

```
claude-configuration/
├── CLAUDE.md                             # Karpathy-style core principles & lifecycle table
├── README.md                             # Quick start instructions
└── .claude/
    ├── CLAUDE.md                         # Claude Code project instructions
    ├── skills/
    │   │   # Direct Path Skills
    │   ├── using-superpowers/SKILL.md    # Master skill gateway
    │   ├── brainstorming/SKILL.md        # 3 paths: Spike / Bounded / Architectural
    │   ├── writing-plans/SKILL.md        # Granular, testable implementation plans
    │   ├── subagent-driven-development/  # Plan orchestrator with specialized agents
    │   ├── executing-plans/SKILL.md      # Linear plan execution workflow
    │   ├── test-driven-development/      # Red -> Green -> Refactor cycle
    │   ├── frontend-vue/SKILL.md         # Strict Vue 3 + Vuetify + TypeScript rules
    │   ├── backend-python/SKILL.md       # Strict Python + FastAPI docstrings & layout
    │   ├── requesting-code-review/       # Dispatches code-reviewer agent
    │   ├── receiving-code-review/        # Ingests review feedback without excuses
    │   ├── verification-before-completion/ # Final test, ESLint, & type checks
    │   ├── finishing-a-development-branch/ # Git merge, rebase & cleanup
    │   │   # Side Skills (On-Demand)
    │   ├── systematic-debugging/SKILL.md # 4-phase root-cause isolation
    │   ├── using-git-worktrees/SKILL.md  # Isolated git worktrees
    │   ├── dispatching-parallel-agents/  # Concurrent subagents on disjoint tasks
    │   └── writing-skills/               # Complete reference suite for authoring skills
    └── agents/
        ├── frontend-specialist.md        # Senior Vue 3 / Vuetify subagent
        ├── backend-specialist.md         # Senior Python / FastAPI subagent
        └── code-reviewer.md              # Rigorous code reviewer enforcing all rules
```

---

## Installation / Copy-Paste

1. **Project-Level**: Copy `.claude/` and `CLAUDE.md` into your repository root:
   ```bash
   cp -r .claude/ /path/to/your/project/
   cp CLAUDE.md /path/to/your/project/
   ```

2. **Global User-Level**: Copy into `~/.claude/` to apply across all Claude Code sessions:
   ```bash
   cp -r .claude/* ~/.claude/
   ```

---

## Lifecycles & Skills Overview

### The Direct Path (Feature Pipeline)
1. **`using-superpowers`**: Routes requests and ensures skills are invoked before action.
2. **`brainstorming`**: Classifies scope into **Spike** (feasibility probe), **Bounded** (in-chat design for existing flows), or **Architectural** (written spec in `docs/specs/`).
3. **`writing-plans`**: Converts approved architectural specs into bite-sized TDD tasks in `docs/plans/`.
4. **`subagent-driven-development`**: Dispatches `frontend-specialist` or `backend-specialist` per task.
5. **`test-driven-development`**: Red $\rightarrow$ Green $\rightarrow$ Refactor cycle.
6. **`frontend-vue` / `backend-python`**: Domain conventions (script separation, no `any`, explicit checks, docstrings, section layouts).
7. **`requesting-code-review` / `receiving-code-review`**: Audits diffs with `code-reviewer` agent and applies fixes.
8. **`verification-before-completion`**: Executes automated tests, ESLint, and type checks.
9. **`finishing-a-development-branch`**: Merges cleanly to main and cleans up worktrees.

### Side Skills (On-Demand)
- **`systematic-debugging`**: Root-cause investigation protocol for bugs and test failures.
- **`using-git-worktrees`**: Branch isolation for parallel experiments.
- **`dispatching-parallel-agents`**: Orchestrating multiple disjoint subagents.
- **`writing-skills`**: Full authoring suite with test transcripts and best practice guides.
