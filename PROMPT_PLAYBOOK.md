# Prompt Playbook

Reusable prompts for ChatGPT, Claude, and Cursor. All prompts have been organized into dedicated files.

---

## General AI Prompts

For use with ChatGPT, Claude, or any AI assistant.

Located in `general-prompts/`:

### Prompt Frameworks
- **[TCREI Template](general-prompts/tcrei-template.md)** - Structured prompt template (Task, Context, Reference, Evaluation, Iteration)
- **[MASTER Framework](general-prompts/master-framework.md)** - Comprehensive structure (Context, Objective, Role, Constraints, Output)
- **[Prompt Engineer](general-prompts/prompt-engineer.md)** - Get AI help to craft better prompts

### Quick Formats
- **[Rage Mode](general-prompts/rage-mode.md)** - Get straight answers, no fluff, 5 concrete steps
- **[Speed Summary](general-prompts/speed-summary.md)** - Summarize into 5 bullets + 1 "so what" takeaway

### Specialized Roles
- **[Systems Architect](general-prompts/systems-architect.md)** - Design production-ready systems with tradeoffs and scaling plans
- **[Startup Co-founder](general-prompts/startup-cofounder.md)** - Validate ideas, find MVP features, identify risks
- **[Code Explainer](general-prompts/code-explainer.md)** - Understand code like you're debugging it

### Learning & Research
- **[Learning Accelerator](general-prompts/learning-accelerator.md)** - Master topics with ELI5 → professional → hands-on structure
- **[Research Synthesizer](general-prompts/research-synthesizer.md)** - Turn research into actionable briefings
- **[Self-Critique Loop](general-prompts/self-critique.md)** - Get AI to critique and improve its own answers

---

## Cursor Development Prompts

For use with Cursor AI coding assistant.

Located in `prompts/`:

### Getting Started (Use These First)
- **[Understand Codebase](prompts/understand-codebase.md)** - ⭐ **START HERE** - Map the repository before making changes
- **[Repository Map](prompts/repository-map.md)** - Understand folder structure and component interactions
- **[Follow Project Rules](prompts/follow-project-rules.md)** - Ensure AI follows your architecture and coding standards

### Planning & Organization
- **[Planning](prompts/planning.md)** - Comprehensive feature planning workflow (detailed)
- **[Task Splitter](prompts/task-splitter.md)** - Break large features into small, safe steps

### Development Workflows
- **[Feature Development](prompts/feature-dev.md)** - Test-first feature development with incremental implementation
- **[Debugging](prompts/debugging.md)** - Systematic debugging workflow (investigate root cause first)
- **[Testing](prompts/testing.md)** - Write comprehensive tests with coverage analysis
- **[Refactoring](prompts/refactoring.md)** - Safe refactoring without changing behavior

### Finishing Work
- **[PR Writing](prompts/pr-writing.md)** - Create comprehensive pull request descriptions
- **[Update Memory](prompts/update-memory.md)** - Keep project memory current after completing work

---

## Quick Reference

### First Time in a Codebase
```
1. @prompts/understand-codebase.md
2. @prompts/repository-map.md
3. Start working with context
```

### Starting a Feature
```
1. @prompts/planning.md or @prompts/task-splitter.md
2. @prompts/feature-dev.md (test-first development)
3. @prompts/update-memory.md (after completion)
```

### Investigating a Bug
```
@prompts/debugging.md - Root cause analysis first, then fix
```

### Before Submitting Work
```
1. @prompts/pr-writing.md - Document changes
2. @prompts/update-memory.md - Update project context
```

---

## Advanced Patterns

### Prompt Chaining

Instead of one massive prompt, chain smaller focused prompts:

**Example - Building a SaaS**:
```
Prompt 1: @general-prompts/startup-cofounder.md → Validate idea
Prompt 2: @general-prompts/systems-architect.md → Design architecture  
Prompt 3: @prompts/task-splitter.md → Break into steps
Prompt 4: @prompts/feature-dev.md → Implement incrementally
Prompt 5: @prompts/update-memory.md → Document progress
```

### Multi-Step Workflows

Combine prompts for complex tasks:

**Example - Major Refactor**:
```
1. @prompts/understand-codebase.md - Understand current state
2. @prompts/planning.md - Plan refactoring approach
3. @prompts/refactoring.md - Execute safe refactoring
4. @prompts/testing.md - Ensure no regressions
5. @prompts/pr-writing.md - Document changes
```

---

## Pro Tips

### Ground AI in Your Project

Always reference project docs when starting work:
```
Before we start, read:
@architecture.md
@coding-standards.md
@memory.md

Now implement [feature] following our patterns.
```

### Iterative Improvement

Use self-critique for important work:
```
@general-prompts/self-critique.md

Give your best answer for: [complex question]
Then critique it and improve it.
```

### Speed vs Depth

**Need speed?**: Use `@general-prompts/rage-mode.md`  
**Need depth?**: Use `@general-prompts/tcrei-template.md` or `@general-prompts/master-framework.md`

---

## Customization

Feel free to:
- Modify prompts for your workflow
- Create project-specific variants
- Combine prompts into your own workflows
- Add prompts to your project's documentation

---

## Quick Access

Copy prompts you use frequently to a scratchpad or add them to your IDE snippets.

**Example snippet**:
```
// Quick debug prompt
@prompts/debugging.md - Bug: [describe issue]
Investigate root cause first.
```

---

**See individual prompt files for detailed usage, examples, and variations.**
