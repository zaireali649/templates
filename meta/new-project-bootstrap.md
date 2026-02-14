# New Project Bootstrap

Canonical step-by-step workflow for starting a new project with these templates.

---

## Purpose

This workflow ensures every new project starts with:
- Consistent AI behavior (via Cursor rules)
- Structured documentation (via project templates)
- Clear development workflows (via prompts)
- Proper initial context (via first-run commands)

**Use this checklist** for every new project to ensure nothing is missed.

---

## Prerequisites

Before starting:

- [ ] New project repository created and initialized
- [ ] Local development environment set up
- [ ] This templates repository cloned to `~/templates` (or known location)
- [ ] Cursor IDE installed and configured

---

## Phase 1: Copy Core Files (5 minutes)

### Step 1: Copy Cursor Rules

```bash
# Navigate to your new project
cd /path/to/your-project

# Create .cursor directory if it doesn't exist
mkdir -p .cursor

# Copy rules
cp ~/templates/cursor/rules.md .cursor/rules.md
```

**What this does**: Establishes AI behavior expectations (plan first, small changes, test-first, read docs before coding).

**Verify**: Check that `.cursor/rules.md` exists in your project root.

---

### Step 2: Copy Project Templates

```bash
# From your project root
cp -r ~/templates/project-templates/* .
```

**This copies 10 files**:
- `llms.txt` - AI-readable project map
- `memory.md` - Implementation history
- `architecture.md` - System design
- `decisions.md` - Architecture Decision Records
- `roadmap.md` - Product direction
- `tasks.md` - Sprint and task tracking
- `testing.md` - Testing standards
- `coding-standards.md` - Code conventions
- `deployment.md` - Deployment processes
- `api-contracts.md` - API design standards

**Verify**: Run `ls -la` and confirm all 10 files are present in project root.

---

### Step 3: Initial Git Commit (Optional but Recommended)

```bash
# Add templates to git
git add .cursor/ *.md

# Commit baseline templates
git commit -m "Add AI-native documentation templates

- Cursor AI behavioral rules
- Project memory and architecture templates
- Testing, coding, and API standards
- Deployment and roadmap tracking

Templates from: [your templates repo or source]"
```

**Why**: Preserves clean template state before customization. Makes it easy to see what you've changed.

---

## Phase 2: Fill Core Placeholders (30-60 minutes)

### Priority Order

Focus on these three files first (in order):

1. **llms.txt** (15 min) - Enables AI to navigate project
2. **memory.md** (10 min) - Establishes current state
3. **architecture.md** (20 min) - Documents initial design

Other templates can be filled as needed during development.

---

### File 1: llms.txt (15 minutes)

Open `llms.txt` and fill these sections:

**Project Overview**:
```markdown
# [Your Project Name]

> [One-sentence description of what this project does]

## Project Overview

**Tech Stack**: [e.g., React, Node.js, PostgreSQL, AWS]
**Status**: [In Development / MVP / Production]
**Purpose**: [2-3 sentence description of why this project exists]
```

**Core Documentation** (minimal for new project):
```markdown
### README.md
[Brief description of what's in your README]

### memory.md
Current project state and implementation history. Read this to understand what has been built and current status.

### architecture.md
System architecture and component design. Read this before making architectural changes.
```

**File Organization** (update tree with your actual structure):
```markdown
## File Organization

```
your-project/
├── src/                 # [Your source code]
├── tests/              # [Your test files]
├── README.md
├── memory.md
├── architecture.md
└── [your actual structure]
```
```

**Skip for now**: Detailed file descriptions (add incrementally as you build)

**Commit**:
```bash
git add llms.txt
git commit -m "Configure llms.txt with project basics"
```

---

### File 2: memory.md (10 minutes)

Open `memory.md` and fill **Current State** section:

```markdown
## Current State

**Version**: 0.1.0 (or Initial Setup)
**Last Updated**: [Today's date]
**Status**: Project initialization

### What's Working
- Project structure created
- Development environment configured
- [Any initial implementations]

### Known Issues
- None yet

### In Progress
- Initial feature development
- Setting up CI/CD
- [Whatever you're starting with]
```

Add initial entry to **Implementation History**:

