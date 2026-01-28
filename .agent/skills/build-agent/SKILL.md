# Build Agent Skill

## Purpose

Meta-skill for evolving the Fractional PM Assistant. Analyzes feature requests, determines the appropriate component type (rule, skill, or capability), gathers guidelines from the user, and creates the new component.

## When to Use

Invoke this skill when:
- User requests a new feature or ability
- User says "I need the agent to..."
- User says "Can you add..."
- User identifies a gap in capabilities
- User wants to automate a recurring task

## Invocation

```
User: "I need the agent to do competitive pricing analysis"
Agent: "I'll use the build-agent skill to add this capability."
```

## Workflow

### Phase 1: Understand the Request

Gather information about what the user needs:

1. **What is the task?** - Clear description of what needs to happen
2. **When does it happen?** - Trigger conditions
3. **What inputs does it need?** - Data, context, parameters
4. **What outputs does it produce?** - Deliverables, artifacts, updates
5. **How complex is it?** - Simple/inline vs. deep/autonomous

### Phase 2: Classify Component Type

Use this decision framework:

```
                    ┌─────────────────────────────────────┐
                    │   Does it need to ALWAYS happen     │
                    │   automatically, without user       │
                    │   invocation?                       │
                    └──────────────┬──────────────────────┘
                                   │
                    ┌──────────────┴──────────────┐
                    │                             │
                   YES                           NO
                    │                             │
                    ▼                             ▼
               ┌────────┐            ┌─────────────────────────────┐
               │  RULE  │            │  Is the task lightweight,   │
               └────────┘            │  quick, and can execute     │
                                     │  inline in conversation?    │
                                     └──────────────┬──────────────┘
                                                    │
                                     ┌──────────────┴──────────────┐
                                     │                             │
                                    YES                           NO
                                     │                             │
                                     ▼                             ▼
                                ┌─────────┐              ┌────────────────┐
                                │  SKILL  │              │  CAPABILITY    │
                                └─────────┘              │  (Sub-Agent)   │
                                                         └────────────────┘
```

**Decision Criteria:**

| Criteria | Rule | Skill | Capability |
|----------|------|-------|------------|
| User invocation needed | No | Yes | Yes |
| Autonomous execution | N/A | No | Yes |
| Execution time | Instant | Quick (<1 min) | Extended (1+ min) |
| Context needed | Minimal | Moderate | Deep |
| Output complexity | Simple | Moderate | Complex |
| Specialized expertise | No | Some | High |
| Can run in background | No | No | Yes |

### Phase 3: Gather Guidelines (MANDATORY)

**ALWAYS ask the user for guidelines before creating the component.**

Ask these questions:

1. **For ALL component types:**
   - "What specific guidelines or constraints should this [rule/skill/capability] follow?"
   - "Are there any edge cases I should handle specially?"
   - "Should this integrate with any existing components?"

2. **For Rules specifically:**
   - "What are the exact trigger conditions?"
   - "What should happen if the rule can't be satisfied?"

3. **For Skills specifically:**
   - "What should the output format look like?"
   - "Are there any templates to follow?"

4. **For Capabilities specifically:**
   - "What expertise or domain knowledge should it have?"
   - "What tools or data sources should it use?"
   - "What quality standards should the output meet?"
   - "Should it follow any specific frameworks or methodologies?"

### Phase 4: Create Component

Based on classification and guidelines, create the appropriate file:

**For Rules:**
```
.agent/rules/[rule-name].md
```

**For Skills:**
```
.agent/skills/[skill-name]/SKILL.md
```

**For Capabilities:**
```
.agent/capabilities/[capability-name]/AGENT.md
```

### Phase 5: Confirm and Document

1. Show the user what was created
2. Explain how to invoke it
3. Update any relevant documentation

## Component Templates

### Rule Template

```markdown
# [Rule Name]

## MANDATORY BEHAVIOR

[Clear statement of what must always happen]

## Trigger Conditions

This rule applies when:
- [Condition 1]
- [Condition 2]

## Required Actions

### Step 1: [Action]
[Description]

### Step 2: [Action]
[Description]

## Examples

### Example 1: [Scenario]
```
[Example of rule in action]
```

## Anti-Patterns (NEVER DO)

- [Anti-pattern 1]
- [Anti-pattern 2]

## Why This Matters

[Explanation of importance]
```

