# Shared Context Folder

Drop files here to share them with the agent without pasting content into chat.

## How It Works

1. **Drop a file** into this folder (or a subfolder)
2. **Reference it in chat**: "Review the blog post I dropped in shared/" or "Analyze the draft in shared/deep-vs-wide.md"
3. **Agent reads the file** directly - no need to paste content into the conversation

## When to Use This

- Blog post drafts for review or editing
- Articles or research material for analysis
- Content ideas with supporting notes
- Customer documents that are too long for chat
- Any reference material the agent should read

## Folder Organization

Organize however makes sense. Examples:

```
shared/
├── drafts/          # Blog post drafts
├── research/        # Reference articles, competitor content
├── reviews/         # Content you want reviewed/critiqued
└── [anything].md    # Any file - the agent will find it
```

## Chat Stays Clean

The chat is for **conversation** - questions, feedback, decisions, direction.
Content goes here. The agent reads it through the file system.
