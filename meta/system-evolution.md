# System Evolution

How this templates repository improves over time based on real-world usage.

---

## Purpose

This repository is a **living system**. Every project that uses these templates should surface insights that improve:
- Prompts that didn't work as expected
- Templates with missing sections
- Rules that need refinement
- Workflows that could be smoother

**Philosophy**: Real projects reveal gaps. Capture those lessons and evolve the templates.

---

## Inputs That Signal Gaps

Watch for these signals that templates need improvement:

### Project Retrospectives
- Teams repeatedly add the same custom sections to templates
- Common questions that documentation doesn't answer
- Prompts that require frequent clarification

### User Friction
- Confusion during template adoption
- Repeated questions in issues/discussions
- Templates copied but never filled in

### Repeated Manual Edits
- Same placeholder always replaced with similar content
- Sections consistently deleted as "not applicable"
- Missing cross-references discovered during use

### AI Performance Issues
- AI suggests solutions that ignore project standards
- Context missing that would have grounded better responses
- Prompts that work in theory but fail in practice

---

## Identifying Gaps in Templates

### Symptoms → Candidate Changes

| Symptom | Root Cause | Template Change |
|---------|------------|-----------------|
| AI doesn't follow coding standards | Standards not explicit enough | Enhance `coding-standards.md` with examples |
| Same questions asked repeatedly | Missing documentation section | Add FAQ or troubleshooting section |
| Template section always deleted | Not universally applicable | Move to optional section or separate template |
| Placeholder confusing | Unclear what to fill in | Add inline examples or guidance |
| Cross-cutting concerns missed | No central reference | Add to `architecture.md` or create new template |
| Retro identifies pattern not captured | Lesson learned not documented | Add to appropriate template or create new one |

### Gap Identification Process

1. **Collect friction points** from projects using templates
2. **Identify patterns** - One-off issues vs systematic gaps
3. **Validate** - Would this improvement help multiple projects?
4. **Assess impact** - High-value fix vs nice-to-have
5. **Prioritize** - Focus on changes that improve AI performance or reduce adoption friction

---

## Updating Existing Templates Safely

### Backwards Compatibility Principles

**Do:**
- Add new optional sections at the end
- Provide inline guidance for new placeholders
- Keep existing section structure intact
- Add examples that clarify without changing semantics

**Don't:**
- Remove sections that existing projects rely on
- Rename placeholders (breaks search/replace flows)
- Reorder major sections (breaks familiarity)
- Change file names (breaks references)

### Update Process

1. **Create draft changes** in a branch
2. **Test with real project** - Copy updated template and validate it works
3. **Check backwards compatibility** - Ensure old versions still make sense
4. **Update version and changelog** - Document what changed and why
5. **Update `llms.txt`** - Reflect new sections in file descriptions
6. **Announce breaking changes** - If unavoidable, provide migration guide

### Template Versioning

**Current approach**: Date-based with semantic indicators

- **Date**: Last updated date in template footer
- **Semantic markers**:
  - **(Added)** - New optional sections
  - **(Changed)** - Modified existing content
  - **(Deprecated)** - Section marked for removal
  - **(Removed)** - Breaking change, provide alternative

**Example changelog entry**:
```markdown
## 2026-02-20 - project-templates/architecture.md
- (Added) Security Architecture section
- (Changed) Core Components format now includes scalability notes
- (Deprecated) "Future Plans" section - use roadmap.md instead
```

---

## Reviewing and Improving Cursor Rules

### Evaluation Criteria

Review `cursor/rules.md` for:

1. **Effectiveness** - Do rules actually change AI behavior?
2. **Clarity** - Are rules specific and actionable?
3. **Completeness** - Are there behaviors we want but haven't specified?
4. **Conflicts** - Do rules contradict each other?
5. **Relevance** - Are rules still aligned with best practices?

### Common Rule Improvements

**Too vague**:
- ❌ "Write good tests"
- ✅ "Write tests covering happy path, edge cases, and error conditions. Follow AAA pattern (Arrange-Act-Assert)."

**Too restrictive**:
- ❌ "Never modify existing code"
- ✅ "Prefer small, incremental changes. When refactoring, ensure tests pass before and after."

**Missing guidance**:
- Problem: AI doesn't update memory.md consistently
- Solution: Add explicit rule: "After implementing features, update memory.md with what changed, why, and files affected."

### Rule Change Process

1. **Identify behavior gap** - What AI should do but doesn't?
2. **Draft specific rule** - Make it actionable
3. **Test in real project** - Copy updated rules, observe AI behavior
4. **Validate improvement** - Does AI follow the new rule?
5. **Update template** - Merge into `cursor/rules.md`
6. **Document in changelog** - Note rule addition/modification

---

## Capturing Lessons from Real Projects

### What to Capture

**Document when you discover**:
- Prompts that consistently fail or succeed
- Template sections that are always modified the same way
- Standards that need more examples
- Workflows that could be streamlined
- Anti-patterns teams encounter repeatedly

**Don't capture**:
- Project-specific implementation details
- One-off issues that won't recur
- Solutions that aren't generalizable

### Where to Record Lessons

Create a lessons log in this repository:

**During projects** (lightweight):
- Create `meta/lessons-queue.md` (not tracked in template)
- Note date, project context (anonymized), what happened, potential improvement

**After projects** (processed):
- Run `meta/template-retrospective.md` workflow
- Convert validated lessons into template updates
- Archive processed lessons with outcomes

### Converting Lessons to Improvements

