# Prompt Evolution

How the prompt library grows and improves over time.

---

## Purpose

This document defines governance for the prompt library:
- Quality criteria for prompts
- Naming conventions
- When to create new vs update existing
- How to retire outdated prompts
- How to test prompts in real projects

**Goal**: Maintain a high-quality, focused prompt library that delivers consistent results.

---

## Prompt Quality Criteria

### What Makes a Good Prompt

A quality prompt should be:

**1. Specific and Actionable**
- ✅ "Create a plan including files to modify, step-by-step approach, and testing strategy"
- ❌ "Help me plan this feature"

**2. Context-Grounding**
- ✅ "Read architecture.md, coding-standards.md, and memory.md before proceeding"
- ❌ Assumes AI has context without explicit reference

**3. Format-Defining**
- ✅ "Return findings as: 1) Root cause, 2) Proposed fix, 3) Test to prevent regression"
- ❌ Leaves output format ambiguous

**4. Iterative and Testable**
- ✅ "First read X, then analyze Y, then propose Z"
- ❌ Single massive instruction that's hard to validate

**5. Failure-Aware**
- ✅ "If you can't find the relevant code, ask these clarifying questions..."
- ❌ No guidance on what to do when prompt conditions aren't met

### Quality Checklist

Before adding/updating a prompt, verify:

- [ ] **Clear objective**: What does this prompt accomplish?
- [ ] **Explicit context**: What docs/files should AI read first?
- [ ] **Structured output**: Is expected format/structure defined?
- [ ] **Examples provided**: Are there concrete examples?
- [ ] **Edge cases handled**: What if assumptions don't hold?
- [ ] **Tested in practice**: Has it been used in a real project?
- [ ] **Distinct from others**: Is it meaningfully different from existing prompts?
- [ ] **Concise**: Is every sentence necessary?

### Anti-Patterns

❌ **Mega-prompt syndrome**: One prompt that does everything
→ Split into focused prompts that can be chained

❌ **Vague instructions**: "Make it good", "Follow best practices"
→ Define specific, measurable criteria

❌ **Missing examples**: Abstract guidance without concrete illustration
→ Include at least one example of expected usage/output

❌ **No grounding**: Prompt doesn't reference project docs
→ Explicitly tell AI what to read first

❌ **Untested**: Prompt sounds good but hasn't been validated
→ Use in real project before adding to library

---

## Naming Conventions

### General AI Prompts (`general-prompts/`)

For prompts that work with any AI assistant (ChatGPT, Claude, etc.).

**Format**: `[purpose]-[type].md`

**Examples**:
- `tcrei-template.md` - Framework name
- `rage-mode.md` - Distinctive style descriptor
- `systems-architect.md` - Role-based prompt
- `learning-accelerator.md` - Purpose-focused
- `speed-summary.md` - Function-focused

**Rules**:
- Use lowercase with hyphens
- Keep names short (2-3 words)
- Make purpose clear from name
- Use descriptive terms, not jargon

---

### Cursor Development Prompts (`prompts/`)

For prompts specific to Cursor AI and coding workflows.

**Format**: `[action-or-phase].md`

**Examples**:
- `planning.md` - Development phase
- `feature-dev.md` - Specific action
- `debugging.md` - Specific action
- `refactoring.md` - Specific action
- `understand-codebase.md` - Specific action
- `pr-writing.md` - Specific action

