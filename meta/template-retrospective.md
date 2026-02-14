# Template Retrospective

A repeatable process for improving templates after finishing projects.

---

## Purpose

After completing a project (or major milestone), run this retrospective to:
- Identify what worked and what didn't
- Surface prompt failures and template gaps
- Convert lessons learned into template improvements
- Decide whether to update prompts, templates, or rules

**Run this retrospective**: End of projects, major milestones, incidents, or quarterly reviews.

---

## Retrospective Setup

### When to Run

**Required**:
- End of project (before final handoff)
- After major architectural changes
- Post-incident (production issues or major bugs)
- Quarterly (even if project ongoing)

**Optional**:
- End of sprint (for rapid iteration)
- After onboarding new team members (capture friction)
- When templates felt particularly helpful or unhelpful

### Participants

**Minimum**:
- Lead developer who used the templates
- Anyone who interacted with AI coding assistant

**Ideal**:
- Whole team (2-5 people)
- Template maintainer (if different person)
- Product/design if relevant to prompts used

### Time Box

- **Quick retro**: 30 minutes (minimal)
- **Standard retro**: 1 hour (recommended)
- **Deep retro**: 2 hours (post-major project or incident)

### Materials to Gather

**Before the meeting**:
- [ ] Git log (last 3-6 months or since project start)
- [ ] Pull requests and PR descriptions
- [ ] Issues/tickets closed
- [ ] Memory.md entries from the project
- [ ] Any prompt transcripts saved (Cursor history, ChatGPT exports)
- [ ] Template files that were customized

---

## Retrospective Questions

### Part 1: What Worked (15 min)

**Prompts**:
1. Which prompts did you use most frequently?
2. Which prompts saved the most time?
3. Which prompts gave consistently good results?
4. Were there any "aha moments" where a prompt or template prevented a mistake?

**Templates**:
1. Which template files were most valuable?
2. Which sections of templates did you reference most?
3. Did AI ground itself in documentation effectively?
4. Which templates evolved most naturally with the project?

**Rules**:
1. Did Cursor AI follow project rules consistently?
2. Which rules had the most positive impact?
3. Were there behaviors you expected but didn't get?

**Capture**: Note 3-5 things that worked well and should be preserved/enhanced.

---

### Part 2: What Didn't Work (20 min)

#### Prompt Failures

**Questions**:
1. Which prompts gave poor results or required heavy editing?
2. Were there tasks you needed prompts for but didn't have?
3. Did any prompts work in theory but fail in practice?
4. Were prompt instructions clear or did they require interpretation?

**Symptom catalog**:
- Prompt too vague → AI gave generic solutions
- Prompt too specific → AI couldn't adapt to project context
- Prompt missing context → AI didn't reference relevant docs
- Prompt unclear on format → Output required reformatting
- Prompt missing examples → AI didn't understand expectations

#### Template Gaps

**Questions**:
1. Which template sections were always modified the same way?
2. Were there sections you consistently deleted as "not applicable"?
3. Did you create custom sections that should be in the template?
4. Were placeholders clear or confusing?
5. Were there cross-references missing?