**Lesson** → **Improvement Type**:

| Lesson Type | Action | File to Update |
|------------|--------|----------------|
| Prompt didn't ground AI properly | Refine prompt with better context instructions | `prompts/*.md` |
| Template missing critical section | Add section to template | `project-templates/*.md` |
| Standard unclear, caused inconsistency | Add examples to standards doc | `project-templates/coding-standards.md` |
| Rule not specific enough | Enhance or add rule | `cursor/rules.md` |
| Workflow inefficient | Update guide or create new prompt | `QUICK_START.md` or `prompts/` |
| Documentation unclear | Improve onboarding guide | `README.md`, `EXISTING_PROJECT_GUIDE.md` |

---

## Maintenance Cadence

### Monthly Review (30 minutes)
- [ ] Check for new GitHub issues/discussions suggesting improvements
- [ ] Review any lessons logged in `meta/lessons-queue.md`
- [ ] Quick scan: are placeholder examples still relevant?
- [ ] Update "Last Updated" dates on modified templates

### Quarterly Review (2-3 hours)
- [ ] Run retrospective on projects completed this quarter
- [ ] Review prompt effectiveness (which prompts are heavily used vs ignored?)
- [ ] Check `llms.txt` for accuracy (does it reflect current file state?)
- [ ] Evaluate whether new templates are needed (recurring patterns not covered)
- [ ] Review deprecated sections (can any be removed safely now?)
- [ ] Update version/changelog
- [ ] Validate all cross-references between files still work

### Annual Review (1 day)
- [ ] Comprehensive evaluation of entire template set
- [ ] Major version consideration (significant changes accumulated?)
- [ ] Competitive analysis (new best practices in AI-native development?)
- [ ] User survey (if templates are public/shared)
- [ ] Refactor/consolidate if templates have sprawled
- [ ] Update research references (new studies on AI code agents?)

### Triggers for Immediate Review
- Breaking change in Cursor AI behavior
- New research on AI coding assistant performance
- Multiple similar issues reported in short time
- Major workflow shift (e.g., new testing framework standard)

---

## Version Control Strategy

### Repository Versioning

**Recommended scheme**: [DATE]-based releases with semantic tags

Format: `YYYY-MM-DD` with optional `major.minor.patch` semantic indicator

**Version bumps**:
- **Major (1.x.x → 2.x.x)** - Breaking changes to template structure, file renames, removed sections
- **Minor (x.1.x → x.2.x)** - New templates added, significant new sections, enhanced prompts
- **Patch (x.x.1 → x.x.2)** - Typo fixes, clarifications, minor example updates

**Git tags**:
```bash
git tag -a v2.1.0 -m "Added meta/ folder for continuous improvement workflows"
git push origin v2.1.0
```

### Changelog Maintenance

Keep `CHANGELOG.md` at repo root with structure:

```markdown
## [Unreleased]
- (Added) New template for X
- (Changed) Enhanced Y with Z

## [2.1.0] - 2026-02-15
### Added
- meta/ folder with system evolution workflows
- meta/template-retrospective.md for post-project reviews

### Changed
- Enhanced architecture.md with security section
- Updated llms.txt with meta/ documentation

### Deprecated
- None

### Removed
- None
```

---

## Quality Assurance Checklist

Before releasing template updates:

**Content Quality**:
- [ ] New content matches existing tone (professional, concise, AI-readable)
- [ ] Placeholders use consistent `[BRACKET]` format
- [ ] Cross-references use correct relative paths
- [ ] Examples are concrete and helpful
- [ ] Sections follow existing structural patterns

**Technical Accuracy**:
- [ ] Tested in at least one real project
- [ ] AI can parse and act on new content
- [ ] No broken links or missing files
- [ ] Git commands and code examples are valid

**Discoverability**:
- [ ] `llms.txt` updated with new/changed files
- [ ] `README.md` updated if user-facing change
- [ ] Relevant guides updated (QUICK_START, EXISTING_PROJECT_GUIDE, etc.)
- [ ] Cross-links added from related files

**Documentation**:
- [ ] Changelog updated with changes
- [ ] Version bumped appropriately
- [ ] "Last Updated" dates refreshed
- [ ] Breaking changes highlighted with migration path

---

## Anti-Patterns to Avoid

❌ **Kitchen sink syndrome** - Adding every possible section "just in case"
✅ **Focused templates** - Keep core templates lean, create specialized variants

❌ **Premature optimization** - Adding templates before patterns are proven
✅ **Evidence-based evolution** - Wait for 2-3 projects to show pattern before templating

❌ **Stale improvements** - Logging lessons but never processing them
✅ **Regular cadence** - Schedule quarterly reviews to process lessons queue

❌ **Breaking changes without notice** - Surprise breaking changes frustrate users
✅ **Deprecation path** - Mark deprecated → provide alternative → remove after grace period

❌ **Documentation drift** - Updating templates but not llms.txt or README
✅ **Synchronized updates** - Update all discovery surfaces when templates change

---

## Getting Started

1. **After your next project**: Run `meta/template-retrospective.md`
2. **Log improvements**: Note what worked and what didn't in `meta/lessons-queue.md`
3. **Monthly check-in**: Review lessons and prioritize improvements
4. **Update templates**: Make evidence-based improvements
5. **Repeat**: Every project makes the templates better

---

**Last Updated**: February 2026
**Versioning Scheme**: Date-based with semantic indicators
**Review Cadence**: Monthly (quick), Quarterly (thorough), Annual (comprehensive)
