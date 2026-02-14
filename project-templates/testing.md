# Testing

This document defines the testing philosophy, standards, and practices for this project.

---

## Testing Philosophy

**Core Belief**: [e.g., "Tests are a safety net that enables confident refactoring and rapid feature development"]

**Testing Goals**:
1. Prevent regressions
2. Document expected behavior
3. Enable safe refactoring
4. Catch bugs before production
5. Provide fast feedback during development

---

## Testing Pyramid

```
       /\
      /  \     E2E Tests (Few)
     /____\    - Critical user flows
    /      \   - Highest confidence
   /        \  - Slowest, most brittle
  /__________\ 

     /\
    /  \       Integration Tests (Some)
   /    \      - Component interactions
  /      \     - API contracts
 /        \    - Database operations
/__________\   

    /\
   /  \         Unit Tests (Many)
  /    \        - Business logic
 /      \       - Utilities
/        \      - Fast and focused
/__________\    
```

**Distribution Target**:
- **Unit Tests**: 70-80% of tests
- **Integration Tests**: 15-25% of tests
- **E2E Tests**: 5-10% of tests

---

## Test Coverage Standards

### Minimum Coverage Requirements

- **Overall Coverage**: [e.g., 80%]
- **Critical Paths**: [e.g., 100%]
- **Business Logic**: [e.g., 90%]
- **Utilities**: [e.g., 85%]

### What Must Be Tested

**Always test**:
- Business logic and calculations
- Data transformations
- API endpoints
- Authentication and authorization
- Payment processing
- Data validation
- Error handling

**Test when complex**:
- UI components with state or logic
- Integration points
- Configuration management

**Don't test** (or test sparingly):
- Third-party libraries
- Trivial getters/setters
- Generated code
- Framework boilerplate

---

## Unit Testing

### Standards

**Characteristics**:
- Fast (< 1ms per test)
- Isolated (no external dependencies)
- Deterministic (same input = same output)
- Independent (can run in any order)

**Structure**: Follow Arrange-Act-Assert (AAA)

```
// Arrange: Set up test data and conditions
const input = createTestInput();

// Act: Execute the code under test
const result = functionUnderTest(input);

// Assert: Verify the outcome
expect(result).toBe(expectedValue);
```

### Naming Convention

**Pattern**: `test[MethodName]_[Scenario]_[ExpectedBehavior]`

**Examples**:
- `testCalculateTotal_WithDiscount_ReturnsDiscountedPrice`
- `testValidateEmail_InvalidFormat_ThrowsValidationError`
- `testGetUser_UserNotFound_ReturnsNull`

Or use descriptive sentences:
- `it("calculates total with discount correctly")`
- `it("throws validation error for invalid email")`
- `it("returns null when user not found")`

### Mocking Strategy

**When to mock**:
- External services (APIs, databases)
- File system operations
- Time-dependent operations
- Expensive computations

**Mocking tools**: [e.g., Jest, Mockito, unittest.mock]

**Example**:
```
[Include language-specific mocking example]
```

---

## Integration Testing

### Standards

**Purpose**: Verify that components work together correctly

**What to test**:
- Database interactions
- API endpoints end-to-end
- Message queue processing
- File I/O operations
- Third-party integrations (with test accounts)

**Test environment**:
- Use test database (not production!)
- Seed with test data
- Clean up after tests
- Isolate from other test runs

### API Testing

**Test each endpoint for**:
- ✅ Happy path (valid input → success)
- ✅ Validation errors (invalid input → 400)
- ✅ Authentication (no auth → 401)
- ✅ Authorization (wrong user → 403)
- ✅ Not found (missing resource → 404)
- ✅ Server errors (edge cases → 500)

**Example**:
```
[Include API test example for your stack]
```

---

## End-to-End (E2E) Testing

### Standards

**Purpose**: Test critical user workflows from UI to database

**What to test** (only critical paths):
- User registration and login
- Core feature workflows
- Payment processing
- Critical business processes

**Tools**: [e.g., Playwright, Cypress, Selenium]

**Best practices**:
- Use stable selectors (data-testid, not CSS classes)
- Make tests resilient to UI changes
- Run against staging environment
- Keep tests focused and minimal

### Example E2E Test

```
[Include E2E test example]
```

---

## Test Data Management

### Test Fixtures

**Location**: `tests/fixtures/` or similar

**Guidelines**:
- Use realistic but minimal data
- Make fixtures reusable
- Document fixture purpose
- Version control fixtures

### Database Seeding

**Approach**: [e.g., Run migrations + seed script for each test suite]

**Cleanup**: [e.g., Rollback transactions after each test]

### Factories and Builders

**Pattern**: Use factories to generate test data

**Example**:
```
[Include factory example for your stack]
```

---

## Running Tests

### Local Development

**Run all tests**:
```bash
[command to run all tests]
```

**Run specific test file**:
```bash
[command to run single test file]
```

**Run with coverage**:
```bash
[command to run tests with coverage report]
```

**Watch mode** (for TDD):
```bash
[command to run tests in watch mode]
```

### CI/CD Pipeline

**When tests run**:
- On every pull request
- Before merge to main
- Before deployment

