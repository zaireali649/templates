# Pull Request Writing Prompt

Use this prompt when preparing a pull request for review.

---

## Prompt

```
I need to create a pull request for [FEATURE/CHANGE].

Write a comprehensive PR description following this structure:

## Summary
[2-3 sentence overview of what changed and why]

## Changes
- [Bulleted list of key changes]
- [Focus on WHAT changed, not implementation details]
- [Group related changes together]

## Motivation
[Why was this change needed? What problem does it solve?]
[Reference issue numbers if applicable]

## Implementation Details
[Brief explanation of technical approach]
[Call out any non-obvious decisions]
[Mention alternatives considered if relevant]

## Testing
- [x] Unit tests added/updated
- [x] Integration tests pass
- [x] Manual testing performed
- [Describe specific test scenarios covered]

## Screenshots/Demos
[If UI changes, include before/after screenshots]
[If complex behavior, consider adding a video or GIF]

## Risks and Considerations
[Any potential breaking changes?]
[Performance implications?]
[Security considerations?]
[Deployment concerns?]

## Documentation Updates
- [x] Code comments added for complex logic
- [x] README updated (if applicable)
- [ ] API documentation updated (if applicable)
- [x] memory.md updated with significant changes

## Reviewer Notes
[Anything reviewers should pay special attention to?]
[Areas where you'd like specific feedback?]
[Known limitations or follow-up work needed?]

## Related Links
- Closes #[issue number]
- Related to #[issue number]
- Depends on #[PR number]
- Documentation: [link]
```

---

## Why This Works

- **Clear context** helps reviewers understand the change
- **Structured format** makes reviews faster and more thorough
- **Testing details** build confidence in the change
- **Risks section** prompts important discussions
- **Reviewer notes** guide the review process

---

## When to Use

- Before submitting any pull request
- When preparing code for review
- To document significant changes
- When changes need stakeholder approval

---

## PR Quality Checklist

- [ ] Title is clear and descriptive
- [ ] Summary explains what and why
- [ ] Changes are broken into reviewable commits
- [ ] Tests are included and passing
- [ ] Documentation is updated
- [ ] No unnecessary changes (formatting, whitespace)
- [ ] Risks and trade-offs are called out
- [ ] Screenshots included for UI changes
- [ ] Linked to relevant issues

---

## Writing Great Commit Messages

Each commit should have:

**Title**: 50 chars max, imperative mood
```
Add user authentication endpoint
Fix memory leak in data processor
Update API rate limiting logic
```

**Body**: Explain WHY, not what (code shows what)
```
The previous rate limiting was per-server, causing inconsistent
behavior in multi-server deployments. This change moves rate
limiting to Redis to ensure consistent limits across all servers.
```

---

## PR Size Guidelines

**Ideal**: 200-400 lines changed
**Maximum**: 1000 lines (larger PRs are harder to review)

If your PR is too large:
- Split into multiple PRs
- Use feature flags for partial work
- Create stacked PRs with dependencies

---

## Review Request Timing

Best times to request review:
- ✅ When all tests pass
- ✅ When you've self-reviewed the diff
- ✅ When documentation is updated
- ✅ When you'd be comfortable merging as-is

Don't request review:
- ❌ When you know there are issues
- ❌ When tests are failing
- ❌ When it's marked as WIP/Draft
- ❌ When major changes are still planned
