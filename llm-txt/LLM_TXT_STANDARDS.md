# llm.txt Best Practices & Standards

> **Research-backed guidelines for creating effective `llm.txt` files that maximize AI code agent performance.**

Based on research by [Lance Martin](https://rlancemartin.github.io/2025/04/03/vibe-code/), optimized `llm.txt` files outperform vector databases, context stuffing, and standard documentation approaches when working with AI code agents like Claude Code and Cursor.

---

## Why llm.txt Works

**Key Finding**: `llm.txt` is "RAG with full documents as retrieval units" - the LLM reasons directly about file descriptions and decides which documents to retrieve.

**Performance Hierarchy** (from research):
1. ✅ **Optimized llm.txt** - 95% success rate
2. ⚠️ Vector Database - 85% success rate  
3. ⚠️ Standard llm.txt - 80% success rate
4. ❌ Context Stuffing - 70% success rate

**Why it wins**: Clear, consistent descriptions allow LLMs to make intelligent retrieval decisions rather than relying on semantic search or processing massive context windows.

---

## Core Principles

### 1. **Optimized Descriptions Are Critical**

The difference between standard and optimized `llm.txt` is description quality:

- ❌ **Bad**: `file.py - Contains utility functions`
- ✅ **Good**: `file.py - Read this file to understand how user authentication is handled, including password hashing with bcrypt, session token generation, and JWT validation. Essential for implementing login/logout functionality.`

### 2. **Consistent Format**

Use a predictable structure so LLMs can quickly parse and reason:

```
### path/to/file.ext
Verb-based description explaining WHEN to read this file, WHAT you'll learn, and WHY it matters.
```

### 3. **Reasoning-Friendly Language**

Write descriptions that help LLMs make decisions:
- Start with action verbs: "Read this file to...", "Reference this file for...", "Use this file when..."
- Explain the "why": "Essential for...", "Required when...", "Useful if..."
- Be specific: Name actual functions, classes, concepts, not generic terms

---

## File Description Template

Use this template for each file in your `llm.txt`:

```markdown
### path/to/file.ext
[Opening statement with file purpose]. Read this file to understand [primary concept 1], [primary concept 2], and [primary concept 3]. [When to use this file - specific scenarios]. [What specific functions/classes/features are covered]. [Any dependencies or related files].
```

**Example**:
```markdown
### backend/auth/jwt_handler.py
JWT token management and validation system. Read this file to understand how authentication tokens are generated using PyJWT, how tokens are validated and refreshed, and how expiration is handled. Use this file when implementing protected API endpoints that require user authentication. Includes `generate_token()`, `validate_token()`, and `refresh_token()` functions. Works with the User model from models/user.py.
```

---

## Structure Guidelines

### 1. Project Overview (Top Section)

```markdown
# Project Name

> One-sentence description of what this project does and its core technology.

## Project Overview

**Tech Stack**: [Key technologies]
**Status**: [Development stage]
**Purpose**: [What problem this solves]
```

### 2. Core Documentation Section

List the most important documentation files first:

```markdown
## Core Documentation

### README.md
[When to read, what you'll learn, why it matters]

### SETUP_GUIDE.md
[When to read, what you'll learn, why it matters]

### API_DOCUMENTATION.md
[When to read, what you'll learn, why it matters]
```

### 3. Organized by Functional Area

Group related files together:

```markdown
## Authentication & Authorization

### auth/login.py
[Description]

### auth/middleware.py
[Description]

## Database Layer

### models/user.py
[Description]

### migrations/001_initial.sql
[Description]
```

### 4. Key Concepts Section

Explain architectural patterns, workflows, or important concepts:

```markdown
## Key Concepts

**Authentication Flow**: 
1. User submits credentials to /login endpoint
2. Server validates against database
3. JWT token generated and returned
4. Client includes token in Authorization header
5. Middleware validates token on protected routes

**Database Schema**: Users table connects to Profiles via foreign key, Sessions table tracks active logins, Audit_Log records all authentication events.
```

### 5. Common Tasks Section

Provide quick reference for frequent operations:

```markdown
## Common Tasks

**To add a new API endpoint**: Create route in api/routes.py, add handler function, update OpenAPI schema in api/schema.yaml.

**To modify database schema**: Create migration file in migrations/, test locally with `npm run migrate:dev`, deploy with `npm run migrate:prod`.

**To add authentication to endpoint**: Import `@require_auth` decorator from auth/middleware.py, apply to route function.
```

---

## Optimization Checklist

Use this checklist to audit your `llm.txt`:

### Content Quality
- [ ] Every file has a description
- [ ] Descriptions explain WHEN to read the file (use cases)
- [ ] Descriptions explain WHAT you'll learn (specific concepts)
- [ ] Descriptions mention specific functions/classes/features (not generic)
- [ ] Related files are cross-referenced
- [ ] Dependencies are noted

### Structure
- [ ] Project overview at top with tech stack
- [ ] Files grouped by functional area
- [ ] Most important files listed first
- [ ] Consistent formatting throughout
- [ ] Key concepts section explains workflows
- [ ] Common tasks section provides quick reference

### Clarity
- [ ] No vague terms ("handles things", "manages stuff")
- [ ] Active voice, not passive ("Read this file" not "This file contains")
- [ ] Specific examples included where helpful
- [ ] Technical terms explained on first use
- [ ] Acronyms spelled out

### Completeness
- [ ] All source code files included
- [ ] All documentation files included
- [ ] All configuration files explained
- [ ] Migration/setup scripts documented
- [ ] Test files referenced (if relevant)

---

## Anti-Patterns to Avoid

### ❌ Too Generic
```markdown
### utils.py
Contains utility functions.
```

### ✅ Specific and Actionable
```markdown
### utils.py
Helper functions for data processing. Read this file to understand date formatting with `format_date()`, string sanitization with `clean_input()`, and file path validation with `validate_path()`. Use these functions throughout the application for consistent data handling.
```

---

### ❌ Missing Context
```markdown
### auth.py
Authentication module.
```

### ✅ Full Context
```markdown
### auth.py
User authentication and session management. Read this file to understand password hashing with bcrypt, login/logout flow, session token generation, and token validation middleware. Required for implementing protected routes and user management features. Connects to the users table in database.
```

---

### ❌ Listing Without Explanation
```markdown
### api/
- users.py
- posts.py
- comments.py
```

### ✅ Descriptive Listings
```markdown
## API Endpoints

### api/users.py
User management endpoints (GET, POST, PUT, DELETE /users). Read this file to understand CRUD operations for users, including registration, profile updates, and account deletion. Uses User model from models/user.py.

### api/posts.py
Post management endpoints (GET, POST, PUT, DELETE /posts). Read this file for content creation, editing, and deletion workflows. Includes pagination, filtering by author/date, and markdown rendering.
```

---

## Maintenance

### When to Update

Update your `llm.txt` whenever you:
- Add new files or modules
- Change architecture or workflows
- Add major features
- Refactor file organization
- Update dependencies or tech stack

### Version Control

```markdown
**Last Updated**: [Date]
**Project Version**: [Semantic version]
**Major Changes**: [What changed since last update]
```

---

## Size Guidelines

**Optimal file size**: 5,000 - 20,000 tokens

- **Too small** (<5k tokens): Missing critical context, LLM makes wrong assumptions
- **Too large** (>20k tokens): Retrieval becomes less efficient, dilutes important information

**If too large**:
- Split into multiple `llm.txt` files by domain (frontend.llm.txt, backend.llm.txt)
- Focus on high-level descriptions, link to detailed docs
- Remove redundant explanations

**If too small**:
- Add more specific examples to descriptions
- Include code snippets in Key Concepts section
- Explain architectural decisions
- Add troubleshooting section

---

## Example: Well-Optimized Entry

```markdown
### backend/api/payment_processing.py
Stripe payment integration with webhook handling. Read this file to understand how payment intents are created using the Stripe API, how webhook events are verified and processed (payment.succeeded, payment.failed, refund.created), and how transactions are logged to the payments table. Essential when implementing checkout flows, subscription billing, or handling payment failures. Includes `create_payment_intent()`, `process_webhook()`, `handle_refund()`, and `verify_webhook_signature()`. Requires STRIPE_SECRET_KEY and STRIPE_WEBHOOK_SECRET in environment variables. Payment records stored in models/payment.py. All transactions logged to activity_log table for compliance.
```

**Why this works**:
- ✅ Clear primary purpose (Stripe integration)
- ✅ Specific use cases (checkout, subscriptions, failures)
- ✅ Named functions (LLM knows what to look for)
- ✅ Dependencies mentioned (env vars, other files)
- ✅ Security context (webhook verification, compliance)

---

## Research References

This guide is based on empirical research comparing code agent performance across different context retrieval methods:

**Source**: [Vibe Code Benchmark by Lance Martin](https://rlancemartin.github.io/2025/04/03/vibe-code/)

**Key Findings**:
- Optimized `llm.txt` achieved 95% success rate on coding challenges
- Most errors with context stuffing were hallucinated APIs (6/11 errors)
- Clear descriptions enable better retrieval decisions
- LLMs can "reason" about which documents to retrieve when given good descriptions

---

## Quick Start

**To create an optimized `llm.txt` for your project**:

1. **Inventory**: List all source files, docs, configs
2. **Prioritize**: Identify the 20% of files that explain 80% of functionality
3. **Describe**: Use the template above for each file
4. **Group**: Organize by functional area
5. **Explain**: Add Key Concepts and Common Tasks sections
6. **Review**: Run through the Optimization Checklist
7. **Test**: Ask an AI to solve a task using only your `llm.txt`
8. **Iterate**: Refine descriptions based on AI performance

---

## Tools

**To optimize existing `llm.txt`**:
- Use an LLM to read each file and generate descriptions
- Ask: "Read [filename] and explain: what it does, when to use it, key functions/classes, dependencies"
- Review and refine for consistency
- Cross-reference related files

**Example prompt for optimization**:
```
Read the file at [path/to/file]. Generate an optimized llm.txt description following this format:

"[Brief purpose statement]. Read this file to understand [3-5 specific concepts/features]. [When to use/scenarios]. [Key functions/classes by name]. [Dependencies and related files]."

Make it specific, actionable, and focused on helping an AI code agent decide when to retrieve this file.
```

---

**Summary**: Invest time in clear, specific, well-structured descriptions. The quality of your `llm.txt` directly impacts AI code agent performance.

