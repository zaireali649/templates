# Adding Templates to Existing Projects

How to adopt AI-native documentation when you already have code but no structured docs.

---

## The Challenge

Your project has:
- ✅ Working code
- ✅ Git history
- ✅ Maybe some README files
- ❌ No architecture.md
- ❌ No memory.md
- ❌ No decisions.md
- ❌ No structured documentation for AI

**Goal**: Bootstrap these templates by documenting what already exists, not what you wish you had.

---

## Phase 1: Add Cursor Rules (5 minutes)

Start here - this improves AI behavior immediately.

```bash
cp cursor/rules.md /path/to/project/.cursor/rules.md
```

**Benefit**: AI will now read docs before coding, make smaller changes, ask questions when unclear.

---

## Phase 2: Create memory.md (30-60 minutes)

Document what exists right now and how you got here.

### Step 1: Copy Template
```bash
cp project-templates/memory.md /path/to/project/
```

### Step 2: Document Current State

Fill in the "Current State" section:
```markdown
## Current State

**Version**: [Check package.json, git tag, or current sprint]
**Last Updated**: [Today's date]
**Status**: Production / In Development / Maintenance

### What's Working
- User authentication with JWT
- Payment processing via Stripe
- Admin dashboard
- Email notifications

### Known Issues
- Slow database queries on reports page
- File uploads fail for files > 50MB
- Mobile UI needs polish

### In Progress
- Adding two-factor authentication
- Migrating to newer API version
```

### Step 3: Add Key History

You don't need complete history. Add 3-5 major milestones:

```markdown
## Implementation History

### 2024-01-15 - Initial Launch
**What was built**: MVP with user accounts, basic dashboard, payment flow
**Why**: Needed to validate market fit quickly
**Key changes**: Set up AWS infrastructure, Stripe integration, React frontend

### 2024-06-20 - Added Admin Features
**What was built**: Admin dashboard, user management, analytics
**Why**: Growing user base needed support tools
**Files affected**: admin/, components/AdminDashboard.tsx

### 2024-11-03 - Performance Optimization
**What was built**: Database indexing, Redis caching, API optimization
**Why**: Response times were >2s, users complaining
**Impact**: Reduced p95 response time from 2.1s to 320ms
```

**Pro tip**: Check git log for major feature branches:
```bash
git log --all --oneline --graph --since="1 year ago" | head -50
```

### Step 4: Document Current Architecture (Brief)

Add one paragraph in "Architecture Evolution":
```markdown
## Architecture Evolution

### Current Architecture
React SPA frontend hosted on Vercel, Node.js/Express API on AWS ECS, 
PostgreSQL database on RDS, Redis cache on ElastiCache. 
Stripe handles payments, SendGrid for email, S3 for file storage.
```

**Done!** You now have project memory. Update this file after each major change.

---

## Phase 3: Create architecture.md (1-2 hours)

Document the system as it exists today.

### Step 1: Copy Template
```bash
cp project-templates/architecture.md /path/to/project/
```

### Step 2: Focus on These Sections First

#### System Overview
Describe what you have in 2-3 sentences:
```markdown
## System Overview

SaaS analytics platform with React frontend and Node.js backend.
Users connect data sources, run queries, and view dashboards.
Processes ~50K events/day across 200 active customers.

**Architecture Style**: Monolithic API with SPA frontend
**Deployment Model**: Multi-tenant SaaS on AWS
```

#### Core Components
List your main pieces (5-10 components max):
```markdown
## Core Components

### Frontend (React SPA)
**Responsibility**: User interface, dashboards, data visualization
**Technology**: React 18, TypeScript, Tailwind CSS
**Key files**: src/components/, src/pages/
**Deployed**: Vercel

### API Server (Node.js/Express)
**Responsibility**: Business logic, data access, authentication
**Technology**: Node.js 18, Express, TypeScript
**Key files**: api/routes/, api/services/
**Deployed**: AWS ECS (Fargate)

### Database (PostgreSQL)
**Responsibility**: User data, analytics results, configuration
**Technology**: PostgreSQL 15 on AWS RDS
**Scalability**: Currently 50GB, can scale to 1TB
```

