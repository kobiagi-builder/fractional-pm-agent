# Update Customer Docs Skill

## Purpose

Systematically update all relevant customer documentation files after any customer interaction. Ensures the obsessive documentation rule is properly executed.

## When to Use

This skill is invoked:
- Automatically after customer interactions (per obsessive-documentation rule)
- Manually when user says "update [customer] docs"
- After any capability produces output for a customer

## Invocation

```
# Automatic (triggered by rule)
[After customer conversation ends]
Agent: "Let me update [Customer]'s documentation..."

# Manual
User: "Update Acme's docs with what we discussed"
Agent: "I'll use the update-customer-docs skill to capture everything."
```

## Workflow

### Step 1: Identify Customer
Determine which customer's files need updating.
- Customer folder: `/customers/[customer-name]/`

### Step 2: Analyze What Changed
Review the interaction/conversation to identify:

**New Information Categories:**
- [ ] Company/team changes → customer-info.md
- [ ] Strategy/vision updates → customer-info.md
- [ ] Product updates → customer-info.md
- [ ] Challenge/priority changes → customer-info.md
- [ ] Financial updates → financials.md
- [ ] Events/meetings → event-log.md
- [ ] Ideas/opportunities → ideas.md
- [ ] Action items → action-items.md
- [ ] Artifacts created → artifacts/

### Step 3: Read Current Files
Load the current state of files that need updating:
- Read customer-info.md (if info changes)
- Read financials.md (if financial changes)
- Read event-log.md (for new entries)
- Read ideas.md (for new ideas)
- Read action-items.md (for action item updates)
- List artifacts/ (to avoid duplicates)

### Step 4: Prepare Updates

**For customer-info.md:**
- Identify which section(s) need updating
- Preserve existing structure
- Add/modify only changed information
- Note the update date in relevant sections

**For financials.md:**
- Add new payment entries
- Update agreement terms if changed
- Add notes about financial discussions

**For event-log.md:**
- Create new entry at TOP of events section
- Use standard event format (see below)
- Include ALL required fields

**For ideas.md:**
- Create new idea entry at TOP of ideas section
- Use standard idea format (see below)
- Include ALL required fields
- Update the "Ideas by Status" summary table

**For action-items.md:**
- Create new action items in appropriate status section (Open)
- Use standard action item format (see below)
- Assign unique ID (AI-XXX, incrementing from Next Available ID)
- Update existing items when progress is made or status changes
- Move items between sections when status changes
- Update Summary Dashboard counts and tables
- Link action items to source event in event-log.md
- Update "Next Available ID" after adding new items

**For artifacts/:**
- Determine appropriate filename: `[topic]-[date].md` or `[topic]-v[N].md`
- Use clear, searchable names
- Include metadata header in artifact

### Step 5: Execute Updates
Write the updates to appropriate files.

### Step 6: Confirm Updates
Report what was updated:
```
Updated [Customer]'s documentation:
- customer-info.md: [what changed]
- event-log.md: Added [event type] entry for [date]
- ideas.md: Added idea "[idea title]"
- action-items.md: Added [AI-XXX] "[title]" / Updated [AI-XXX] status to [status]
- artifacts/: Created [filename]
```

## Event Log Entry Format

```markdown
### [YYYY-MM-DD] [Event Type]: [Brief Title]

**Participants**: [Names and roles]
**Duration**: [Time spent, if applicable]

**Context/Why**:
[What prompted this event? Background context.]

**What Happened**:
[Detailed description of the event, discussion points, activities]

**Decisions Made**:
- [Decision 1 with rationale]
- [Decision 2 with rationale]

**Action Items**:
- [ ] [Task] - Owner: [Name] - Due: [Date]
- [ ] [Task] - Owner: [Name] - Due: [Date]

**Lessons Learned**:
[Insights, things to remember, what worked/didn't work]

**Consequences/Follow-up**:
[What happens next? Dependencies created? Future implications?]

---
```

## Idea Entry Format

```markdown
### [YYYY-MM-DD] [Idea Title]

**Status**: [New / Under Consideration / Approved / Rejected / Implemented / Parked]

**Description**:
[Clear description of the idea - what is it and what problem does it solve?]

**References**:
- [Link, article, conversation, or source that inspired this idea]
- [Related internal documents or artifacts]

**Pros**:
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

**Cons**:
- [Drawback 1]
- [Drawback 2]
- [Drawback 3]

**Risks**:
- [Risk 1 with potential impact]
- [Risk 2 with potential impact]

**Right Timing**:
[When is the right time to pursue this? What conditions need to be true? What dependencies exist?]

**Action Items**:
- [ ] [Next step to explore or validate this idea] - Owner: [Name] - Due: [Date]

---
```

## Action Item Entry Format

