# Customer Context Loading Rule

## MANDATORY BEHAVIOR

Before performing ANY work related to a specific customer, you MUST first load that customer's complete context.

## Trigger Conditions

This rule applies whenever:
- User mentions a customer name
- User asks to work on something for a specific customer
- User references "the customer" or "them" in context of previous customer work
- Any task requires customer-specific knowledge

## Required Actions

### Step 1: Identify Customer
Determine the customer name from the conversation context.

### Step 2: Verify Customer Exists
Check if `/customers/[customer-name]/` directory exists.

**If exists:**
- Proceed to Step 3

**If does NOT exist:**
- Ask user: "I don't have records for [Customer Name]. Should I create a new customer folder?"
- If yes, create folder structure using the template
- Gather initial customer information before proceeding

### Step 3: Load All Customer Files
Read ALL files in the customer folder:

```
/customers/[customer-name]/
├── customer-info.md      # REQUIRED - Read first
├── financials.md         # REQUIRED
├── event-log.md          # REQUIRED - Note recent events
└── artifacts/            # Scan for existing artifacts
    └── *.md
```

### Step 4: Summarize Context (Internal)
After loading, mentally note:
- Key stakeholders and their roles
- Current challenges and priorities
- Recent events and decisions
- Existing artifacts and work in progress
- Any relevant financial context

### Step 5: Confirm Ready
Briefly acknowledge context is loaded:
> "I've loaded [Customer Name]'s context. [Brief relevant summary based on task]. How would you like to proceed?"

## Examples

### Example 1: Direct Customer Reference
```
User: "Let's discuss Acme Corp's roadmap"

Agent (internal):
1. Customer = "Acme Corp" ✓
2. Check /customers/acme-corp/ exists ✓
3. Read customer-info.md, financials.md, event-log.md, artifacts/*
4. Note: Q2 planning phase, CEO wants mobile-first, budget concerns
5. Respond with context acknowledgment
```

### Example 2: Implicit Reference
```
User: "What did we decide last week about the feature prioritization?"

Agent (internal):
1. Customer = [from previous context or ask]
2. If unclear: "Which customer are you referring to?"
3. Load context, specifically check event-log.md for last week
4. Respond with specific decision details
```

### Example 3: New Customer
```
User: "I just signed a new customer called TechStart"

Agent:
1. Customer = "TechStart"
2. /customers/techstart/ does not exist
3. "Great! Let me set up TechStart's customer folder. I'll need some initial information..."
4. Create folder structure
5. Gather and save initial info
```

## Anti-Patterns (NEVER DO)

- **NEVER** answer customer-specific questions without loading context first
- **NEVER** assume customer details from memory - always verify against files
- **NEVER** skip loading files because "you remember" from earlier in conversation
- **NEVER** provide outdated information - files are source of truth

## Why This Matters

Customer context is the foundation of effective fractional PM work. Without current, accurate context:
- You might give advice that contradicts previous decisions
- You might miss important stakeholder dynamics
- You might overlook recent events that change the situation
- You lose the trust that comes from being "always prepared"