```markdown
## Implementation History

### [Today's date] - Project Bootstrap
**What was built**: Initial project structure, documentation templates, development environment
**Why**: Starting [project name] to [solve what problem]
**Key decisions**: 
- Tech stack: [your choices]
- Architecture: [your approach]
**Files created**: Initial project structure
**Notes**: Using AI-native documentation templates for better AI assistant performance
```

**Skip for now**: Most other sections (fill as project evolves)

**Commit**:
```bash
git add memory.md
git commit -m "Initialize project memory with current state"
```

---

### File 3: architecture.md (20 minutes)

Open `architecture.md` and fill these sections:

**System Overview**:
```markdown
## System Overview

[2-3 sentences describing what you're building]

**Architecture Style**: [e.g., Monolithic API with SPA frontend, Microservices, Serverless]
**Deployment Model**: [e.g., Single-tenant on AWS, Multi-tenant SaaS, On-premise]
```

**Core Components** (just initial structure):
```markdown
## Core Components

### [Component 1, e.g., Frontend]
**Responsibility**: [What it does]
**Technology**: [Stack/framework]
**Key files**: [Initial structure]
**Scalability**: [Plans for growth]

### [Component 2, e.g., Backend API]
**Responsibility**: [What it does]
**Technology**: [Stack/framework]
**Key files**: [Initial structure]
**Scalability**: [Plans for growth]
```

**Technology Decisions**:
```markdown
## Technology Decisions

### [Choice 1, e.g., Database]
**Choice**: [Your selection]
**Reason**: [Why this choice]
**Trade-offs**: [What you're giving up]

### [Choice 2, e.g., Frontend Framework]
**Choice**: [Your selection]
**Reason**: [Why this choice]
**Trade-offs**: [What you're giving up]
```

**Skip for now**: Detailed data flows, security architecture, DR plans (add as you build)

**Commit**:
```bash
git add architecture.md
git commit -m "Document initial system architecture"
```

---

## Phase 3: Quick-Fill Optional Templates (15 minutes)

Fill these minimally so they exist with correct context:

### decisions.md

```markdown
### ADR-000: Use Architecture Decision Records

**Date**: [Today's date]
**Status**: Accepted

**Context**: Need to document why we make technical decisions.

**Decision**: Use ADRs based on Michael Nygard's template.

**Consequences**: Team has shared context on technical choices.
```

### roadmap.md

```markdown
## Vision
[1-2 sentences: What is this project becoming?]

## Current Focus
**Quarter**: Q[X] [Year]
**Theme**: MVP Development / Initial Launch / [Your phase]
**Key Goals**:
- [ ] [Goal 1]
- [ ] [Goal 2]
- [ ] [Goal 3]
```

### tasks.md

```markdown
## Current Sprint

**Sprint**: 1
**Dates**: [Start] - [End]
**Goal**: [What you're accomplishing this sprint]

### Active Tasks

#### High Priority
- [ ] **[Task 1]** - [Brief description]
- [ ] **[Task 2]** - [Brief description]
```

**Commit**:
```bash
git add decisions.md roadmap.md tasks.md
git commit -m "Initialize decisions, roadmap, and task tracking"
```

---

## Phase 4: Configure Standards (As Needed)

Fill `coding-standards.md`, `testing.md`, `api-contracts.md`, and `deployment.md` as you establish patterns.

**Don't fill these blindly** - wait until you have real code and real patterns. Then document what you're actually doing.

**Timing**:
- `coding-standards.md`: After 2-3 files written, document your conventions
- `testing.md`: When you write your first test, document your approach
- `api-contracts.md`: When you create your first endpoint, document your API style
- `deployment.md`: When you first deploy, document the process

---

## Phase 5: First Prompts to Run (5 minutes)

Open Cursor and run these prompts to establish AI context:

### 1. Orient AI to Project (Required)

```
I've just set up a new project using AI-native documentation templates.

Please read:
@llms.txt
@memory.md  
@architecture.md
@.cursor/rules.md

Confirm you understand:
1. What this project does
2. The current tech stack
3. The architectural approach
4. The development rules you should follow
```

**Expected response**: AI summarizes project, tech stack, architecture, and confirms it will follow rules.

---

### 2. Validate Setup (Optional but Recommended)

```
@architecture.md - Review the current project structure and let me know if there are any files or folders we should create before we start coding.

Consider:
- Standard folder structure for [your tech stack]
- Configuration files we'll need
- Initial boilerplate
```

