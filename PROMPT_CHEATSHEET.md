# Prompt Cheat Sheet

Quick lookup for what each prompt does.

---

## General AI Prompts (`general-prompts/`)

| Prompt | What It Does |
|--------|--------------|
| **tcrei-template** | Structured prompt: Task → Context → Reference → Evaluate → Iterate |
| **master-framework** | Comprehensive structure: Context, Objective, Role, Constraints, Output |
| **prompt-engineer** | AI helps you write better prompts (meta-prompt) |
| **rage-mode** | No fluff. Ask 3 questions max, give 5 concrete steps |
| **speed-summary** | Summarize anything into 5 bullets + 1 "so what" |
| **systems-architect** | Design production systems with diagrams and tradeoffs |
| **startup-cofounder** | Validate ideas: problem, market, MVP, monetization, risks |
| **learning-accelerator** | Learn fast: ELI5 → professional → example → project → mistakes |
| **code-explainer** | Explain code like you're debugging it |
| **self-critique** | AI critiques and improves its own answer |
| **research-synthesizer** | Turn research into: findings, consensus, gaps, actions |

---

## Cursor Coding Prompts (`prompts/`)

| Prompt | What It Does |
|--------|--------------|
| **understand-codebase** | ⭐ **START HERE** - AI maps the repo before making changes |
| **repository-map** | Show folder structure and how components interact |
| **task-splitter** | Break big feature into small safe steps |
| **follow-project-rules** | Make AI follow your architecture.md and coding-standards.md |
| **update-memory** | Update memory.md after finishing work |
| **planning** | Plan feature: files to change, steps, risks |
| **debugging** | Systematic debugging: root cause first, then fix |
| **feature-dev** | Test-first development workflow |
| **testing** | Write comprehensive tests with coverage |
| **refactoring** | Safe refactoring without changing behavior |
| **pr-writing** | Write complete PR descriptions |

---

## Quick Workflows

**New codebase:**
```
understand-codebase → repository-map → start coding
```

**New feature:**
```
planning/task-splitter → feature-dev → pr-writing → update-memory
```

**Bug:**
```
debugging → fix → pr-writing
```

**Refactor:**
```
planning → refactoring → testing → pr-writing
```

---

**See `PROMPT_PLAYBOOK.md` for detailed usage and examples.**
