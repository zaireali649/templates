# Understand the Codebase

**Use this as your FIRST PROMPT in any new repository.**

Get AI to build a mental map before making changes.

---

## Prompt

```
Study this repository and explain:

- what the application does
- tech stack used
- architecture overview
- key entry points
- how to run locally
- risky or complex areas
```

---

## Why This Is Critical

**Before this prompt**: AI makes assumptions, suggests wrong patterns, breaks things

**After this prompt**: AI understands your system and makes contextual suggestions

**Time investment**: 2-3 minutes
**Time saved**: Hours of fixing bad suggestions

---

## What You'll Get

**Application purpose**: "This is a SaaS analytics dashboard that..."

**Tech stack**: "React frontend, Node.js API, PostgreSQL, Redis, deployed on AWS..."

**Architecture**: "Frontend in src/, API in api/, shared types in shared/..."

**Entry points**: "Start at src/index.tsx for frontend, api/server.ts for backend..."

**How to run**: "npm install && npm run dev for local development..."

**Risky areas**: "Payment processing in api/payments/, complex state in src/store/, database migrations in migrations/"

---

## Follow-up Questions

After the initial explanation, ask:

**For deeper understanding**:
```
Show me a typical user flow through the codebase
```

**For specific areas**:
```
Explain how authentication works in detail
```

**For dependencies**:
```
What are the key dependencies and what do they do?
```

---

## When to Use

- **Always** - first prompt in any new repo
- Joining a new project
- Contributing to open source
- Before making significant changes
- After being away from a codebase for months

---

## Pro Tip

Combine with architecture.md if it exists:

```
Study this repository using @architecture.md as context, then explain:
[same questions as above]
```

This grounds AI in your documented architecture before exploring the code.
