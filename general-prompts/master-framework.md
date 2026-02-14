# MASTER Framework

Comprehensive prompt structure for complex requests.

---

## Template

```
Context: [Background information, current situation]

Objective: [What you want to achieve, success criteria]

Role: [What role/expertise the AI should assume]

Constraints: [Limitations, requirements, boundaries]

Output format: [How you want the response structured]
```

---

## Example Usage

```
Context: 
We're a 50-person SaaS company with a Rails monolith becoming hard to maintain. 
Database queries are slow, deploy times are 20 minutes, and new features take weeks.

Objective: 
Develop a migration plan to microservices that:
- Reduces deploy time to < 5 minutes
- Improves team velocity by 30%
- Doesn't disrupt current operations

Role: 
Act as a senior architect who has successfully led 3+ microservice migrations

Constraints:
- Cannot rewrite everything (must be incremental)
- Team has limited DevOps experience
- Budget for 6 months of effort
- Must maintain 99.9% uptime

Output format:
1. Assessment of current state
2. Target architecture
3. Phased migration plan (6 months)
4. Risk mitigation strategies
5. Success metrics
```

---

## Why This Works

- **Context**: Grounds AI in your reality
- **Objective**: Clear success criteria
- **Role**: Activates relevant expertise
- **Constraints**: Prevents unrealistic suggestions
- **Output**: Gets format you need

---

## When to Use

- Complex strategic questions
- Multi-faceted problems
- Need expert-level guidance
- Lots of context matters
- Specific output format needed
