# Fractional PM Assistant

An AI agent that helps fractional Product Managers manage multiple customers, maintain obsessive documentation, and orchestrate specialized capabilities for PM work.

## What It Does

The Fractional PM Assistant acts as your always-on PM partner that:

1. **Maintains Customer Context** - Keeps comprehensive, always-current documentation for each customer (company info, financials, event logs, artifacts)
2. **Enforces Documentation Discipline** - Automatically updates customer files after every interaction
3. **Orchestrates Expert Work** - Delegates specialized tasks to focused sub-agents (research, analysis, design)
4. **Self-Evolves** - Builds new capabilities as your needs grow

## Architecture: Skills vs Capabilities

We use a **hybrid architecture** that separates concerns by complexity and autonomy:

```
┌─────────────────────────────────────────────────────────────────┐
│                     FRACTIONAL PM ASSISTANT                      │
├─────────────────────────────────────────────────────────────────┤
│  RULES (Auto-Behaviors)                                         │
│  • Always load customer context before work                     │
│  • Always update docs after interactions                        │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│  SKILLS (Lightweight, Inline)          │  CAPABILITIES (Expert, │
│  • build-agent                         │   Autonomous)          │
│  • load-customer-context               │                        │
│  • update-customer-docs                │  PM Work Capabilities: │
│                                        │  • user-interviews     │
│  Quick tasks, <1 min                   │  • data-analyst        │
│  Run inline in conversation            │  • competition-research│
│  Internal operations                   │  • prioritization      │
│                                        │  • flow-designer       │
│                                        │  • ux-ui-designer      │
│                                        │                        │
│                                        │  Practice Capabilities:│
│                                        │  • sales-advisor       │
│                                        │  • marketing-advisor   │
│                                        │  • relationship-advisor│
│                                        │                        │
│                                        │  Deep work, 1+ min     │
│                                        │  Run autonomously      │
│                                        │  Expert domain work    │
└─────────────────────────────────────────────────────────────────┘
```

### Why the Separation?

| Aspect | Skills | Capabilities |
|--------|--------|--------------|
| **Execution** | Inline, same conversation | Autonomous sub-agent |
| **Duration** | Quick (<1 min) | Extended (1+ min) |
| **Focus** | Internal operations | Expert domain work |
| **Context** | Shares main context | Isolated, focused context |
| **Use Case** | Doc updates, loading context | Research, analysis, design |

**Skills** are for things that should happen quickly and stay in the flow of conversation - like updating a customer file or loading context.

**Capabilities** are for deep work that benefits from isolation and focus - like conducting competitive research or designing user flows. They run as sub-agents with their own context.

## Structure

```
fractional_pm_agent/
├── .agent/
│   ├── AGENT.md                    # Main agent definition
│   ├── rules/                      # Auto-enforced behaviors
│   │   ├── customer-context-loading.md
│   │   └── obsessive-documentation.md
│   ├── skills/                     # Lightweight inline tasks
│   │   ├── build-agent/            # Meta-skill: add new capabilities
│   │   ├── load-customer-context/  # Load customer files into memory
│   │   └── update-customer-docs/   # Update customer documentation
│   └── capabilities/               # Expert sub-agents
│       ├── user-interviews-analyst/  # PM Work
│       ├── data-analyst/
│       ├── competition-researcher/
│       ├── prioritization-analyst/
│       ├── flow-designer/
│       ├── ux-ui-designer/
│       ├── sales-advisor/            # Practice Development
│       ├── marketing-advisor/
│       └── relationship-advisor/
└── customers/
    ├── .template/                  # Template for new customers
    └── [customer-name]/            # Customer-specific folders
        ├── customer-info.md
        ├── financials.md
        ├── event-log.md
        └── artifacts/
```

## Current Capabilities

### Skills (Internal Operations)

| Skill | Purpose |
|-------|---------|
| **build-agent** | Meta-skill to add new rules, skills, or capabilities. Always asks for guidelines before creating. |
| **load-customer-context** | Reads all customer files and provides context summary |
| **update-customer-docs** | Systematically updates customer files after interactions |

### Capabilities (Expert Sub-Agents)

