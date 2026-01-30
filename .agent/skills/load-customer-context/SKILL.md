# Load Customer Context Skill

## Purpose

Efficiently load all customer documentation into working memory before any customer-specific work. Provides a structured summary to confirm context is ready.

## When to Use

This skill is invoked:
- When user mentions they want to work on a specific customer
- Before any customer-specific task
- When switching between customers
- When user asks "what do we know about [customer]?"

## Invocation

```
User: "Let's work on Acme Corp"
Agent: "Loading Acme Corp's context..."
[Skill executes]
Agent: "I've loaded Acme Corp's context. Here's the current state: ..."
```

## Workflow

### Step 1: Identify Customer
Parse customer name from user input.
- Handle variations: "Acme", "Acme Corp", "acme-corp"
- Normalize to folder name format (lowercase, hyphenated)

### Step 2: Verify Customer Exists

**Check:** Does `/customers/[customer-name]/` exist?

**If NO:**
```
"I don't have a customer folder for [Customer Name]. Would you like me to:
1. Create a new customer folder for them
2. Search for similar names (in case of typo)

Which would you prefer?"
```

**If YES:** Proceed to Step 3

### Step 3: Load All Documentation

Read these files in order:

1. **customer-info.md** (PRIMARY)
   - Company overview
   - Team & stakeholders
   - Vision & mission
   - Product details
   - ICP
   - Market context
   - Competitors
   - Challenges
   - Timelines
   - Needs & pain points
   - Preferences

2. **financials.md**
   - Agreement type
   - Pricing
   - Payment status
   - Any financial notes

3. **event-log.md**
   - Recent events (last 30 days focus)
   - Open action items
   - Recent decisions

4. **ideas.md**
   - Active ideas (Under Consideration, Approved)
   - Recently added ideas
   - Parked ideas worth noting

5. **action-items.md**
   - Open action items
   - In Progress items
   - Blocked items (highlight these!)
   - Overdue items (highlight these!)
   - Recently completed items

6. **artifacts/** (list)
   - Available artifacts
   - Recent/active artifacts

### Step 4: Synthesize Context Summary

Create a structured summary for working memory:

```markdown
## [Customer Name] - Context Summary

### Quick Facts
- **Stage**: [Startup/Growth/Enterprise]
- **Industry**: [Industry]
- **Team Size**: [Size]
- **My Role**: [Retainer/Project/Hourly] @ [Rate]
- **Status**: [Active engagement level]

### Key Stakeholders
- [Name] ([Role]) - [Key notes]
- [Name] ([Role]) - [Key notes]

### Current Priorities
1. [Priority 1]
2. [Priority 2]
3. [Priority 3]

### Active Challenges
- [Challenge 1]
- [Challenge 2]

### Recent Activity (Last 30 Days)
- [Date]: [Event summary]
- [Date]: [Event summary]

### Action Items Summary
**Open**: [count] | **In Progress**: [count] | **Blocked**: [count] | **Overdue**: [count]

#### Overdue (URGENT)
- [AI-XXX] [Title] - Due: [Date] - [Days] overdue

#### Blocked (ATTENTION)
- [AI-XXX] [Title] - Blocker: [reason]

#### In Progress
- [AI-XXX] [Title] - Due: [Date] - Owner: [Name]

#### Open (Next Up)
- [AI-XXX] [Title] - Due: [Date] - Priority: [Priority]

### Active Ideas
- [Idea title] - [Status] - [Date]
- [Idea title] - [Status] - [Date]

### Available Artifacts
- [artifact-name.md] - [Type] - [Date]
- [artifact-name.md] - [Type] - [Date]

### Working Preferences
- [Preference 1]
- [Preference 2]
```

### Step 5: Present Summary

Share summary with user:

```
"I've loaded [Customer Name]'s context. Here's the current state:

[Condensed summary - key facts, current priorities, recent activity, open items]

What would you like to focus on?"
```

## Context Summary Levels

### Brief (Default for quick tasks)
```
[Customer] - [Stage] [Industry] company
Key contact: [Name] ([Role])
Current focus: [Top priority]
Last activity: [Date] - [Event]
```

### Standard (Default for work sessions)
Full synthesis as shown in Step 4

### Deep (When user asks for comprehensive view)
Include:
- Complete stakeholder map
- Full challenge analysis
- All open action items
- Recent decision history
- Financial details

## Handling Multiple Customers

If user mentions multiple customers:
```
"You mentioned [Customer A] and [Customer B]. Which would you like to focus on?

Or if you need to compare/reference both, I can load both contexts."
```

## Context Refresh

If user has been working on a customer for a while:
```
User: "Refresh context" / "Reload [customer]"
Agent: [Reloads files, presents updated summary]
```

## Error Handling

**Customer not found:**
- Suggest similar names
- Offer to create new customer

**Incomplete files:**
- Note missing information
- Offer to gather missing info

**Corrupted files:**
- Attempt recovery
- Note issues found
- Offer to rebuild from what's available

## Example Outputs

### Example 1: Standard Context Load

```
User: "Let's work on TechStart"

Agent: "Loading TechStart's context...

TechStart - Context Summary

Quick Facts:
- Series A startup in fintech
- 25-person team
- Retainer engagement @ $8k/month
- Active since October 2024

Key Stakeholders:
- Maria Chen (CEO) - Final decisions, prefers data-driven arguments
- Tom Wilson (CTO) - Technical feasibility, concerns about tech debt
- Lisa Park (Head of Product) - Day-to-day PM partner

Current Priorities:
1. Launch mobile app by March 15
2. Reduce customer churn (currently 8%)
3. Prepare for Series B pitch

Recent Activity:
- Jan 25: Sprint planning - scoped mobile MVP features
- Jan 20: Churn analysis workshop - identified 3 key reasons
- Jan 15: Roadmap review with Maria

Open Action Items:
- [ ] Mobile app PRD - Due: Jan 30 (me)
- [ ] User interview synthesis - Due: Feb 1 (me)

What would you like to focus on?"
```

### Example 2: Customer Not Found

```
User: "Let's work on Acme"

Agent: "I don't have a customer folder for 'Acme'. I found these similar names:
- acme-corp
- acme-solutions

Did you mean one of these? Or should I create a new customer folder for 'Acme'?"
```

### Example 3: Brief Context

```
User: "Quick question about TechStart's timeline"

Agent: "Loading TechStart context...

TechStart - Series A fintech, mobile app launch March 15
Key contact: Lisa Park (Head of Product)
Current focus: Mobile MVP + churn reduction

What's your question about the timeline?"
```

## Notes

- Always load context BEFORE answering customer-specific questions
- Don't assume information from previous conversations - verify against files
- If files are outdated, note this and offer to update
- Context loading should feel instant - don't overload user with information they didn't ask for