**Rules**:
- Use lowercase with hyphens
- Prefer action verbs (debugging, planning, testing)
- Match developer mental model (what they're trying to do)
- Keep consistent with existing patterns

---

## Creating New Prompts

### When to Create a New Prompt

**Create a new prompt when**:
- Pattern emerges across 2-3 projects (not a one-off)
- No existing prompt covers this use case
- Existing prompts are too general for this specific need
- Combining existing prompts would be awkward

**Example**: After 3 projects need "database migration workflow", create `prompts/database-migration.md`

### When NOT to Create a New Prompt

**Don't create when**:
- Only used once (wait for pattern)
- Could enhance existing prompt instead
- Too project-specific to generalize
- Already covered by combining existing prompts

**Example**: Don't create "React testing prompt" if `prompts/testing.md` already works for all frameworks.

---

### New Prompt Template

```markdown
# [Prompt Name]

[One-sentence description of what this prompt accomplishes]

---

## When to Use This

Use this prompt when:
- [Scenario 1]
- [Scenario 2]
- [Scenario 3]

---

## The Prompt

```
[AI name or "AI Assistant"], [specific task instruction]

Before proceeding:
1. Read @[relevant-doc-1.md]
2. Read @[relevant-doc-2.md]
3. [Any other preparation]

[Main instruction with clear steps]

Output format:
1. [Section 1]
2. [Section 2]
3. [Section 3]

[Any additional guidance or constraints]
```

---

## Example

[Show concrete example of prompt in use]

Input:
```
[Example input]
```

Expected Output:
```
[Example output]
```

---

## Variations

**[Variation 1 Name]**: [Brief description and modification]

**[Variation 2 Name]**: [Brief description and modification]

---

## Tips

- [Tip 1]
- [Tip 2]
- [Tip 3]

---

**Last Updated**: [Date]
**Tested With**: [Cursor / ChatGPT / Claude / etc.]
```

---

### New Prompt Checklist

Before committing a new prompt:

- [ ] Validated in at least 1 real project
- [ ] Follows naming conventions
- [ ] Includes clear "When to Use" section
- [ ] Provides concrete example
- [ ] References relevant docs (@architecture.md style)
- [ ] Defines expected output format
- [ ] Includes usage tips
- [ ] Distinct from existing prompts (not duplicative)
- [ ] Added to PROMPT_PLAYBOOK.md
- [ ] Added to llms.txt with clear description
- [ ] Tested with target AI (Cursor, ChatGPT, etc.)

---

## Updating Existing Prompts

### When to Update

**Update a prompt when**:
- Users report it doesn't work as expected
- AI behavior has changed (new model)
- Better examples or clarity improvements identified
- Project retrospective reveals prompt gap
- Missing edge case handling

### Types of Updates

**Minor (non-breaking)**:
- Adding examples
- Clarifying instructions
- Adding tips section
- Fixing typos
- Adding variations

**Major (potentially breaking)**:
- Changing core instructions
- Restructuring output format
- Removing sections
- Changing objective

### Update Process

1. **Identify issue**: What isn't working?
2. **Propose fix**: How would you improve it?
3. **Test fix**: Validate in real project
4. **Review impact**: Would this break existing workflows?
5. **Update documentation**: Reflect changes in PROMPT_PLAYBOOK.md and llms.txt
6. **Version note**: Add "Last Updated" date and change description

**For major changes**:
- Consider creating new prompt instead (keep old for compatibility)
- Announce change in changelog
- Provide migration guidance if needed

---

## Retiring Prompts

### When to Retire

**Retire a prompt when**:
- No longer used (check with users first)
- Superseded by better prompt
- AI behavior changed and prompt no longer effective
- Consolidated into more comprehensive prompt

### Deprecation Process

**Don't delete immediately** - Use deprecation path:

1. **Mark deprecated** (keep file for 6+ months):
```markdown
# ⚠️ DEPRECATED: [Prompt Name]

**Status**: Deprecated as of [Date]
**Reason**: [Why deprecated]
**Alternative**: Use @prompts/[new-prompt].md instead

[Migration guidance if needed]

---

[Keep original prompt content for reference]
```

2. **Update references**:
- Mark as deprecated in PROMPT_PLAYBOOK.md
- Add deprecation note in llms.txt
- Update README if mentioned

3. **Announce deprecation**:
- Add to changelog
- Notify users if public library

4. **Remove after grace period**:
- After 6-12 months, safe to delete
- Keep record in git history

---

## Testing Prompts

### Testing Protocol

**Before adding prompt to library**:

1. **Solo validation** (1-2 uses):
   - Use in real work scenario
   - Observe AI response
   - Note deviations from expected behavior

2. **Revision** (if needed):
   - Refine based on first use
   - Clarify ambiguous instructions
   - Add missing context references

3. **Second validation** (1-2 more uses):
   - Test revised version
   - Confirm improvements
   - Note any remaining issues

4. **Ready for library**:
   - Works consistently across 2-3 uses
   - Produces expected output format
   - AI grounds itself properly

### Acceptance Criteria

A prompt is ready when:

- ✅ AI follows instructions consistently
- ✅ Output matches expected format
- ✅ AI references specified documentation
- ✅ Handles edge cases gracefully
- ✅ Works across 2-3 different scenarios
- ✅ Other users can apply it successfully

### Continuous Testing

**Ongoing validation**:
- Track which prompts are used frequently vs ignored
- Collect feedback from users
- Monitor for "prompt drift" (AI behavior changes over time)
- Retest after major AI model updates

---

## Versioning and Changelog

### Prompt Versioning

**Lightweight approach** (no formal versions):
- Track "Last Updated" date in each prompt
- Document major changes in repo changelog
- Use git history for detailed change tracking

**When formal versioning needed**:
- If prompts are used as API/integration points
- If backward compatibility is critical
- Use semantic versioning: major.minor.patch

### Changelog Format

In repo `CHANGELOG.md`:

```markdown
## [2.1.0] - 2026-02-15

### Prompts Added
- prompts/database-migration.md - Workflow for safe schema changes

### Prompts Updated
- prompts/debugging.md - Added log gathering checklist
- prompts/planning.md - Explicit testing.md reference

### Prompts Deprecated
- prompts/old-style-testing.md - Use prompts/testing.md instead

### Prompts Removed
- None
```

---

## Prompt Categories

Organize prompts into logical categories for discoverability:

### General AI Prompts

**Frameworks**: Structured prompt templates (TCREI, MASTER)
**Quick Formats**: Fast, focused prompts (Rage Mode, Speed Summary)
**Roles**: Specialized AI personas (Systems Architect, Code Explainer)
**Learning**: Educational prompts (Learning Accelerator, Research Synthesizer)

### Cursor Development Prompts

**Orientation**: First-time codebase exploration (Understand Codebase, Repository Map)
**Planning**: Pre-implementation workflows (Planning, Task Splitter)
**Development**: Active coding prompts (Feature Dev, Testing, Refactoring)
**Quality**: Code improvement (Debugging, PR Writing)
**Maintenance**: Post-implementation (Update Memory)

### When to Add New Category

Only if 3+ prompts share distinct characteristics not covered by existing categories.

---

## Maintenance Cadence

### Monthly
- [ ] Check for new prompt suggestions (issues, feedback)
- [ ] Quick review: are prompts still accurate?

### Quarterly
- [ ] Usage analysis: Which prompts are used? Which ignored?
- [ ] Test sample of prompts with current AI models
- [ ] Process any deprecation candidates
- [ ] Update examples if outdated

### After Major AI Model Updates
- [ ] Retest all prompts with new model
- [ ] Update prompts if behavior changed
- [ ] Document any new capabilities to leverage

---

## Prompt Library Health Metrics

### Good Signs

✅ Prompts used regularly in real projects
✅ Positive feedback / few revision requests
✅ New prompts emerge from validated patterns (not speculation)
✅ Clear gaps get filled quickly
✅ Deprecated prompts are actually replaced by better alternatives

### Warning Signs

⚠️ Many prompts never used (library bloat)
⚠️ Frequent complaints about prompt effectiveness
⚠️ New prompts added without real-world validation
⚠️ Duplicative prompts (should have updated existing)
⚠️ Prompts work in theory but fail in practice

---

## Getting Started

**To improve an existing prompt**:
1. Use it in real project and note issues
2. Draft improvements
3. Test revised version
4. Update prompt file
5. Update PROMPT_PLAYBOOK.md and llms.txt
6. Commit with clear description

**To create a new prompt**:
1. Validate pattern exists (used 2-3 times)
2. Draft prompt using template above
3. Test in real scenario
4. Refine based on results
5. Add to library following checklist
6. Update PROMPT_PLAYBOOK.md and llms.txt

**To retire a prompt**:
1. Mark as deprecated
2. Provide alternative
3. Update all references
4. Remove after grace period

---

**Last Updated**: February 2026
**Quality Standard**: All prompts tested in real projects before inclusion
**Review Frequency**: Quarterly with ongoing improvements
