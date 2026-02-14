# Testing Prompt

Use this prompt when adding tests or improving test coverage.

---

## Prompt

```
I need to add tests for [COMPONENT/FEATURE].

Create comprehensive tests following this approach:

1. **Review Testing Standards**
   - Read @testing.md for project expectations
   - Check existing tests for patterns
   - Understand the testing framework and conventions

2. **Identify Test Cases**
   - Happy path scenarios
   - Edge cases and boundary conditions
   - Error conditions and invalid input
   - Integration points with other components
   - Performance or security considerations

3. **Write Tests**
   - Use descriptive test names that explain what's being tested
   - Follow Arrange-Act-Assert pattern
   - Keep tests independent and isolated
   - Use appropriate test doubles (mocks, stubs, fakes)
   - Ensure tests are deterministic and repeatable

4. **Coverage Analysis**
   - Verify all critical paths are tested
   - Check branch coverage for conditionals
   - Test error handling paths
   - Validate edge cases are covered

5. **Test Maintenance**
   - Keep tests simple and readable
   - Avoid testing implementation details
   - Make tests resilient to refactoring
   - Document complex test setup

Write the tests following these guidelines.
```

---

## Why This Works

- **Prevents regressions** by catching breaking changes
- **Documents behavior** through executable examples
- **Enables refactoring** with confidence
- **Catches bugs early** before production
- **Improves design** by making code testable

---

## When to Use

- Adding new features (test-first)
- Improving coverage for existing code
- Fixing bugs (write test that reproduces it)
- Refactoring (ensure tests pass before and after)
- Before making risky changes

---

## Test Quality Checklist

- [ ] Test names clearly describe what's being tested
- [ ] Tests are independent (can run in any order)
- [ ] Tests are fast and deterministic
- [ ] All edge cases are covered
- [ ] Error conditions are tested
- [ ] Tests follow project conventions
- [ ] Test code is clean and maintainable

---

## Common Test Types

**Unit Tests**: Test individual functions/methods in isolation
- Fast, focused, no external dependencies
- Use mocks for dependencies

**Integration Tests**: Test how components work together
- Verify interfaces and contracts
- May use real dependencies

**End-to-End Tests**: Test complete user workflows
- Slower but high confidence
- Test critical paths

Choose the right level based on what you're testing.
