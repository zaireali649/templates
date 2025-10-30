# Create llms.txt for This Project

**Instruction for AI Assistant:**

> Create an optimized `llms.txt` file for this project following the standards in `@LLM_TXT_STANDARDS.md`. Analyze all files in this repository and generate comprehensive descriptions for each, organized by functional area.

That's it! Just say that to any AI code agent.

---

## What the AI Will Do

The AI will:
1. ✅ Scan all files in your project
2. ✅ Organize them by functional area (backend, frontend, database, etc.)
3. ✅ Write optimized descriptions following the research-backed format
4. ✅ Include specific function/class names
5. ✅ Add Key Concepts and Common Tasks sections
6. ✅ Create a production-ready `llms.txt` file

**Alternative:** If you prefer starting with a template, copy `llms.txt.template` to `llms.txt` and ask the AI to fill it in.

---

## Quick Copy-Paste Commands

### Option 1: Full Auto-Generation
```
@LLM_TXT_STANDARDS.md @CREATE_LLM_TXT.md - Create an optimized llms.txt for this project
```

### Option 2: Update Existing llms.txt
```
@LLM_TXT_STANDARDS.md @llms.txt - Optimize this llms.txt file following the standards
```

### Option 3: Add Specific Files
```
@LLM_TXT_STANDARDS.md - Add descriptions for these new files to llms.txt: [list files]
```

---

## What You'll Get

A file structure like this:

```markdown
# Your Project Name

> [Auto-generated description]

## Project Overview

**Tech Stack**: [Detected automatically]
**Status**: [Current state]
**Purpose**: [Primary purpose]

## Core Documentation

### README.md
[Optimized description with specific details]

### SETUP_GUIDE.md
[When to read, what you'll learn]

## [Auto-detected functional areas]

### path/to/file.ext
[Detailed, actionable description with function names]

## Key Concepts

[Architectural patterns explained]

## Common Tasks

[Quick reference for frequent operations]
```

---

## Tips for Best Results

**Be specific if needed:**
```
@LLM_TXT_STANDARDS.md - Create llms.txt focusing on:
- Backend API endpoints
- Database schema
- Authentication flow
```

**Request updates:**
```
@LLM_TXT_STANDARDS.md - Update llms.txt with the 5 new files I just added
```

**Get explanations:**
```
@LLM_TXT_STANDARDS.md - Explain why my current llms.txt isn't optimal
```

---

## File Placement

**Option A: Keep as Shared Templates (Recommended)**
1. Store these files in a central location: `~/templates/llms-txt/`
   - `LLM_TXT_STANDARDS.md`
   - `CREATE_LLM_TXT.md`
   - `llms.txt.template`
2. Reference from any project without copying
3. Just use `@` to reference the template location

**Option B: Copy to Each Project**
1. Copy `LLM_TXT_STANDARDS.md` to project root
2. Copy `CREATE_LLM_TXT.md` to project root
3. Optionally copy `llms.txt.template` as starting point

**Pro tip:** Keep templates in a shared folder you can reference across all projects via absolute path or symlink!

---

**That's it!** No complex prompts to remember. Just tag the files and say "create llms.txt" or "do this".