**Gap types**:
- Missing section (needed but not in template)
- Wrong granularity (too detailed or too high-level)
- Confusing placeholder (unclear what to fill in)
- Stale guidance (doesn't match current practices)
- Missing examples (hard to know what good looks like)

#### Rule Ineffectiveness

**Questions**:
1. Did AI ignore any rules consistently?
2. Were there rules that conflicted with each other?
3. Were rules specific enough to change behavior?
4. Did you wish AI would do something but no rule covered it?

**Capture**: Note 5-10 specific friction points with context.

---

### Part 3: Missing Context (15 min)

**Questions**:
1. What context did AI frequently miss that would have improved suggestions?
2. Were there architectural patterns not documented in `architecture.md`?
3. Did `memory.md` capture important history or miss key context?
4. Were coding standards clear enough in `coding-standards.md`?
5. Would additional templates have helped? (Examples: API versioning, feature flags, migrations)

**Common gaps**:
- Performance requirements not documented
- Security constraints not explicit
- API design patterns not captured
- Testing strategies not defined
- Deployment constraints not clear

**Capture**: List context that existed in people's heads but not in documentation.

---

### Part 4: Template Customizations (10 min)

Review the actual template files used in the project:

**For each template**:
1. What sections were added?
2. What sections were deleted?
3. What placeholders were confusing?
4. How did the file evolve over the project?

**Example review** - `architecture.md`:
- ✅ Kept: All core sections
- ➕ Added: "Feature Flags" section (repeated pattern)
- ➖ Deleted: "Disaster Recovery" (overkill for MVP)
- 🤔 Modified: "Core Components" format changed to include database tables

**Capture**: Patterns in how templates were customized.

---

## Analysis: Root Cause → Improvement Type

### Decision Matrix

| Root Cause | Symptom | Improvement Type | Action |
|------------|---------|------------------|--------|
| Prompt too vague | AI gives generic answers | Enhance prompt | Add specific context instructions, examples |
| Prompt missing context reference | AI ignores standards | Enhance prompt | Add explicit "@architecture.md" style references |
| Template section always modified same way | Repeated manual edits | Update template | Add/modify section in template |
| Template section always deleted | Clutter, not useful | Make optional | Move to separate specialized template |
| Placeholder confusing | Unclear what to fill in | Improve template | Add inline guidance or example |
| Missing template | Created custom file repeatedly | Create new template | Add to project-templates/ if generalizable |
| Rule ignored by AI | Unexpected behavior | Enhance rule | Make more specific, add examples |
| Rule unclear | Inconsistent application | Clarify rule | Rewrite with concrete guidance |
| Missing rule | AI behavior not aligned | Add rule | Define expected behavior explicitly |
| Context not documented | AI makes wrong assumptions | Update docs | Add to architecture.md, memory.md, etc. |

### Categorizing Improvements

**High Priority** (do immediately):
- Prompts that consistently failed
- Templates with critical missing sections
- Rules that AI ignores frequently

**Medium Priority** (do this quarter):
- Templates sections that are often customized
- Prompts that need examples or clarification
- Documentation gaps that caused confusion

**Low Priority** (backlog):
- Nice-to-have template enhancements
- Edge case coverage
- Specialized variants for niche use cases

---

## Output Artifacts

### 1. Improvements Queue

Create structured list of proposed changes:

```markdown
## Template Retrospective - [PROJECT_NAME] - [DATE]

### Prompts to Update
- **prompts/planning.md**: Add explicit step to reference testing.md
  - Why: AI skipped test planning in 3/5 features
  - Priority: High

- **prompts/debugging.md**: Add checklist for gathering logs
  - Why: Debugging session wasted 30 min looking for log location
  - Priority: Medium

### Templates to Enhance
- **project-templates/architecture.md**: Add "Feature Flags" section
  - Why: Every project now uses feature flags, should be documented
  - Priority: High

- **project-templates/api-contracts.md**: Add webhook security example
  - Why: Implemented webhooks, template had no guidance on signature verification
  - Priority: Medium

### Rules to Add/Modify
- **cursor/rules.md**: Add rule about checking api-contracts.md before API changes
  - Why: AI suggested endpoint structure that violated our REST conventions
  - Priority: High

### New Templates to Create
- **project-templates/feature-flags.md**: Document feature flag strategy
  - Why: Pattern repeated across 3 features, should be templated
  - Priority: Medium

### Documentation Gaps
- **memory.md**: Missing performance baseline notes
  - Why: AI couldn't assess if change impacted performance
  - Priority: Low
```

### 2. Validation Plan

For each high-priority improvement:

```markdown
## Validation Plan

### Improvement: Add "Feature Flags" section to architecture.md

**Hypothesis**: Documenting feature flag patterns will help AI suggest consistent implementations

**Test**:
1. Add section to architecture.md template
2. Copy updated template to test project
3. Ask AI to implement feature flag for new feature
4. Evaluate: Does AI follow documented pattern?

**Success Criteria**:
- AI references feature flag documentation
- AI suggests implementation matching documented pattern
- No need for manual correction

**Timeline**: Test in next project start (within 2 weeks)
```

### 3. Changes Committed

After validation, commit improvements:

```markdown
## Changes from [PROJECT_NAME] Retrospective - [DATE]

**Prompts Updated**:
- ✅ prompts/planning.md - Added testing.md reference
- ✅ prompts/debugging.md - Added log gathering checklist

**Templates Enhanced**:
- ✅ project-templates/architecture.md - Added "Feature Flags" section
- ✅ project-templates/api-contracts.md - Added webhook security example

**Rules Modified**:
- ✅ cursor/rules.md - Added API contract validation rule

**New Templates**:
- ✅ project-templates/feature-flags.md - Created new template

**llms.txt Updated**: ✅
**README Updated**: ✅ (for new template)
**Version Bumped**: 2.2.0
**Changelog Updated**: ✅
```

---

## Retrospective Formats

### Quick Format (30 min)

1. **Wins** (5 min): 3 things that worked
2. **Friction** (15 min): 5-7 things that didn't work
3. **Action items** (10 min): 2-3 high-priority improvements to queue

### Standard Format (1 hour)

1. **Wins** (15 min): What worked (prompts, templates, rules)
2. **Friction** (20 min): What didn't work (failures, gaps, confusion)
3. **Root cause** (15 min): Why things didn't work
4. **Improvements** (10 min): Specific changes to make

### Deep Format (2 hours)

1. **Context** (15 min): Project overview and template usage patterns
2. **Wins** (20 min): Detailed review of what worked
3. **Friction** (30 min): Comprehensive friction point analysis
4. **Root cause** (20 min): Map symptoms to root causes
5. **Prioritization** (20 min): Rank improvements by impact
6. **Validation plan** (15 min): How to test proposed changes

---

## Templates for Common Scenarios

### Post-MVP Retrospective

**Focus on**:
- Was initial setup (bootstrap process) smooth?
- Did core templates (memory, architecture, llms.txt) provide enough structure?
- Were first-project prompts (understand-codebase, repository-map) effective?

**Key question**: "What would have made week 1 easier?"

### Post-Feature Launch

**Focus on**:
- Did feature development prompts (planning, feature-dev, testing) work?
- Were coding standards clear enough?
- Did PR writing and memory update prompts capture context well?

**Key question**: "What context did AI miss that slowed us down?"

### Post-Incident Retrospective

**Focus on**:
- What documentation gaps contributed to the incident?
- Would better architecture docs have prevented it?
- Did debugging prompts help investigation?

**Key question**: "What documentation would have prevented or accelerated resolution?"

### Quarterly Review

**Focus on**:
- Trends over multiple features/sprints
- Templates that evolved most (or became stale)
- Prompts used frequently vs ignored

**Key question**: "What patterns emerged that aren't captured in templates?"

---

## Pro Tips

**Keep it blameless**: Focus on system improvement, not individual performance.

**Bring data**: Review actual git history, PRs, and files. Don't rely only on memory.

**Focus on patterns**: One-off issues aren't worth templating. Wait for pattern (2-3 occurrences).

**Quick validation**: Test improvements in real projects before committing.

**Batch updates**: Group related improvements and release together (avoid churn).

**Document outcomes**: Track whether improvements actually helped in next projects.

**Close the loop**: Review past retro improvements - did they work?

---

## Follow-Up Actions

After retrospective:

1. **Immediately** (same day):
   - [ ] Document improvements queue
   - [ ] Share findings with team
   - [ ] Prioritize top 3 improvements

2. **This week**:
   - [ ] Draft template/prompt updates for high-priority items
   - [ ] Create validation plan for major changes
   - [ ] Update meta/lessons-queue.md with validated learnings

3. **This month**:
   - [ ] Test improvements in real project
   - [ ] Commit validated changes
   - [ ] Update llms.txt, README, changelog
   - [ ] Bump version

4. **Next retrospective**:
   - [ ] Review whether improvements from last retro worked
   - [ ] Iterate if needed

---

**Last Updated**: February 2026
**Recommended Frequency**: End of projects, quarterly, or post-incident
**Time Investment**: 30 min (quick) to 2 hours (deep)
