# AI Engineering Templates

A collection of reusable templates for AI-native software development. Copy these files into your projects to improve AI coding assistant performance and maintain better project context.

---

## What's Inside

This repository contains three types of templates:

### 🤖 Cursor AI Rules (`cursor/`)

Behavioral rules for Cursor AI that promote:
- Planning before coding
- Small, safe changes
- Test-first development
- Reading project docs before making changes
- Updating project memory after major work

**Usage**: Copy `cursor/rules.md` to `.cursor/rules.md` in your project root.

### 🎭 AI-Native Development (`meta/personas/`)

This template includes a reusable AI persona system.

Personas live in:
`meta/personas/`

Every new repo should copy the default persona into:
`.cursor/rules/`

This ensures consistent AI collaboration across projects.

**Usage**: Copy `meta/personas/jordan-persona.md` to `.cursor/rules/jordan.md` in your project.

### 📋 Reusable Prompts (`prompts/`)

Copy-paste prompts optimized for small, focused tasks:
- `planning.md` - Plan features before implementation
- `debugging.md` - Systematic bug investigation
- `feature-dev.md` - Test-first feature development
- `testing.md` - Comprehensive test coverage
- `refactoring.md` - Safe code improvements
- `pr-writing.md` - Clear pull request documentation

**Usage**: Copy prompts into Cursor when needed, or reference them with `@prompts/[file]`.

### 📚 Project Templates (`project-templates/`)

Core documentation files that provide persistent context for AI:
- `llms.txt` - AI-readable project map
- `memory.md` - Implementation history and current state
- `architecture.md` - System design and components
- `decisions.md` - Architecture Decision Records (ADRs)
- `roadmap.md` - Product direction and milestones
- `tasks.md` - Active sprint and task tracking
- `testing.md` - Testing philosophy and standards
- `coding-standards.md` - Code style and conventions
- `deployment.md` - Deployment processes and runbooks
- `api-contracts.md` - API design standards

**Usage**: Copy entire `project-templates/` folder to your project root and customize placeholders.

---

## Quick Start

### For a New Project

1. **Set up AI persona**:
   ```bash
   mkdir -p /path/to/your-project/.cursor/rules/
   cp meta/personas/jordan-persona.md /path/to/your-project/.cursor/rules/jordan.md
   ```

2. **Copy Cursor rules**:
   ```bash
   cp cursor/rules.md /path/to/your-project/.cursor/rules.md
   ```

3. **Copy project templates**:
   ```bash
   cp -r project-templates/* /path/to/your-project/
   ```

4. **Customize templates**:
   - Fill in placeholders marked with `[BRACKETS]`
   - Update project-specific information
   - Remove sections that don't apply

5. **Use prompts as needed**:
   - Reference during development: `@prompts/feature-dev.md`
   - Or keep templates folder accessible for copy-paste

### For an Existing Project

1. Set up AI persona:
   - Copy `meta/personas/jordan-persona.md` to `.cursor/rules/jordan.md`

2. Add Cursor rules:
   - Copy `cursor/rules.md` to `.cursor/rules.md`

3. Start with core documentation:
   - Copy `memory.md`, `architecture.md`, and `decisions.md`
   - Document current state and historical context

4. Gradually adopt other templates as needed

---

## Additional Resources

### Meta / Continuous Improvement (`meta/`)

Workflows for evolving and improving this templates repository:
- `system-evolution.md` - How to improve templates over time
- `template-retrospective.md` - Post-project review process
- `new-project-bootstrap.md` - Canonical setup workflow
- `prompt-evolution.md` - Prompt library governance
- `personas/` - Reusable AI personas for consistent collaboration
- **`OPERATING_RHYTHM.md`** - Daily/monthly/quarterly maintenance cadence (start here!)

**Note**: The `meta/` folder is for maintaining *this* templates repository. Copy `meta/personas/` files into downstream projects as needed.

### Client Documentation (`client-docs/`)

Templates for consulting and agency work:
- Monthly retainer reports
- Retainer agreements
- Value analysis and pricing

### llms.txt Framework (`llms-txt/`)

Research-backed guidelines for creating optimized `llms.txt` files:
- `LLM_TXT_STANDARDS.md` - Best practices (95% AI success rate)
- `CREATE_LLM_TXT.md` - Quick creation guide
- `llms.txt.template` - Blank template
- `QUICK_REFERENCE.md` - Command cheatsheet

### ML Ops Runbooks (`oncall-runbooks/`)

Incident response procedures for ML systems:
- Model deployment and retraining
- Monitoring and alerting
- Data pipeline failures
- Infrastructure scaling

---

## Philosophy

Traditional repositories document for humans. **AI-native repositories document for AI agents.**

AI coding assistants perform significantly better when projects include:
- Architecture context
- Coding standards
- Testing expectations
- Decision history
- Roadmap and tasks
- Persistent memory

These templates provide that structure.

---

## How This Improves AI Performance

1. **Reduces hallucinations** - Clear context prevents invented solutions
2. **Maintains consistency** - Standards guide implementation patterns
3. **Preserves decisions** - ADRs prevent relitigating choices
4. **Enables planning** - Roadmap and tasks provide direction
5. **Improves quality** - Testing and coding standards set expectations
6. **Speeds onboarding** - New developers (AI or human) understand quickly

---

## Maintenance

**Keep documentation current**:
- Update `memory.md` after completing major features
- Document decisions in `decisions.md` when choosing between alternatives
- Keep `tasks.md` synchronized with actual work
- Refresh `architecture.md` when system design changes

**Stale documentation is worse than no documentation** - it misleads AI and humans alike.

---

## Contributing

Found an improvement? Have a template to add? Open an issue or PR.

---

## License

[Your chosen license]

---

## Credits

- llms.txt research by [Lance Martin](https://rlancemartin.github.io/2025/04/03/vibe-code/)
- ADR format by [Michael Nygard](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions)

---

**Last Updated**: February 2026