#### Key Data Flows
Pick 1-2 critical user flows:
```markdown
## Data Flow

### User Runs Analytics Query

1. **User Action**: Submits query in dashboard
   - Component: QueryBuilder.tsx
   - Validates query syntax client-side

2. **API Processing**: POST /api/queries
   - Component: QueryController
   - Authenticates user, checks quota
   - Queues job in Redis

3. **Background Processing**: Worker picks up job
   - Component: QueryWorker
   - Executes against user's data source
   - Stores results in database

4. **Results Display**: Frontend polls for completion
   - Gets results via GET /api/queries/:id/results
   - Renders in dashboard
```

### Step 3: Use AI to Help

Ask AI to help document your architecture:
```
@architecture.md - Read through the codebase and help me fill in 
the Core Components section. For each major part of the system 
(frontend, backend, database, etc), describe its responsibility, 
technology, key files, and how it scales.
```

**Skip for now**: Future plans, disaster recovery, detailed metrics. Add these later.

---

## Phase 4: Create decisions.md (30-60 minutes)

Document why you made key technical choices.

### Step 1: Copy Template
```bash
cp project-templates/decisions.md /path/to/project/
```

### Step 2: Document 3-5 Major Decisions

Think about:
- Why this tech stack?
- Why this architecture pattern?
- Why this hosting provider?
- Major refactors or rewrites

Example:
```markdown
### ADR-001: Use PostgreSQL Instead of MongoDB

**Date**: 2023-08-15
**Status**: Accepted

**Context**
Needed database for user data, analytics results, and configuration.
Requirements: ACID transactions, complex queries, relationships between entities.
Team has strong SQL experience but limited NoSQL experience.

**Decision**
Use PostgreSQL as primary database, hosted on AWS RDS.

**Consequences**

**Positive**:
- Strong consistency guarantees
- Excellent query optimizer for analytics
- Team expertise reduces risk
- Rich ecosystem (PostGIS, full-text search)

**Negative**:
- Vertical scaling limits (can migrate to sharding later)
- More complex schema migrations vs schema-less
- RDS costs higher than self-hosted

**Alternatives Considered**
- **MongoDB**: Better for flexible schemas, but analytics queries harder
- **MySQL**: Similar to Postgres, but weaker JSON support and full-text search
```

### Step 3: Mine Git History and Slack

Look for past discussions:
```bash
# Find major refactors
git log --all --grep="refactor" --grep="migrate" --since="1 year ago"

# Find dependency changes
git log --all -- package.json requirements.txt
```

Ask the team: "What were our biggest technical debates?"

**Start small**: 3-5 decisions is enough. Add more over time.

---

## Phase 5: Add llms.txt (1-2 hours)

Create AI-readable project map.

### Option A: Let AI Generate It
```bash
cp project-templates/llms.txt /path/to/project/llms.txt
```

Then in Cursor:
```
@llms-txt/LLM_TXT_STANDARDS.md - Generate an optimized llms.txt 
for this project. Scan all files and create descriptions following 
the standards.
```

### Option B: Manual (Start Small)
Focus on the 20% of files that represent 80% of the system:
- Main entry points (index.ts, main.py, app.py)
- Core business logic files
- Important utilities
- Key React components
- Database models

Use the template but only document ~10-20 critical files first. Expand later.

---

## Phase 6: Optional Templates (Add As Needed)

### roadmap.md
Good for: Product-focused teams, external stakeholders
```bash
cp project-templates/roadmap.md /path/to/project/
```
Fill in "Current Focus" and "Recently Completed" first. Skip far-future stuff.

### tasks.md
Good for: Sprint planning, tracking active work
```bash
cp project-templates/tasks.md /path/to/project/
```
Document current sprint only. Don't backfill old sprints.

### testing.md
Good for: Teams scaling up, new contributors
```bash
cp project-templates/testing.md /path/to/project/
```
Document how tests currently work, not how you wish they worked.

