# Cursor AI Rules

These rules guide AI behavior in this project to ensure high-quality, safe, and maintainable code.

---

## Core Principles

### 1. Think Before Coding

- **Read project documentation first** before making changes
- Review `memory.md`, `architecture.md`, and `decisions.md` to understand context
- Check `tasks.md` and `roadmap.md` to align with current priorities
- Ask clarifying questions if requirements are unclear or ambiguous

### 2. Plan Before Implementation

- Break down complex tasks into small, testable steps
- Propose an approach before writing code
- Identify affected files and potential side effects
- Consider edge cases and error handling upfront

### 3. Prefer Small, Safe Changes

- Make incremental changes that can be easily reviewed and tested
- Avoid large refactors without explicit approval
- Keep pull requests focused on a single concern
- Minimize the blast radius of each change

### 4. Never Break Existing Behavior

- Run existing tests before making changes
- Add tests for new functionality before implementation
- Verify that changes don't affect unrelated features
- Maintain backward compatibility unless explicitly breaking changes are requested

### 5. Follow Existing Patterns

- Match the existing code style and architecture
- Use established conventions in the codebase
- Reference similar implementations for consistency
- Don't introduce new patterns without discussion

### 6. Test-First Development

- Write tests before implementing features when possible
- Ensure new code has appropriate test coverage
- Update tests when modifying existing functionality
- Document test scenarios and edge cases

### 7. Update Project Memory

- Update `memory.md` after completing major changes
- Document architectural decisions in `decisions.md`
- Update `architecture.md` if system design changes
- Keep `tasks.md` current with completed and upcoming work

### 8. Clear Communication

- Explain the reasoning behind technical decisions
- Document non-obvious implementation details
- Provide clear commit messages and PR descriptions
- Flag potential risks or trade-offs

---

## Code Quality Standards

### Documentation

- Add comments for complex logic
- Document public APIs and interfaces
- Keep README and setup instructions current
- Explain "why" not just "what" in comments

### Error Handling

- Handle edge cases explicitly
- Provide meaningful error messages
- Log errors with sufficient context
- Fail gracefully with user-friendly feedback

### Security

- Validate all user input
- Follow security best practices for the stack
- Never commit secrets or credentials
- Review security implications of changes

### Performance

- Consider performance impact of changes
- Avoid premature optimization
- Profile before optimizing
- Document performance-critical sections

---

## Workflow Guidelines

### Before Starting Work

1. Read relevant documentation files
2. Understand the current state from `memory.md`
3. Check for related decisions in `decisions.md`
4. Review existing tests and code patterns

### During Development

1. Make small, incremental commits
2. Write tests alongside implementation
3. Run tests frequently
4. Keep changes focused and minimal

### Before Submitting

1. Run full test suite
2. Update documentation if needed
3. Update `memory.md` for significant changes
4. Write clear commit messages and PR descriptions

---

## When to Ask Questions

Ask for clarification when:

- Requirements are ambiguous or incomplete
- Multiple valid approaches exist with different trade-offs
- The change might affect other features or systems
- Breaking changes or major refactors are needed
- You're unsure about project conventions or patterns
- Security or performance implications are unclear

---

## Project-Specific Context

This project follows the conventions documented in:

- `coding-standards.md` - Language and style conventions
- `testing.md` - Testing philosophy and requirements
- `architecture.md` - System design and component relationships
- `api-contracts.md` - API design standards
- `deployment.md` - Deployment processes and environments

Always reference these files before making significant changes.
