# [Customer Name] - Action Items

> Central tracking for all action items across customer interactions.
> Items are organized by status, with newest entries at the top within each section.

---

## Action Item Entry Template

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

## Status Reference

| Status | Meaning | Color |
|--------|---------|-------|
| `Open` | Not yet started | 🔵 |
| `In Progress` | Actively being worked on | 🟡 |
| `Blocked` | Cannot proceed - dependency or issue | 🔴 |
| `Completed` | Done and verified | 🟢 |
| `Cancelled` | No longer needed | ⚫ |

## Priority Reference

| Priority | Response Time | Description |
|----------|---------------|-------------|
| `Critical` | Same day | Blocking other work or customer |
| `High` | Within 2-3 days | Important, time-sensitive |
| `Medium` | Within 1 week | Standard priority |
| `Low` | When possible | Nice to have, no urgency |

---

## Summary Dashboard

### By Status

| Status | Count | Items |
|--------|-------|-------|
| 🔵 Open | 0 | - |
| 🟡 In Progress | 0 | - |
| 🔴 Blocked | 0 | - |
| 🟢 Completed (last 30 days) | 0 | - |

### Overdue Items

| ID | Item | Due | Owner | Days Overdue |
|----|------|-----|-------|--------------|
| - | - | - | - | - |

### Upcoming Deadlines (Next 7 Days)

| ID | Item | Due | Owner | Priority |
|----|------|-----|-------|----------|
| - | - | - | - | - |

---

## Open Items

<!-- New open items go here -->

---

## In Progress

<!-- Items currently being worked on -->

---

## Blocked

<!-- Items that cannot proceed -->

---

## Completed

<!-- Completed items, newest first. Archive items older than 90 days -->

---

## Cancelled

<!-- Cancelled items with reason -->

---

## Archive

> Items completed more than 90 days ago are moved here for reference.

---

## ID Assignment

Action Item IDs follow the pattern: `AI-XXX`
- Start at AI-001 for each customer
- Increment sequentially
- Never reuse IDs (even for cancelled items)

**Next Available ID**: AI-001
