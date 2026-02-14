# Refactoring Prompt

Use this prompt when improving code structure without changing behavior.

---

## Prompt

```
I need to refactor [CODE/COMPONENT] to [IMPROVEMENT GOAL].

Follow this safe refactoring process:

1. **Ensure Test Coverage**
   - Verify existing tests pass
   - Add tests if coverage is insufficient
   - Document current behavior through tests
   - Establish a safety net before changing code

2. **Plan the Refactoring**
   - Identify specific code smells or issues
   - Define the target structure
   - Break into small, safe steps
   - Identify potential risks

3. **Refactor Incrementally**
   - Make one small change at a time
   - Run tests after each change
   - Commit working states frequently
   - Never change behavior and structure simultaneously

4. **Common Refactoring Patterns**
   - Extract function/method
   - Rename for clarity
   - Remove duplication
   - Simplify conditional logic
   - Move code to better location
   - Extract interface or abstraction

5. **Verify and Document**
   - All tests still pass
   - Behavior is unchanged
   - Code is more maintainable
   - Update @decisions.md if architecture changed

Execute this refactoring following these safe steps.
```

---

## Why This Works

- **Safety first** with tests preventing regressions
- **Small steps** reduce risk and make review easier
- **Frequent commits** allow easy rollback if needed
- **No behavior changes** keeps the refactoring focused
- **Improved maintainability** without adding features

---

## When to Use

- Code is hard to understand or modify
- Duplication needs to be removed
- Preparing for new features
- Improving performance or security
- Simplifying complex logic
- After several bug fixes in the same area

---

## Refactoring Red Flags

Stop and reconsider if:

- Tests start failing unexpectedly
- The scope keeps growing
- You're changing behavior "while you're here"
- You can't easily explain the changes
- The diff is becoming too large

---

## Safe Refactoring Checklist

- [ ] Existing tests pass before starting
- [ ] Test coverage is adequate
- [ ] Each step is small and focused
- [ ] Tests pass after each step
- [ ] No behavior changes (tests prove this)
- [ ] Code is more maintainable after refactoring
- [ ] Changes are well-documented in commits

---

## Key Principles

**Red → Green → Refactor**
1. Write failing test (Red)
2. Make it pass (Green)
3. Improve the code (Refactor)

**Two Hats**
- Feature hat: Add functionality
- Refactoring hat: Improve structure

Never wear both hats at once!

**Boy Scout Rule**
Leave code cleaner than you found it, but in small increments.
