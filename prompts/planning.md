# Planning Prompt

Use this prompt when starting work on a new feature or significant change.

---

## Prompt

```
I need to implement [FEATURE/CHANGE DESCRIPTION].

Before writing code:

1. Read relevant documentation:
   - @memory.md - What's been implemented
   - @architecture.md - System design
   - @decisions.md - Past technical decisions
   - @tasks.md - Current priorities

2. Create a plan that includes:
   - Files that need to be modified
   - New files that need to be created
   - Step-by-step implementation approach
   - Potential risks or side effects
   - Testing strategy

3. Identify:
   - Existing patterns to follow
   - Similar implementations in the codebase
   - Dependencies and affected components
   - Edge cases to handle

After reviewing, provide your implementation plan. Wait for approval before proceeding.
```

---

## Why This Works

- **Prevents rework** by ensuring alignment before coding
- **Reduces bugs** by identifying edge cases upfront
- **Maintains consistency** by referencing existing patterns
- **Enables better reviews** with clear scope and approach
- **Documents decisions** before they're implemented

---

## When to Use

- Starting a new feature
- Making architectural changes
- Working on unfamiliar code
- When requirements are complex
- Before significant refactoring
