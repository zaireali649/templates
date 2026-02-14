# Quick Start Guide

How to use these templates in your projects.

---

## For a New Project

### 1. Copy Cursor Rules
```bash
cp cursor/rules.md /path/to/your-project/.cursor/rules.md
```

This sets AI behavior expectations (plan first, small changes, test-first).

---

### 2. Copy Project Templates
```bash
cp -r project-templates/* /path/to/your-project/
```

This gives you 10 documentation files:
- `llms.txt` - AI project map
- `memory.md` - What's been built
- `architecture.md` - System design
- `decisions.md` - Why technical choices were made
- `roadmap.md` - Product direction
- `tasks.md` - Current sprint/tasks
- `testing.md` - Test standards
- `coding-standards.md` - Code conventions
- `deployment.md` - How to deploy
- `api-contracts.md` - API standards

---

### 3. Fill in Placeholders

Replace all `[BRACKETS]` with your project details:
- Project name and description
- Tech stack
- Team info
- Current status

Start with `llms.txt`, `memory.md`, and `architecture.md` first.

---

### 4. Use Prompts During Development

Reference prompts in Cursor with `@`:

- `@prompts/planning.md` - Before building features
- `@prompts/debugging.md` - When investigating bugs
- `@prompts/feature-dev.md` - For test-first development
- `@prompts/testing.md` - When writing tests
- `@prompts/refactoring.md` - Before restructuring code
- `@prompts/pr-writing.md` - When creating PRs

Or copy-paste prompts as needed.

---

## For an Existing Project

**See `EXISTING_PROJECT_GUIDE.md` for detailed walkthrough.**

### Quick Start

1. **Add Cursor rules**:
   ```bash
   cp cursor/rules.md /path/to/project/.cursor/rules.md
   ```

2. **Add core docs** (priority order):
   ```bash
   cp project-templates/memory.md /path/to/project/
   cp project-templates/architecture.md /path/to/project/
   cp project-templates/decisions.md /path/to/project/
   ```

3. **Document what exists now** (not what you wish you had)

4. **Add other templates** gradually as needed

**Challenge**: Documenting existing systems without architecture.md? 
See `EXISTING_PROJECT_GUIDE.md` for step-by-step help including:
- How to mine git history for decisions
- Using AI to help document your architecture
- Prioritizing which templates to add first
- Real examples and time estimates

---

## Key Files Explained

### Cursor Rules (`cursor/rules.md`)
Controls AI agent behavior - copy to `.cursor/rules.md` in your project.

### Prompts (`prompts/*.md`)
Copy-paste workflows for common tasks. Reference with `@prompts/[file].md`.

### Project Templates (`project-templates/*.md`)
Persistent memory for AI agents. Copy to project root and customize.

### Client Docs (`client-docs/*.md`)
Monthly reports and retainer agreements for consulting work.

### llms.txt Framework (`llms-txt/*.md`)
Guidelines for creating optimized `llms.txt` files (already have one in project-templates).

### ML Runbooks (`oncall-runbooks/*.md`)
Incident response procedures for ML systems.

---

## Tips

**Update regularly**: Keep `memory.md` and `tasks.md` current as you work.

**Reference in commits**: AI agents read these files before making changes.

**Customize freely**: Remove sections you don't need, add project-specific content.

**Keep it simple**: Start with core docs, add others as project grows.

---

## Example Workflow

```bash
# 1. New project
mkdir my-app && cd my-app
git init

# 2. Copy templates
cp ~/templates/cursor/rules.md .cursor/rules.md
cp -r ~/templates/project-templates/* .

# 3. Fill in placeholders
# Edit llms.txt, memory.md, architecture.md with your project info

# 4. Start coding with AI
# Reference @prompts/planning.md before features
# AI follows .cursor/rules.md automatically
# AI reads your project docs for context
```

---

## Questions?

See `README.md` for detailed documentation.
