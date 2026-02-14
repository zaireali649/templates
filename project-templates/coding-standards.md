# Coding Standards

This document defines code style, conventions, and engineering standards for this project.

---

## General Principles

### Code Quality Values

1. **Readability First**: Code is read more than written
2. **Simplicity**: Simple solutions over clever ones
3. **Consistency**: Follow existing patterns
4. **Testability**: Design code to be easily tested
5. **Maintainability**: Future developers (including you) will thank you

### Boy Scout Rule

**Leave code cleaner than you found it.**

Make small improvements when you touch code, but keep changes focused.

---

## Language-Specific Standards

### [Primary Language - e.g., Python]

**Style Guide**: [e.g., PEP 8, Google Style Guide, Airbnb]

**Formatter**: [e.g., Black, Prettier, gofmt]

**Linter**: [e.g., pylint, ESLint, golangci-lint]

**Type Checking**: [e.g., mypy, TypeScript, Flow]

**Key conventions**:
- Indentation: [spaces/tabs, size]
- Line length: [e.g., 88 characters]
- Quotes: [single/double]
- Naming: [conventions for variables, functions, classes]

### [Secondary Language if applicable]

[Same structure as above]

---

## Naming Conventions

### General Guidelines

- Use descriptive, searchable names
- Avoid abbreviations unless universally understood
- Be consistent across the codebase
- Make names pronounceable

### Variables

**Format**: [e.g., snake_case, camelCase]

**Examples**:
- ✅ `user_count`, `total_price`, `is_active`
- ❌ `uc`, `tp`, `flg`

**Booleans**: Use positive names with `is_`, `has_`, `can_`, `should_`
- ✅ `is_valid`, `has_permission`, `can_edit`
- ❌ `not_invalid`, `lacks_permission`

### Functions

**Format**: [e.g., snake_case, camelCase]

**Convention**: Use verb or verb phrases
- ✅ `calculate_total()`, `get_user()`, `send_email()`
- ❌ `total()`, `user()`, `email()`

### Classes

**Format**: [e.g., PascalCase, CapWords]

**Convention**: Use nouns or noun phrases
- ✅ `UserManager`, `EmailService`, `PaymentProcessor`
- ❌ `DoUserStuff`, `HandleEmail`

### Constants

**Format**: [e.g., UPPER_SNAKE_CASE]

**Examples**:
- ✅ `MAX_RETRIES`, `DEFAULT_TIMEOUT`, `API_BASE_URL`

### Files and Modules

**Format**: [e.g., lowercase with underscores, kebab-case]

**Convention**: Match primary class/function name
- ✅ `user_manager.py`, `email-service.js`
- ❌ `um.py`, `service.js`

---

## Code Organization

### File Structure

**Recommended order**:
1. Module docstring/header comments
2. Imports (standard library, third-party, local)
3. Constants
4. Helper functions
5. Main classes/functions
6. Script/execution code (if applicable)

### Import Standards

**Order**:
1. Standard library imports
2. Third-party library imports
3. Local application imports

**Style**:
- ✅ One import per line
- ✅ Sort alphabetically within groups
- ❌ Avoid wildcard imports (`from module import *`)

**Example**:
```
[Language-specific import example showing proper grouping]
```

### Project Structure

```
project/
├── src/                   # Source code
│   ├── api/              # API routes/endpoints
│   ├── models/           # Data models
│   ├── services/         # Business logic
│   ├── utils/            # Utility functions
│   └── config/           # Configuration
├── tests/                # Test files (mirror src structure)
├── docs/                 # Documentation
├── scripts/              # Utility scripts
└── [config files]        # Package.json, requirements.txt, etc.
```

---

## Functions and Methods

### Function Length

**Guideline**: Keep functions short and focused

**Target**: < 30 lines (excluding docstring/comments)

**Why**: Easier to understand, test, and maintain

### Function Complexity

**Cyclomatic Complexity**: Keep < 10

**If a function is too complex**:
- Extract helper functions
- Simplify conditional logic
- Consider refactoring

### Parameters

