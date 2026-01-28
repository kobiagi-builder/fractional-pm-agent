# Artifacts Folder

This folder contains all work products, analyses, designs, and deliverables created for [Customer Name].

## Naming Convention

Use descriptive, searchable names:

```
[type]-[topic]-[date or version].md

Examples:
- analysis-churn-2025-01.md
- roadmap-q2-2025-v1.md
- prioritization-mobile-features-2025-01-28.md
- research-competitor-acme-2025-01.md
- design-onboarding-flow-v2.md
- interview-synthesis-q1-2025.md
```

## Artifact Types

| Type | Prefix | Description |
|------|--------|-------------|
| Analysis | `analysis-` | Data analysis, metrics reviews |
| Prioritization | `prioritization-` | RICE scores, priority lists |
| Roadmap | `roadmap-` | Product roadmaps |
| Research | `research-` | Competitive, market, user research |
| Design | `design-` | Wireframes, flows, specs |
| Interview | `interview-` | Interview guides, syntheses |
| Strategy | `strategy-` | Strategic documents |
| Presentation | `presentation-` | Decks and presentation materials |
| Report | `report-` | Status reports, summaries |
| Workshop | `workshop-` | Workshop outputs and materials |

## Artifact Header Template

Every artifact should start with:

```markdown
# [Artifact Title]

**Customer**: [Customer Name]
**Created**: [YYYY-MM-DD]
**Last Updated**: [YYYY-MM-DD]
**Type**: [Type from list above]
**Status**: [Draft / In Review / Final]
**Author**: [Name]

---

## Context

[Why was this artifact created? What problem does it solve?]

---

[Main content...]
```

## Version Control

- For evolving documents, use version suffixes: `-v1`, `-v2`, etc.
- For time-bound documents, use date suffixes: `-2025-01`, `-q2-2025`
- Keep previous versions for reference (don't delete)

## Linking

When referencing artifacts in other documents, use:
- Relative links: `See [Roadmap Q2](artifacts/roadmap-q2-2025-v1.md)`
- In event-log: Note which artifacts were created/updated
