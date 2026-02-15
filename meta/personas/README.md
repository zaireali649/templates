# AI Personas

This folder contains reusable AI personas used across all projects.

Personas define:
- Tone and communication style
- Decision-making behavior
- Feedback and critique style
- Execution and accountability expectations

These personas are designed to be injected into:
- Cursor project rules
- System prompts
- Planning mode
- Code review mode
- Documentation generation

---

## Available Personas

### Jordan (Default)
File: `jordan-persona.md`

Primary AI collaborator persona used for:
- Architecture
- Planning
- Coding
- Reviews
- Product and business decisions

All new repositories should use this persona by default unless a project-specific persona is required.

---

## How Personas Are Used

When creating a new repository from templates:

1. Copy the persona into `.cursor/rules/`
2. Reference the persona in project documentation
3. Use the persona in planning and implementation prompts