#### PM Work Capabilities
Help deliver work FOR customers:

| Capability | Expertise |
|------------|-----------|
| **user-interviews-analyst** | Interview design, facilitation, thematic analysis, persona building |
| **data-analyst** | Product analytics, metrics, A/B testing, dashboards |
| **competition-researcher** | Competitive intelligence, market analysis, battle cards |
| **prioritization-analyst** | RICE framework, opportunity scoring, roadmap planning |
| **flow-designer** | User flows, journey maps, service blueprints |
| **ux-ui-designer** | Wireframes, interaction specs, design systems |

#### Practice Development Capabilities
Help grow the fractional PM practice:

| Capability | Expertise |
|------------|-----------|
| **sales-advisor** | Lead qualification, proposal development, objection handling, closing strategy |
| **marketing-advisor** | Personal branding, content strategy, lead generation, thought leadership |
| **relationship-advisor** | Account health, difficult conversations, renewals, boundary setting |

## Rules (Always Active)

1. **Customer Context Loading** - MUST load customer folder before any customer-specific work
2. **Obsessive Documentation** - MUST update customer files after every interaction

## The Build-Agent Skill

The `build-agent` skill is the meta-skill that allows the agent to evolve. When you need a new capability:

1. Describe what you need
2. The skill determines if it should be a **Rule**, **Skill**, or **Capability**
3. It **always asks you for guidelines** before creating anything
4. Creates the new component with your specifications

**Decision Framework:**

```
Does it need to happen automatically, without user invocation?
├── YES → RULE
└── NO → Is it lightweight and quick (<1 min)?
    ├── YES → SKILL
    └── NO → CAPABILITY
```

## Development Roadmap

### Planned Capabilities

As the practice grows, we'll add capabilities for:

- **Market Research** - TAM/SAM/SOM analysis, trend research
- **Stakeholder Mapping** - Org charts, influence maps, communication plans
- **Workshop Facilitation** - Session design, templates, synthesis
- **Roadmap Builder** - Timeline visualization, dependency mapping
- **Metrics Dashboard Designer** - KPI definition, dashboard specs
- **Go-to-Market Strategist** - Launch planning, channel strategy
- **Technical Writer** - PRDs, specs, documentation
- **Customer Success Analyst** - Health scoring, churn analysis

### Planned Skills

- **generate-weekly-report** - Auto-generate status reports
- **create-meeting-agenda** - Prepare agendas from context
- **summarize-customer** - Quick customer briefing
- **export-artifacts** - Package deliverables for sharing

### Planned Integrations

- **Calendar sync** - Auto-log meetings
- **Notion/Confluence** - Sync documentation
- **Slack/Teams** - Capture async discussions
- **Linear/Jira** - Track action items

## Usage

### Starting Work with a Customer

```
User: "Let's work on SolarDefend"
Agent: [Loads customer context]
       "I've loaded SolarDefend's context. [Summary]. What would you like to focus on?"
```

### After Any Customer Interaction

```
Agent: [Automatically updates docs]
       "Updated SolarDefend's documentation:
        - customer-info.md: Added pilot progress
        - event-log.md: Logged today's call"
```

### Requesting Expert Work

```
User: "I need competitive analysis for SolarDefend"
Agent: [Invokes competition-researcher capability]
       [Sub-agent performs deep research]
       [Saves to artifacts/]
       "Completed competitive analysis. Saved to artifacts/research-competitors-2025-01.md"
```

### Adding New Capabilities

```
User: "I need the agent to help with pricing strategy"
Agent: [Invokes build-agent skill]
       "This should be a CAPABILITY because it requires strategic analysis.
        Before I create it, I need some guidelines:
        1. What pricing frameworks should it use?
        2. Should it factor in competitive pricing?
        ..."
```

## Philosophy

1. **Documentation is a superpower** - The agent is obsessive about keeping records current
2. **Context is king** - Always load full context before customer work
3. **Right tool for the job** - Skills for quick ops, Capabilities for deep work
4. **Evolve with use** - Build new capabilities as needs emerge
5. **Guidelines matter** - Always ask before creating new components

## License

Private - Internal use only