### coding-standards.md
Good for: Multi-person teams, onboarding new developers
```bash
cp project-templates/coding-standards.md /path/to/project/
```
Document existing conventions you already follow.

### deployment.md
Good for: Teams with manual deploy processes, SRE/DevOps needs
```bash
cp project-templates/deployment.md /path/to/project/
```
Document current deploy process, not ideal future state.

### api-contracts.md
Good for: API-heavy projects, external integrations
```bash
cp project-templates/api-contracts.md /path/to/project/
```
Document current API conventions and major endpoints.

---

## Maintenance Strategy

### Weekly
- Update `tasks.md` with completed and new tasks
- Note any blockers or decisions needed

### After Each Feature
- Update `memory.md` with what was built
- Add entry to `decisions.md` if you made a significant choice

### Monthly
- Review `architecture.md` for accuracy
- Update `roadmap.md` with completed items
- Check `llms.txt` is current (add new files)

### Quarterly
- Full documentation review
- Archive completed items
- Update metrics and scale numbers

---

## Common Pitfalls

❌ **Don't**: Try to document everything perfectly before starting
✅ **Do**: Start with memory.md and architecture.md, add others gradually

❌ **Don't**: Document what you wish you had
✅ **Do**: Document what actually exists right now

❌ **Don't**: Write documentation and never update it
✅ **Do**: Make updates part of your workflow (commit with code changes)

❌ **Don't**: Make documentation an afterthought
✅ **Do**: Update docs in same PR as code changes

❌ **Don't**: Write for humans only
✅ **Do**: Write for AI agents (clear, specific, structured)

---

## Quick Migration Checklist

**Day 1** (1 hour):
- [ ] Copy cursor/rules.md to .cursor/rules.md
- [ ] Copy memory.md and fill in "Current State"
- [ ] Add 3-5 history entries to memory.md

**Week 1** (3-4 hours):
- [ ] Copy architecture.md and document system overview
- [ ] Add core components to architecture.md
- [ ] Document 1-2 critical data flows

**Week 2** (2-3 hours):
- [ ] Copy decisions.md
- [ ] Document 3-5 major technical decisions
- [ ] Generate or create initial llms.txt

**Week 3+** (ongoing):
- [ ] Add optional templates as needed
- [ ] Update docs with each major change
- [ ] Refine and expand over time

---

## Getting Team Buy-In

**Show value quickly**:
1. Add cursor/rules.md → AI makes better suggestions immediately
2. Add memory.md → New team members get context faster
3. Track one sprint in tasks.md → Visibility into what's happening

**Make it easy**:
- Update docs in same PR as code
- Keep docs in repo (not separate wiki)
- Use AI to help write/update docs

**Start small, prove value, expand**:
Don't mandate all templates day 1. Start with core docs, show how they help, then add more.

---

## Example: Real Migration

**Before**:
- 2-year-old codebase
- README with setup instructions
- No architecture docs
- Tribal knowledge in Slack

**Week 1**: Added memory.md (1 hour)
- Documented current state
- Added 5 major milestones from git history
- Result: New contractor got up to speed 2x faster

**Week 2**: Added architecture.md (2 hours)
- Used AI to help scan codebase
- Documented 8 core components
- Drew 2 data flow diagrams
- Result: Architectural discussions became concrete

**Week 3**: Added decisions.md (1 hour)
- Documented 4 major decisions
- Captured "why MongoDB" discussion from Slack
- Result: Stopped relitigating old choices

**Month 2**: Added remaining templates incrementally
- Result: AI suggestions improved 50%, onboarding time cut in half

---

## Need Help?

**Stuck on what to document?**
Ask AI: "What are the most important files/components in this codebase?"

**Don't know your architecture?**
Ask AI: "Analyze this codebase and describe the system architecture"

**Can't remember past decisions?**
Check: git log, Slack history, old PR discussions, team retrospectives

**Too overwhelming?**
Just start with memory.md. One file is infinitely better than zero.
