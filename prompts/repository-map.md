# Repository Map

Create a mental model of the codebase structure.

---

## Prompt

```
Create a mental map of this repo.

Output:
- folder structure summary
- responsibilities of each major folder
- key services/modules and how they interact
```

---

## Why This Helps

Gives you (and AI) a clear structural understanding before diving into specifics.

**Like**: Reading a table of contents before reading a book

**Result**: Faster navigation, better understanding of where things belong

---

## Example Output

```
Folder Structure:
src/
  components/  - React UI components
  pages/       - Next.js page routes
  hooks/       - Custom React hooks
  utils/       - Helper functions
  api/         - API client code

api/
  routes/      - Express route definitions
  services/    - Business logic layer
  models/      - Database models
  middleware/  - Auth, logging, error handling

shared/
  types/       - TypeScript type definitions
  constants/   - Shared constants

Key Interactions:
- Pages use Components and Hooks
- Components call API client
- API client talks to Backend routes
- Routes use Services for business logic
- Services interact with Models
- Everything shares Types from shared/
```

---

## Follow-up Questions

**For data flow**:
```
Show me how data flows from user action to database and back
```

**For specific feature**:
```
Which files are involved in the authentication flow?
```

**For dependencies**:
```
What are the key external services this app depends on?
```

---

## When to Use

- New to the codebase
- Before starting a cross-cutting feature
- Planning refactoring
- Documentation for team members
- Code review of structural changes

---

## Combine With

Use alongside `understand-codebase.md`:

1. First: `@prompts/understand-codebase.md` (understand what it does)
2. Then: `@prompts/repository-map.md` (understand how it's organized)
3. Finally: Start working with full context