```markdown
### [AI-XXX] [Action Item Title]

**Status**: [Open / In Progress / Blocked / Completed / Cancelled]
**Priority**: [Critical / High / Medium / Low]
**Owner**: [Name]
**Created**: [YYYY-MM-DD]
**Due**: [YYYY-MM-DD]
**Completed**: [YYYY-MM-DD or -]

**Source**: [Link to event-log entry or meeting that created this item]

**Description**:
[Clear description of what needs to be done]

**Acceptance Criteria**:
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

**Dependencies**:
- [Dependency 1 - status]
- [Dependency 2 - status]

**Progress Notes**:
| Date | Update |
|------|--------|
| [YYYY-MM-DD] | [Progress update] |

**Blockers** (if any):
- [Blocker description and what's needed to unblock]

**Outcome** (when completed):
[What was delivered? Any follow-up items created?]

---
```

### Action Item Statuses

| Status | Meaning |
|--------|---------|
| `Open` | Not yet started |
| `In Progress` | Actively being worked on |
| `Blocked` | Cannot proceed - dependency or issue |
| `Completed` | Done and verified |
| `Cancelled` | No longer needed |

### Action Item Priorities

| Priority | Response Time |
|----------|---------------|
| `Critical` | Same day |
| `High` | Within 2-3 days |
| `Medium` | Within 1 week |
| `Low` | When possible |

## Artifact File Format

```markdown
# [Artifact Title]

**Customer**: [Customer Name]
**Created**: [YYYY-MM-DD]
**Last Updated**: [YYYY-MM-DD]
**Type**: [Analysis | Design | Roadmap | Prioritization | Research | Other]
**Status**: [Draft | In Review | Final]

---

## Context

[Why was this artifact created? What problem does it solve?]

## [Main Content Sections]

[Artifact-specific content...]

---

## Revision History

| Date | Changes | Reason |
|------|---------|--------|
| YYYY-MM-DD | Initial version | [Reason] |
```

## Update Guidelines

### What to Capture

**Always capture:**
- Explicit decisions made
- Action items with owners
- New information about the customer
- Changes to priorities or strategy
- Meeting/event metadata
- Ideas and opportunities mentioned

**Capture when significant:**
- Discussion points that inform future work
- Stakeholder sentiment or concerns
- Blockers or risks identified
- Dependencies discovered
- Potential opportunities or improvements discussed

### How to Write

**Be specific:**
- Bad: "Discussed the roadmap"
- Good: "Reviewed Q2 roadmap, agreed to prioritize mobile app over web dashboard due to user research showing 73% mobile usage"

**Include context:**
- Bad: "Decided to delay launch"
- Good: "Decided to delay launch by 2 weeks (new date: March 15) because QA found 3 critical bugs in payment flow"

**Preserve nuance:**
- Bad: "CEO approved the plan"
- Good: "CEO approved the plan with reservations about timeline; wants weekly check-ins to track progress"

## Examples

### Example 1: After a Strategy Meeting

```markdown
### 2025-01-28 Meeting: Q2 Strategy Review

**Participants**: John (CEO), Sarah (Product), Me
**Duration**: 90 minutes

**Context/Why**:
Quarterly planning cycle - needed to align on Q2 priorities before budget allocation meeting next week.

**What Happened**:
- Reviewed Q1 results: 15% growth vs 20% target
- Identified mobile experience as key gap (NPS feedback)
- Debated build vs buy for analytics dashboard
- Sarah presented user research from December

**Decisions Made**:
- Prioritize mobile app redesign in Q2 (build in-house)
- Defer analytics dashboard to Q3 (consider buying solution)
- Hire 2 additional engineers for mobile team

**Action Items**:
- [ ] Create mobile redesign PRD - Owner: Me - Due: 2025-02-04
- [ ] Research analytics vendors - Owner: Sarah - Due: 2025-02-07
- [ ] Draft job descriptions - Owner: John - Due: 2025-02-03

**Lessons Learned**:
- Should have shared Q1 metrics before meeting - would have saved 20 min
- User research was compelling - use more data in future presentations

**Consequences/Follow-up**:
- Mobile redesign will be main PM focus for Q2
- Need to update roadmap and communicate to stakeholders
- Budget meeting on Feb 1 will need updated projections
```

### Example 2: Quick Update Call

```markdown
### 2025-01-28 Call: Payment Bug Update

**Participants**: Sarah (Product), Me
**Duration**: 15 minutes

**Context/Why**:
Following up on critical payment bug reported yesterday.

**What Happened**:
- Bug has been identified and fixed
- Root cause: timezone handling in subscription renewal
- Fix deployed to staging, production deploy tomorrow AM

**Decisions Made**:
- Will notify affected users after production deploy
- Adding monitoring alert for payment failures

**Action Items**:
- [ ] Draft user notification email - Owner: Sarah - Due: 2025-01-28
- [ ] Set up payment failure alert - Owner: Engineering - Due: 2025-01-29

**Lessons Learned**:
- Timezone bugs are recurring - need systemic fix

**Consequences/Follow-up**:
- Watch payment metrics closely for 48 hours post-deploy
- Add timezone testing to QA checklist
```

## Error Handling

**If customer folder doesn't exist:**
- Create it using template structure
- Log event as "Customer onboarding"

**If file format is corrupted:**
- Back up current file
- Reconstruct from template
- Note the issue in event log

**If update conflicts with existing info:**
- Preserve old info with strikethrough or "Previously" note
- Add new info with date
- Document the change reason
