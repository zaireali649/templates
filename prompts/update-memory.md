# Update Memory

Keep project memory current after completing work.

---

## Prompt

```
Update @memory.md with:

What we implemented:
[Describe what was built]

Key decisions made:
[Any important choices or tradeoffs]

Files changed:
[List of modified files]

Remaining work:
[What's left to do]

Notes for future:
[Anything important to remember]
```

---

## Why This Matters

**Without memory updates**: Context gets lost, mistakes get repeated

**With updates**: 
- Future developers (including AI) understand what happened
- Decisions are preserved
- Known issues are documented
- Onboarding is faster

---

## Example

```
Update @memory.md with:

What we implemented:
Added two-factor authentication using TOTP. Users can now enable 2FA 
in settings, scan QR code with authenticator app, and use 6-digit codes 
to login.

Key decisions made:
- Chose TOTP over SMS for better security and lower cost
- Made 2FA optional rather than mandatory to ease adoption
- Store backup codes hashed in database (not reversible)
- 30-second time window for code validity

Files changed:
- api/routes/auth.ts - Added 2FA verification endpoint
- api/services/twoFactor.ts - TOTP generation and validation
- src/components/Settings/TwoFactorSetup.tsx - Setup UI
- database/migrations/20240214_add_2fa.sql - Added 2FA fields

Remaining work:
- Add 2FA recovery flow if user loses device
- Email notification when 2FA is enabled/disabled
- Admin ability to disable 2FA for account recovery
- Metrics on 2FA adoption rate

Notes for future:
- QR codes generated server-side to prevent client manipulation
- Backup codes are single-use only
- Consider adding WebAuthn support as alternative to TOTP
```

---

## When to Use

After:
- Completing a feature
- Making architectural changes
- Fixing significant bugs
- Making important decisions
- Merging major PRs

---

## What to Update

### Current State Section
```
Update "What's Working" with new completed features
Update "Known Issues" with any new bugs discovered
Update "In Progress" with current work
```

### Implementation History
```
Add dated entry with:
- What was built
- Why it was built
- Key technical decisions
- Files affected
```

### Lessons Learned
```
Document:
- What worked well
- What didn't work
- What you'd do differently
```

---

## Frequency

**Minimum**: After every merged PR

**Ideal**: Daily for active development

**Critical**: Before knowledge transfer or onboarding

---

## Pro Tip

Combine with PR workflow:

```
Before creating PR:
@prompts/pr-writing.md - Create PR description

After merging PR:
@prompts/update-memory.md - Update project memory
```

This ensures both short-term (PR) and long-term (memory.md) documentation stay current.

---

## AI-Assisted Updates

Let AI help write the update:

```
We just implemented [feature]. Help me write an update for @memory.md 
including what we built, key decisions, and files changed.
```

AI can draft the update, you review and refine.