**Maximum parameters**: 3-4 (consider passing an object if more)

**Parameter order**: Required first, optional last

**Named parameters**: Use for boolean flags or optional parameters

### Return Values

**Be consistent**: Same function should return same type

**Early returns**: Use for guard clauses and error conditions

**Avoid**: Returning null/None when possible (use exceptions or optional types)

---

## Comments and Documentation

### When to Comment

**Good reasons**:
- Explain WHY, not WHAT (code shows what)
- Document non-obvious behavior
- Warn about gotchas or edge cases
- Link to external resources (tickets, docs)
- TODO comments (with owner and date)

**Bad reasons**:
- Explaining obvious code
- Commenting instead of refactoring
- Keeping old code commented out

### Comment Style

**Function/method documentation**:
```
[Language-specific docstring example with parameters, returns, raises]
```

**Inline comments**:
- Use sparingly
- Place on line above code (not at end of line)
- Complete sentences with proper punctuation

### TODOs and FIXMEs

**Format**: `TODO(username): Description of what needs doing`

**Examples**:
```
# TODO(john): Add input validation
# FIXME(jane): This breaks with empty arrays
# HACK(bob): Temporary workaround for API limitation
```

**Guidelines**:
- Create issue for important TODOs
- Include issue number: `TODO(#123): Fix user caching`
- Don't let TODOs accumulate indefinitely

---

## Error Handling

### Exceptions vs Error Codes

**Prefer exceptions** for exceptional conditions

**Use error codes/results** for expected alternative outcomes

### Exception Guidelines

**Do**:
- Use specific exception types
- Provide helpful error messages
- Include relevant context
- Document exceptions in docstrings

**Don't**:
- Catch generic exceptions without re-raising
- Use exceptions for flow control
- Swallow exceptions silently

### Example

```
[Language-specific error handling example]
```

### Logging Errors

**Always log**:
- Exception type and message
- Stack trace
- Request context (user, endpoint)
- Input that caused error

**Log levels**:
- ERROR: Something failed
- WARN: Something suspicious
- INFO: Significant events
- DEBUG: Detailed diagnostic info

---

## Testing Standards

See `testing.md` for comprehensive testing guidelines.

**Quick standards**:
- Write tests for all new code
- Maintain > 80% coverage
- Follow AAA pattern (Arrange-Act-Assert)
- Use descriptive test names
- Keep tests independent

---

## Security Practices

### Input Validation

**Always validate**:
- User input
- External API responses
- File uploads
- Query parameters

**Sanitize**:
- HTML/SQL injection prevention
- Command injection prevention
- Path traversal prevention

### Authentication and Authorization

**Never**:
- Store passwords in plain text
- Log sensitive data
- Trust client-side validation alone
- Hard-code credentials

**Always**:
- Use bcrypt/scrypt for passwords
- Validate permissions on server
- Use HTTPS for all requests
- Follow principle of least privilege

### Secrets Management

**Storage**: [e.g., Environment variables, AWS Secrets Manager, HashiCorp Vault]

**Never commit**:
- API keys
- Passwords
- Private keys
- Tokens

**Use**: `.gitignore` to exclude secret files

---

## Performance Guidelines

### General Rules

**Don't**:
- Premature optimization
- Optimize without profiling
- Trade readability for micro-optimizations

**Do**:
- Use appropriate data structures
- Avoid N+1 queries
- Cache expensive operations
- Lazy load when appropriate

### Database Queries

**Best practices**:
- Select only needed columns
- Use indexes on query columns
- Batch operations when possible
- Avoid queries in loops

### API Calls

**Best practices**:
- Batch requests when possible
- Cache responses appropriately
- Use pagination for large datasets
- Implement timeouts

---

## Code Review Standards

### What to Look For

**Functionality**:
- [ ] Does it work as intended?
- [ ] Are edge cases handled?
- [ ] Is error handling appropriate?

**Code Quality**:
- [ ] Is it readable and clear?
- [ ] Are names descriptive?
- [ ] Is it well-structured?
- [ ] Does it follow conventions?

