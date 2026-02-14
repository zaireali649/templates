# Task Splitter

Break large features into small, safe, completable steps.

---

## Prompt

```
Break this feature into the smallest safe steps.

Feature: [describe feature]

Requirements:
- Each step should be completable in one focused session
- Each step should be independently testable
- Each step should not break existing functionality
- Steps should build on each other logically
```

---

## Why This Works

**Large tasks**: Overwhelming, easy to introduce bugs, hard to review

**Small tasks**: 
- Manageable scope
- Easier to test
- Smaller diffs = better reviews
- Can commit after each step
- Easy to roll back if needed

---

## Example

**Before**:
```
Add user profile feature with avatar upload, bio editing, and privacy settings
```

**After splitting**:
```
Step 1: Add User profile database table and migration
- Create migration for user_profiles table
- Add model/schema
- Test database operations

Step 2: Create basic profile view page
- Add route for /profile
- Create read-only profile component
- Display existing user data

Step 3: Add bio editing
- Add edit button and form
- Implement update endpoint
- Add validation and error handling
- Test edit flow

Step 4: Add avatar upload
- Implement file upload endpoint
- Add image storage (S3/local)
- Update profile view with avatar
- Test upload and display

Step 5: Add privacy settings
- Create settings UI
- Add privacy flags to database
- Implement privacy logic
- Test privacy controls

Step 6: Polish and edge cases
- Handle missing avatars
- Add loading states
- Improve error messages
- Cross-browser testing
```

---

## What You Get

For each step:
- **Clear scope**: Know exactly what to build
- **Definition of done**: When is this step complete?
- **Testing approach**: How to verify it works
- **Risk assessment**: What could go wrong?

---

## When to Use

- Starting a large feature
- Feeling overwhelmed by scope
- Before sprint planning
- Breaking down epics
- When estimates are too large

---

## Follow-up

After splitting:

```
For step 1, what files will I need to modify or create?
```

```
What are the potential risks in step 3?
```

```
Can steps 4 and 5 be done in parallel?
```

---

## Pro Tip

Combine with planning:

```
@prompts/task-splitter.md - Break this feature into steps

Then for each step:
@prompts/planning.md - Plan implementation for step [N]
```
