# Operating Rhythm for AI Template Repository

This document defines how the AI template repository is used and
maintained over time. It ensures the system compounds instead of
becoming shelfware.

This file is not copied into downstream projects. It governs how this
repository itself is used.

------------------------------------------------------------------------

# Core Principle

The repository improves through real usage.

Every project using these templates should feed improvements back into
this repository.

This creates a continuous improvement loop.

------------------------------------------------------------------------

# Daily Workflow (During Active Development)

When working inside any project that uses these templates:

Use the following files regularly:

memory.md tasks.md .cursor/rules.md prompts/

Daily habits: - Update memory.md after major changes - Keep tasks.md
current - Use prompt library for structured work - Prefer planning
prompts before coding

Goal: Keep project context fresh so AI performs well.

------------------------------------------------------------------------

# Project Kickoff Ritual

Trigger this at the start of every new project.

Open: meta/new-project-bootstrap.md

Perform the full bootstrap workflow.

This includes: - Copying templates into the new repository - Creating
the .cursor folder - Filling llms.txt placeholders - Running the first
planning prompts

Goal: Start every project consistently.

------------------------------------------------------------------------

# Milestone Retrospective Trigger

Run a retrospective whenever one of these occurs:

-   MVP completed
-   Major feature shipped
-   Client project finished
-   Incident or postmortem completed
-   Large refactor completed

Open: meta/template-retrospective.md

Output: - Improvement ideas - Prompt gaps - Template gaps - Lessons
learned

Goal: Capture insights while they are fresh.

------------------------------------------------------------------------

# Monthly Maintenance Session

Once per month, schedule a 30 to 60 minute session.

Open: meta/system-evolution.md meta/prompt-evolution.md

Tasks:

1.  Review improvement queue
2.  Review prompts that felt weak
3.  Review templates that felt missing or outdated
4.  Update repository with approved improvements
5.  Update llms.txt if structure changed

Goal: Ensure the repository evolves continuously.

------------------------------------------------------------------------

# Quarterly Deep Review

Once every 3 months, perform a deeper review.

Questions to answer:

-   Which templates are rarely used?
-   Which prompts are used constantly?
-   Which prompts should be merged or retired?
-   Are Cursor rules still effective?
-   Are templates still aligned with real projects?

Goal: Prevent bloat and keep the system focused.

------------------------------------------------------------------------

# Annual Review

Once per year:

-   Review entire repository structure
-   Archive outdated prompts and templates
-   Reevaluate folder organization
-   Refresh documentation tone and clarity

Goal: Keep the system modern and relevant.

------------------------------------------------------------------------

# Continuous Improvement Loop

Real projects → Retrospective → Improvements → Template Updates → Better
future projects

This loop is the core of the system.

------------------------------------------------------------------------

# Success Indicators

The system is working if:

-   New projects start faster
-   AI produces better first drafts
-   Less time is spent re-explaining context
-   Prompts feel easier and shorter over time
-   Templates require fewer edits in new repos

------------------------------------------------------------------------

# Final Rule

Use the system consistently. Small improvements compound over time.