**Testing**:
- [ ] Are there tests?
- [ ] Do tests cover edge cases?
- [ ] Is coverage maintained?

**Security**:
- [ ] Is input validated?
- [ ] Are there security risks?
- [ ] Are secrets handled properly?

**Performance**:
- [ ] Are there obvious bottlenecks?
- [ ] Is it efficient enough?

### Giving Feedback

**Be**:
- Constructive and specific
- Respectful and kind
- Focused on code, not person

**Format**: "Consider [suggestion] because [reason]"

**Examples**:
- ✅ "Consider extracting this into a helper function to improve testability"
- ❌ "This is bad"

### Receiving Feedback

**Be**:
- Open to suggestions
- Willing to discuss
- Grateful for the review

**Remember**: Reviews improve code quality and spread knowledge

---

## Git Practices

### Branch Naming

**Format**: `[type]/[short-description]`

**Types**:
- `feature/` - New features
- `fix/` - Bug fixes
- `refactor/` - Code improvements
- `docs/` - Documentation
- `test/` - Test additions

**Examples**:
- `feature/user-authentication`
- `fix/payment-validation`
- `refactor/database-queries`

### Commit Messages

**Format**:
```
[Type]: Short description (50 chars)

Longer explanation if needed (wrap at 72 chars).
- What changed and why
- Reference issues: Fixes #123

```

**Types**: feat, fix, docs, refactor, test, chore

**Examples**:
- `feat: Add user email verification`
- `fix: Resolve race condition in payment processing`
- `refactor: Extract duplicate validation logic`

### Pull Requests

See `prompts/pr-writing.md` for detailed PR guidelines.

**Requirements**:
- Clear title and description
- Tests included
- Documentation updated
- All checks passing
- Requested reviews addressed

---

## Dependencies

### Adding Dependencies

**Before adding**:
1. Is it necessary?
2. Is it actively maintained?
3. What are the licensing implications?
4. What's the size/performance impact?
5. Are there better alternatives?

**Document**: Add comment explaining why dependency is needed

### Updating Dependencies

**Frequency**: [e.g., Monthly, quarterly]

**Process**:
1. Review changelog
2. Check for breaking changes
3. Update and test
4. Document any changes needed

### Dependency Hygiene

**Regularly**:
- Review unused dependencies
- Update to latest secure versions
- Check for security vulnerabilities

**Tools**: [e.g., npm audit, pip-audit, Dependabot]

---

## Anti-Patterns to Avoid

### Code Smells

**Avoid**:
- God classes (classes that do too much)
- Long methods (> 30 lines)
- Deep nesting (> 3 levels)
- Duplicate code
- Magic numbers (use named constants)
- Tight coupling

### Bad Practices

**Don't**:
- Copy-paste code (extract shared logic)
- Commit commented-out code
- Leave TODO comments indefinitely
- Skip error handling
- Ignore linter warnings

---

## Configuration

### Linter Configuration

**Files**: [e.g., `.eslintrc`, `pyproject.toml`, `.golangci.yml`]

**Run locally**: `[command to run linter]`

**Auto-fix**: `[command to auto-fix issues]`

### Formatter Configuration

**Files**: [e.g., `.prettierrc`, `pyproject.toml`]

**Format on save**: Recommended in IDE settings

**Command**: `[command to format code]`

### Pre-commit Hooks

**Setup**: `[command to install hooks]`

**What runs**:
- Code formatting
- Linting
- Type checking
- Fast tests

---

## IDE Setup

### Recommended Extensions

**[Your IDE - e.g., VSCode]**:
- [Extension 1] - [Purpose]
- [Extension 2] - [Purpose]
- [Extension 3] - [Purpose]

### Settings

**Recommended IDE settings**:
```json
[Include IDE settings snippet]
```

---

## Resources

- **Style Guide**: [Link to official language style guide]
- **Linter Docs**: [Link to linter documentation]
- **Team Wiki**: [Link to internal documentation]
- **Examples**: [Link to example code in repo]

---

**Last Updated**: [YYYY-MM-DD]

**Linter Version**: [Version]

**Formatter Version**: [Version]