**Expected response**: AI suggests any missing structure (e.g., `src/`, `tests/`, config files).

---

### 3. Plan First Feature (Before Coding)

```
@prompts/planning.md - We're ready to implement our first feature: [describe feature]

Create a plan including:
- Files to create/modify
- Step-by-step implementation approach
- Testing strategy
- Any architectural considerations
```

**Expected response**: Detailed plan following the planning prompt format.

---

## Phase 6: First Tasks Checklist (Before Coding Begins)

Before writing application code:

### Setup Tasks
- [ ] Initialize package manager (npm, pip, cargo, etc.)
- [ ] Install core dependencies
- [ ] Set up linter and formatter (document in coding-standards.md)
- [ ] Configure pre-commit hooks if using
- [ ] Create basic folder structure (`src/`, `tests/`, etc.)
- [ ] Set up local development environment (database, services)

### Documentation Tasks  
- [ ] README.md with setup instructions
- [ ] .env.example with required environment variables
- [ ] Contributing guidelines if team project

### First Code Tasks
- [ ] Basic "hello world" or health check endpoint
- [ ] One simple test to validate testing setup
- [ ] Verify linter and formatter work

### Validation Tasks
- [ ] Can run the project locally
- [ ] Can run tests
- [ ] AI can understand project structure (test with simple prompt)
- [ ] Commit history is clean and documented

---

## Variations

### For a Greenfield Project (New Codebase)

Use the full workflow above. This is the default.

---

### For an Existing Codebase (Migration)

**See `EXISTING_PROJECT_GUIDE.md` for detailed instructions.**

Quick variation:
1. **Phase 1**: Copy Cursor rules and templates (same as above)
2. **Phase 2**: Document **current state** (not ideal state)
   - llms.txt: Map existing files
   - memory.md: Recent history (last 3-6 months)
   - architecture.md: Current architecture (as-is)
3. **Phase 3**: Mine git history for decisions
4. **Phase 4**: Run first prompts to validate AI understanding
5. **Phase 5**: Fill other templates incrementally

---

### For a Team Project

**Add these steps**:

**After Phase 2**:
- [ ] Team review of documentation (ensure accuracy)
- [ ] Agree on conventions before coding begins
- [ ] Schedule weekly memory.md updates

**After Phase 3**:
- [ ] Share `.cursor/rules.md` expectations with team
- [ ] Agree on PR and review workflows
- [ ] Set up shared prompt library (if needed)

**Before Phase 6**:
- [ ] Pair on first feature to validate workflow
- [ ] Document team-specific conventions

---

### For a Rapid Prototype / Hackathon

**Minimal version** (15 min setup):
1. Copy `.cursor/rules.md` ✅
2. Copy only `memory.md` and `llms.txt` ✅
3. Fill project overview in llms.txt (5 min)
4. Fill current state in memory.md (5 min)
5. Run first prompt to orient AI ✅
6. Start coding

Skip: architecture.md, roadmap.md, standards docs (add later if prototype succeeds)

---

## Success Criteria

You'll know bootstrap succeeded when:

✅ AI references project documentation when making suggestions
✅ AI follows coding standards without being told
✅ AI suggests solutions aligned with architecture
✅ Team members can understand project by reading docs
✅ New contributors get oriented quickly

---

## Troubleshooting

**AI isn't reading my docs**:
- Check `.cursor/rules.md` is in the right location
- Try explicitly referencing: "Before proceeding, read @architecture.md"
- Verify llms.txt has accurate file descriptions

**Templates feel overwhelming**:
- Start with just llms.txt, memory.md, architecture.md
- Fill other templates only when you need them
- Better to have 3 good docs than 10 empty files

**Placeholders are confusing**:
- Look at examples in the template
- Check existing projects for patterns
- Ask AI: "Help me fill [template] for [project type]"

**Setup taking too long**:
- Use rapid prototype variation (15 min)
- Fill templates incrementally as project grows
- Remember: upfront time investment pays off quickly

---

## Next Steps

After bootstrap is complete:

1. **Start first feature** using `@prompts/planning.md`
2. **Update memory.md** after each significant change
3. **Run retrospective** after first feature or end of sprint
4. **Refine documentation** based on what you learn

---

**Last Updated**: February 2026
**Time Investment**: 1-2 hours for full setup, 15 min for minimal
**Recommended**: Run through this checklist for every new project
