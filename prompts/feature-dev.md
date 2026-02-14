# Feature Development Prompt

Use this prompt when implementing a new feature or enhancement.

---

## Prompt

```
I need to implement: [FEATURE DESCRIPTION]

Follow this workflow:

1. **Context Gathering**
   - Read @architecture.md to understand where this fits
   - Check @coding-standards.md for conventions
   - Review @api-contracts.md if building APIs
   - Look at similar features for patterns

2. **Write Tests First**
   - Define acceptance criteria
   - Write failing tests that describe desired behavior
   - Include edge cases and error scenarios
   - Reference @testing.md for standards

3. **Implement Incrementally**
   - Start with the simplest case
   - Make tests pass one at a time
   - Keep each commit small and focused
   - Follow existing patterns in the codebase

4. **Verify Quality**
   - All tests pass (including existing tests)
   - Code follows project standards
   - Error handling is complete
   - Performance is acceptable

5. **Document**
   - Update relevant documentation
   - Add code comments for complex logic
   - Update @memory.md with what was built
   - Note any decisions in @decisions.md

Implement this feature following these steps.
```

---

## Why This Works

- **Test-first** ensures clear requirements and prevents regressions
- **Incremental approach** makes changes easier to review
- **Pattern consistency** improves maintainability
- **Quality checks** catch issues early
- **Documentation** helps future developers

---

## When to Use

- Building new features
- Adding enhancements to existing features
- Implementing user stories
- Developing new components
- Extending functionality

---

## Checklist

Before marking the feature complete:

- [ ] All acceptance criteria met
- [ ] Tests written and passing
- [ ] Follows coding standards
- [ ] Error handling implemented
- [ ] Documentation updated
- [ ] No regressions in existing features
- [ ] Ready for code review
