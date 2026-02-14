# Follow Project Rules

Ensure AI follows your project's established patterns and standards.

---

## Prompt

```
Implement this feature: [describe feature]

Follow the rules and patterns defined in:
@architecture.md
@coding-standards.md
@testing.md
@api-contracts.md

Match existing code style and conventions in the codebase.
```

---

## Why This Matters

**Without this**: AI invents new patterns, breaks conventions, creates inconsistency

**With this**: AI follows your established practices, maintains consistency

---

## What This Does

AI will:
- Check architecture.md for system design patterns
- Follow coding-standards.md for naming and style
- Match testing.md for test expectations
- Follow api-contracts.md for API design
- Look at existing code for examples

Result: Code that looks like it was written by someone who knows your project.

---

## Variations

**For specific standards**:
```
Implement this feature following @coding-standards.md only.
```

**For architectural alignment**:
```
Design this component following the patterns in @architecture.md.
```

**For testing requirements**:
```
Write tests for this feature following @testing.md standards.
```

---

## Example Output

Instead of:
```javascript
// AI invents new pattern
function getUserData() {
  return axios.get('/user')
}
```

You get:
```javascript
// Follows your project's API client pattern from architecture.md
async function fetchUserData(): Promise<User> {
  return apiClient.get<User>('/api/v1/users/me')
}
```

---

## When to Use

- Every feature implementation
- When onboarding AI to your project
- After establishing new standards
- When consistency is critical
- Working with junior developers (AI or human)

---

## Best Practice

Reference project docs at the start of each session:

```
I'm working on this codebase. Before we start:
1. Read @architecture.md
2. Read @coding-standards.md  
3. Read @testing.md

Now, let's implement [feature].
```

This grounds AI in your project before making suggestions.

---

## Pro Tip

If AI still suggests something inconsistent:

```
This doesn't follow our patterns in @coding-standards.md. 
Rewrite following our conventions.
```

Point specifically to the doc that defines the correct pattern.
