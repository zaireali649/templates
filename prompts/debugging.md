# Debugging Prompt

Use this prompt when investigating bugs or unexpected behavior.

---

## Prompt

```
I'm experiencing [DESCRIBE THE BUG/ISSUE].

Help me debug this systematically:

1. Gather information:
   - Exact error message and stack trace
   - Steps to reproduce
   - Expected vs actual behavior
   - Recent changes that might be related
   - Environment details (OS, versions, config)

2. Investigate:
   - Review relevant code in the stack trace
   - Check related tests for clues
   - Look for similar issues in @memory.md or @decisions.md
   - Verify dependencies and configuration

3. Form hypotheses:
   - What are the most likely root causes?
   - What assumptions might be wrong?
   - What changed recently?

4. Test hypotheses:
   - Add logging/debugging output
   - Write minimal reproduction case
   - Test each hypothesis systematically

5. Propose fix:
   - Minimal change to resolve the root cause
   - Add test to prevent regression
   - Document the issue in @memory.md

Work through this methodically. Don't jump to solutions without understanding the root cause.
```

---

## Why This Works

- **Finds root causes** instead of treating symptoms
- **Prevents regressions** by adding tests
- **Builds knowledge** by documenting issues
- **Saves time** by avoiding trial-and-error
- **Improves code quality** with systematic investigation

---

## When to Use

- Encountering unexpected behavior
- Investigating test failures
- Tracking down production issues
- Understanding complex bugs
- When quick fixes haven't worked

---

## Tips

- Start with the error message and stack trace
- Add logging before making changes
- Test one hypothesis at a time
- Don't assume—verify with evidence
- Document findings for future reference
