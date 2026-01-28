# Obsessive Documentation Rule

## MANDATORY BEHAVIOR

After EVERY customer interaction, you MUST update the relevant customer documentation files. No exceptions. No "I'll do it later." Documentation happens NOW.

## Trigger Conditions

This rule applies after:
- Any conversation about a customer
- Any work product created for a customer
- Any decision made or discussed
- Any meeting, call, or event mentioned
- Any new information learned about a customer
- Any change in customer status, challenges, or priorities

## What Gets Updated

### 1. customer-info.md
Update when you learn:
- New team members or stakeholder changes
- Strategy or vision updates
- Product changes or pivots
- New challenges or resolved challenges
- Market or competitor changes
- Timeline or milestone updates
- New needs or pain points
- Preference or working style discoveries

### 2. financials.md
Update when:
- Payment is made or mentioned
- Pricing discussions occur
- Agreement terms change
- Invoice sent or received
- Budget conversations happen

### 3. event-log.md
**ALWAYS** add an entry for:
- Meetings (scheduled or impromptu)
- Calls (even quick ones)
- Email discussions of significance
- Decisions (big or small)
- Presentations or workshops
- Deliverable handoffs
- Feedback sessions
- Problem escalations
- Wins and celebrations

### 4. artifacts/
Create or update when:
- Any analysis is performed
- Any design is created
- Any prioritization is done
- Any roadmap is built
- Any document is generated
- Any research is compiled

## Event Log Entry Format

Every event MUST include:

```markdown
### [YYYY-MM-DD] [Event Type]: [Title]

**Participants**: [Who was involved]
**Duration**: [How long, if applicable]

**Context/Why**:
[What led to this event? Why now?]

**What Happened**:
[Detailed account of the event]

**Decisions Made**:
- [Decision 1]
- [Decision 2]

**Action Items**:
- [ ] [Action 1] - Owner: [Name] - Due: [Date]
- [ ] [Action 2] - Owner: [Name] - Due: [Date]

**Lessons Learned**:
[What did we learn? What would we do differently?]

**Consequences/Follow-up**:
[What happens next as a result of this event?]
```

## Event Types

Use consistent event type labels:
- `Meeting` - Scheduled meetings
- `Call` - Phone/video calls
- `Workshop` - Collaborative sessions
- `Decision` - Major decisions (even async)
- `Delivery` - Artifact handoffs
- `Feedback` - Customer feedback received
- `Escalation` - Problems raised
- `Win` - Successes and celebrations
- `Update` - Status or information updates
- `Analysis` - Deep dives and research
- `Planning` - Strategy and roadmap sessions

## Completeness Standards

### Minimum Viable Documentation
Even for small interactions, capture:
- Date
- What happened (1-2 sentences minimum)
- Any decisions or action items

### Full Documentation
For significant events, capture ALL fields in the template.

### When in Doubt
**Over-document.** Future you reviewing these files will be grateful for context you might think is "obvious" now.

## Automation Approach

After customer work, follow this sequence:

1. **Identify what changed** - What new information do we have?
2. **Categorize updates** - Which files need updating?
3. **Update files** - Make the actual updates
4. **Confirm updates** - Tell user what was documented

Example confirmation:
> "I've updated [Customer]'s documentation:
> - Added stakeholder notes to customer-info.md
> - Logged today's meeting in event-log.md
> - Saved the prioritization analysis to artifacts/prioritization-q2-2025.md"

## Anti-Patterns (NEVER DO)

- **NEVER** finish customer work without updating docs
- **NEVER** say "I'll remember this" - write it down
- **NEVER** update docs partially - complete all relevant files
- **NEVER** use vague entries like "had a meeting" - be specific
- **NEVER** skip the "why" - context is crucial
- **NEVER** forget action items and their owners

## Quality Checks

Before considering documentation complete, verify:

- [ ] All new information is captured in customer-info.md
- [ ] Event log entry has all required fields filled
- [ ] Any artifacts created are saved with descriptive names
- [ ] Action items have owners and due dates
- [ ] Financial updates (if any) are recorded
- [ ] Dates are accurate (YYYY-MM-DD format)

## Why This Matters

**Documentation is your superpower as a fractional PM:**

1. **Continuity** - Pick up exactly where you left off, even weeks later
2. **Credibility** - Show customers you're tracking everything
3. **Accountability** - Clear record of decisions and who made them
4. **Learning** - Patterns emerge from good documentation
5. **Handoff** - If you ever need to transition, everything is ready
6. **Protection** - Documentation protects both you and the customer

**The cost of NOT documenting:**
- "What did we decide about X?" - awkward
- "Who was supposed to do Y?" - unclear
- "When did they first mention Z?" - unknown
- Trust erodes when things fall through cracks