**Test stages**:
1. Lint and format checks
2. Unit tests (fast, parallel)
3. Integration tests
4. E2E tests (critical paths only)

**Failure policy**: [e.g., "Any test failure blocks deployment"]

---

## Test-Driven Development (TDD)

### Red-Green-Refactor Cycle

1. **Red**: Write a failing test
2. **Green**: Write minimal code to pass
3. **Refactor**: Improve code while keeping tests green

### When to Use TDD

**Good candidates for TDD**:
- Business logic with clear requirements
- Bug fixes (write test that reproduces bug)
- Algorithms and calculations
- API endpoints

**Less suitable for TDD**:
- Exploratory work
- UI/UX experimentation
- Prototypes and spikes

---

## Continuous Testing Practices

### Pre-commit Checks

Run automatically before commit:
- [ ] Lint
- [ ] Format check
- [ ] Unit tests (fast subset)

### Pre-push Checks

Run automatically before push:
- [ ] All unit tests
- [ ] Integration tests
- [ ] Coverage check

### Pull Request Checks

Run automatically on PR:
- [ ] All tests
- [ ] Coverage report
- [ ] Security scans
- [ ] E2E tests (critical paths)

---

## Testing Tools and Frameworks

### Test Framework
**Tool**: [e.g., Jest, pytest, JUnit, Go testing]

**Why**: [Reason for choice]

### Assertion Library
**Tool**: [e.g., expect, assert, Hamcrest]

### Mocking
**Tool**: [e.g., Jest mocks, unittest.mock, Mockito]

### E2E Testing
**Tool**: [e.g., Playwright, Cypress]

### Code Coverage
**Tool**: [e.g., Istanbul, Coverage.py, JaCoCo]

**Reporting**: [Where coverage reports are viewed]

---

## Performance Testing

### Load Testing

**When**: [e.g., Before major releases, after performance-critical changes]

**Tools**: [e.g., k6, JMeter, Locust]

**Scenarios**:
- [Scenario 1: Normal load]
- [Scenario 2: Peak load]
- [Scenario 3: Stress test]

### Benchmarking

**Critical paths to benchmark**:
- [API endpoint or function]
- [Another performance-critical operation]

**Acceptance criteria**:
- [e.g., "API response time < 200ms at p95"]
- [e.g., "Database queries < 50ms"]

---

## Security Testing

### Automated Security Scans

**Tools**: [e.g., Snyk, OWASP Dependency Check]

**Frequency**: [e.g., On every PR, daily]

### Security Test Cases

- [ ] SQL injection prevention
- [ ] XSS prevention
- [ ] CSRF protection
- [ ] Authentication bypass attempts
- [ ] Authorization checks
- [ ] Input validation
- [ ] Secrets not exposed

---

## Flaky Tests

### Prevention

- Avoid time-dependent assertions
- Use deterministic test data
- Properly clean up between tests
- Don't depend on test execution order
- Handle async operations correctly

### Dealing with Flaky Tests

1. **Document**: Mark flaky test in issue tracker
2. **Investigate**: Find root cause
3. **Fix or Disable**: Either fix properly or temporarily disable
4. **Don't Ignore**: Flaky tests erode confidence

---

## Test Maintenance

### When to Update Tests

- When behavior changes (expected)
- When tests are brittle (refactor tests)
- When coverage drops (add tests)
- When tests are slow (optimize)

### Deleting Tests

Delete tests when:
- Feature is removed
- Test is redundant
- Test provides no value

**Don't** delete tests because:
- They're failing (fix them)
- They're slow (optimize them)
- They're annoying (that's the point!)

---

## Testing Checklist

### For Every Feature

- [ ] Unit tests for business logic
- [ ] Integration tests for API/database
- [ ] Edge cases covered
- [ ] Error cases tested
- [ ] Documentation updated

### For Every Bug Fix

- [ ] Test that reproduces the bug
- [ ] Test passes after fix
- [ ] Related edge cases considered
- [ ] Root cause documented

### Before Release

- [ ] All tests passing
- [ ] Coverage meets requirements
- [ ] E2E tests for critical paths run
- [ ] Performance tests pass
- [ ] Security scans clean

---

## Common Testing Patterns

### [Pattern Name 1]

**Use case**: [When to use this pattern]

**Example**:
```
[Code example]
```

---

### [Pattern Name 2]

[Same structure]

---

## Troubleshooting Test Failures

### Test Fails Locally

1. Check if dependencies are up to date
2. Verify environment configuration
3. Check for leftover state from previous tests
4. Run single test in isolation

### Test Fails in CI Only

1. Check for environment differences
2. Look for timing/race conditions
3. Verify test data seeding
4. Check CI logs for clues

### All Tests Suddenly Fail

1. Check for infrastructure issues
2. Verify database/service availability
3. Check for breaking changes in dependencies
4. Review recent commits

---

## Resources and References

- **Testing Guidelines**: [Link to team wiki or docs]
- **Test Examples**: `tests/examples/`
- **Coverage Reports**: [Link to coverage dashboard]
- **CI Pipeline**: [Link to CI configuration]

---

**Last Updated**: [YYYY-MM-DD]

**Test Coverage**: [Current %]

**Test Count**: [Current numbers by type]
