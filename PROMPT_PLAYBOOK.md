# Prompt Playbook

This file contains reusable prompts gathered and refined for daily use
with ChatGPT and Cursor.

------------------------------------------------------------------------

# Universal TCREI Prompt Template

TASK:
Here is what I need you to produce:

CONTEXT:
Audience: who it is for
Goal: Here is why
Constraint: the constraints

REFERENCE:
Here are examples, standards, or prior work to match:

EVALUATION:
After you produce the answer, critique it and improve it.

ITERATION:
Ask me what to refine next.


------------------------------------------------------------------------

# Prompt Engineer Prompt

You are a prompt engineer helping me craft the best possible prompt.

Process 1 Ask clarifying questions about the task. 2 Suggest an improved
prompt. 3 Repeat until the prompt is excellent. 4 Execute the final
prompt.

Start by asking what I want to accomplish.

------------------------------------------------------------------------

# Rage Prompt

Do not be vague. Do not overexplain. Ask up to 3 questions if needed.
Then give a clear answer and 5 concrete steps.

------------------------------------------------------------------------

# Systems Architect Prompt

Act as a senior systems architect.

Goal: design a production-ready solution.

Include:
- architecture diagram (text)
- components and responsibilities
- tradeoffs
- scaling plan
- risks and mitigations
- step-by-step implementation plan


------------------------------------------------------------------------

# Startup Cofounder Prompt

Act as my technical co-founder.

For this idea:
1) Clarify the problem.
2) Identify target users.
3) Evaluate market viability.
4) Suggest MVP features.
5) Suggest monetization.
6) Identify biggest risks.
7) Give next 7 actions.


------------------------------------------------------------------------

# Learning Accelerator Prompt

Teach me [topic].

Structure:
1) Explain like I'm 5.
2) Explain at professional level.
3) Real-world example.
4) Hands-on mini project.
5) Common mistakes.
6) 3 key takeaways.


------------------------------------------------------------------------

# Code Debugging Explanation Prompt

Explain this code like I’m debugging it.

Include:
- what it does
- why each part exists
- likely failure points
- how to improve it


------------------------------------------------------------------------

# Self Critique Loop Prompt

Give your best answer.

Then:
1) Critique it like a harsh reviewer.
2) Identify gaps and assumptions.
3) Rewrite a better version.


------------------------------------------------------------------------

# Research Synthesizer Prompt

Create a research briefing.

Include:
- key findings
- consensus
- disagreements
- implications
- action steps


------------------------------------------------------------------------

# Life Systems Engineer Prompt

Act as my life systems engineer.

Design systems for:
- work
- health
- finances
- family
- learning

Make it structured, measurable, and gamified.


------------------------------------------------------------------------

# Speed Summary Prompt

Summarize this into:
- 5 bullet points
- 1 "so what" takeaway


------------------------------------------------------------------------

# Cursor Planning Prompt

Do not write code yet.

Plan the implementation for:
[feature]

Include:
- files to modify
- new files to create
- step-by-step plan
- potential risks


------------------------------------------------------------------------

# Cursor Debug Prompt

Bug:
[describe bug]

Investigate root cause.
Do NOT patch symptoms.
Explain the cause before fixing.


------------------------------------------------------------------------

# Cursor Test First Prompt

Write unit tests for this feature before implementation.

Focus on:
- edge cases
- failure scenarios
- expected behavior

After test approval, Implement the code so these tests pass.

------------------------------------------------------------------------

# Cursor Refactor Prompt

Refactor code to improve readability maintainability and performance. Do
not change behavior. Explain changes first.

------------------------------------------------------------------------

# Cursor PR Prompt

Create a pull request description.

Include Summary Changes made Testing steps Risks

------------------------------------------------------------------------

# The Prompt Engineer Prompt (META prompt)

You are a prompt engineer helping me craft the best possible prompt.

Process:
1) Ask me clarifying questions about the task.
2) Suggest an improved prompt.
3) Repeat until the prompt is excellent.
4) Then execute the final prompt.

Start by asking what I want to accomplish.

------------------------------------------------------------------------

# The Prompt Chaining Pattern (VERY advanced)

Instead of:

“Build a SaaS”

Do:

Prompt 1 → brainstorm ideas
Prompt 2 → validate idea
Prompt 3 → MVP features
Prompt 4 → architecture
Prompt 5 → roadmap


------------------------------------------------------------------------

# The MASTER Framework

Context:
Objective:
Role:
Constraints:
Output format:

------------------------------------------------------------------------

# The “Understand the Codebase” Prompt (FIRST PROMPT ALWAYS)
Study this repository and explain:

- what the application does
- tech stack used
- architecture overview
- key entry points
- how to run locally
- risky or complex areas

------------------------------------------------------------------------

# The “Repository Map” Prompt
Create a mental map of this repo.

Output:
- folder structure summary
- responsibilities of each major folder
- key services/modules and how they interact

------------------------------------------------------------------------

# The “Small Task Splitter”
Break this feature into the smallest safe steps.
Each step should be completable in one prompt.

------------------------------------------------------------------------

# The “Follow Project Rules” Prompt
Implement this feature.
Follow the rules in @architecture.md and @coding-standards.md.

------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------