### Skill Template

```markdown
# [Skill Name]

## Purpose

[What this skill does]

## When to Use

Invoke this skill when:
- [Trigger 1]
- [Trigger 2]

## Invocation

```
User: "[Example user request]"
Agent: "[How agent responds]"
```

## Workflow

### Step 1: [Phase Name]
[Description]

### Step 2: [Phase Name]
[Description]

## Inputs

- **[Input 1]**: [Description]
- **[Input 2]**: [Description]

## Outputs

- **[Output 1]**: [Description]
- **[Output 2]**: [Description]

## Guidelines

[User-provided guidelines go here]

## Examples

### Example 1: [Scenario]
[Detailed example]
```

### Capability Template

```markdown
# [Capability Name]

## Identity

You are a [role description] specializing in [domain].

## Expertise

- [Expertise area 1]
- [Expertise area 2]
- [Expertise area 3]

## When to Invoke

Use this capability when:
- [Trigger 1]
- [Trigger 2]

## Workflow

### Phase 1: [Phase Name]
[Description]

### Phase 2: [Phase Name]
[Description]

## Inputs Required

- **[Input 1]**: [Description]
- **[Input 2]**: [Description]

## Outputs Produced

- **[Output 1]**: [Description and format]
- **[Output 2]**: [Description and format]

## Quality Standards

- [Standard 1]
- [Standard 2]

## Methodologies & Frameworks

- [Framework 1]
- [Framework 2]

## Integration

### With Customer Documentation
[How this capability interacts with customer files]

### With Other Capabilities
[How this capability can work with others]

## Guidelines

[User-provided guidelines go here]
```

## Examples

### Example 1: Adding a Rule

```
User: "I need the agent to always check for conflicting action items before adding new ones"

Agent: "I'll analyze this request...

This should be a RULE because:
- It needs to happen automatically, without user invocation
- It's a validation check, not a task
- It should prevent problems before they occur

Before I create this rule, I need some guidelines:
1. What defines a 'conflict'? (Same owner + overlapping dates? Same topic?)
2. What should happen if a conflict is found? (Warn? Block? Ask?)
3. Should this apply to all customers or specific ones?"

User: [Provides guidelines]

Agent: [Creates rule with guidelines incorporated]
```

### Example 2: Adding a Skill

```
User: "I need to generate weekly status reports for customers"

Agent: "I'll analyze this request...

This should be a SKILL because:
- User will invoke it explicitly ('generate status report')
- It's a focused task with clear output
- It doesn't require deep research or extended analysis

Before I create this skill, I need some guidelines:
1. What should the report format look like?
2. What time period should it cover by default?
3. Should it pull from event-log automatically?
4. Any specific sections required?"

User: [Provides guidelines]

Agent: [Creates skill with guidelines incorporated]
```

### Example 3: Adding a Capability

```
User: "I need the agent to do in-depth customer journey mapping"

Agent: "I'll analyze this request...

This should be a CAPABILITY because:
- It requires specialized UX expertise
- It needs extended focus and analysis
- It produces complex artifacts (journey maps)
- It may need to gather additional research

Before I create this capability, I need some guidelines:
1. What journey mapping methodology should it follow? (e.g., service blueprint, experience map)
2. What should the output format be? (Miro board, markdown, specific template?)
3. What stages should it typically cover? (Awareness to advocacy? Custom?)
4. Should it include emotional mapping? Touchpoint analysis?
5. What level of detail is expected?"

User: [Provides guidelines]

Agent: [Creates capability with guidelines incorporated]
```

## Important Notes

1. **Always ask for guidelines** - Never assume. The user's context and preferences matter.
2. **Validate the classification** - Share your reasoning and let user correct if needed.
3. **Keep components focused** - One component = one responsibility.
4. **Consider integration** - How does this fit with existing components?
5. **Document thoroughly** - Future you will need to understand this.
