# Create llm.txt for This Project

**Instruction for AI Assistant:**

> Create an optimized `llm.txt` file for this project following the standards in `@LLM_TXT_STANDARDS.md`. Analyze all files in this repository and generate comprehensive descriptions for each, organized by functional area.

That's it! Just say that to any AI code agent.

---

## What the AI Will Do

The AI will:
1. ✅ Scan all files in your project
2. ✅ Organize them by functional area (backend, frontend, database, etc.)
3. ✅ Write optimized descriptions following the research-backed format
4. ✅ Include specific function/class names
5. ✅ Add Key Concepts and Common Tasks sections
6. ✅ Create a production-ready `llm.txt` file

**Alternative:** If you prefer starting with a template, copy `llm.txt.template` to `llm.txt` and ask the AI to fill it in.

---

## Quick Copy-Paste Commands

### Option 1: Full Auto-Generation
```
@LLM_TXT_STANDARDS.md @CREATE_LLM_TXT.md - Create an optimized llm.txt for this project
```

### Option 2: Update Existing llm.txt
```
@LLM_TXT_STANDARDS.md @llm.txt - Optimize this llm.txt file following the standards
```

### Option 3: Add Specific Files
```
@LLM_TXT_STANDARDS.md - Add descriptions for these new files to llm.txt: [list files]
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
@LLM_TXT_STANDARDS.md - Create llm.txt focusing on:
- Backend API endpoints
- Database schema
- Authentication flow
```

**Request updates:**
```
@LLM_TXT_STANDARDS.md - Update llm.txt with the 5 new files I just added
```

**Get explanations:**
```
@LLM_TXT_STANDARDS.md - Explain why my current llm.txt isn't optimal
```

---

## File Placement

**Option A: Keep as Shared Templates (Recommended)**
1. Store these files in a central location: `~/templates/llm-txt/`
   - `LLM_TXT_STANDARDS.md`
   - `CREATE_LLM_TXT.md`
   - `llm.txt.template`
2. Reference from any project without copying
3. Just use `@` to reference the template location

**Option B: Copy to Each Project**
1. Copy `LLM_TXT_STANDARDS.md` to project root
2. Copy `CREATE_LLM_TXT.md` to project root
3. Optionally copy `llm.txt.template` as starting point

**Pro tip:** Keep templates in a shared folder you can reference across all projects via absolute path or symlink!

---

**That's it!** No complex prompts to remember. Just tag the files and say "create llm.txt" or "do this".

