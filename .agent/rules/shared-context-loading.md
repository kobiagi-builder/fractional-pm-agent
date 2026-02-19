# Shared Context Loading Rule

## MANDATORY BEHAVIOR

ALL content flows through files. The chat is ONLY for conversation.

This applies in BOTH directions:
- **User -> Agent**: Content shared via `shared/` folder (or other file locations). NEVER through chat.
- **Agent -> User**: Generated content (drafts, posts, analyses) WRITTEN to files. NEVER dumped into chat.

## The Back Channel

```
shared/
└── [files go here - both user inputs AND agent outputs]
```

**Chat** = conversation: questions, feedback, decisions, direction, short summaries.
**Files** = content: blog posts, drafts, articles, research, analyses, generated output.

## INPUT: How the Agent Receives Content

### When the user wants to share content with the agent:

**CORRECT flow**:
```
User: "Review my blog post draft - it's in shared/"
Agent: [reads shared/ directory] → [reads file] → [provides feedback in chat]
```

**WRONG flow**:
```
User: [pastes entire blog post into chat]
Agent: [processes it from chat] ← THIS IS WRONG
```

### If content arrives through chat instead of a file:

**STOP. Do not process it.** Instead:

> "I see you've shared the content directly in the chat. To keep our conversation clean and preserve context, please save it as a file in the `shared/` folder and let me know. I'll read it from there.
>
> Example: Save it as `shared/my-draft.md` and tell me it's ready."

This is not optional. Redirect EVERY time. The user has explicitly requested this workflow.

### When checking for files, look in this order:
1. `shared/` - Primary back channel
2. `customers/[customer-name]/artifacts/` - Customer-specific content
3. `growth/` - Growth and content strategy files
4. Direct file path if the user provides one

## OUTPUT: How the Agent Delivers Content

### When the agent generates content (drafts, posts, analyses, edited versions):

**CORRECT flow**:
```
Agent: [writes draft to shared/drafts/post-title.md]
Agent in chat: "I've written the draft and saved it to shared/drafts/post-title.md.
Key decisions I made: [2-3 bullet summary]. Take a look and let me know your feedback."
```

**WRONG flow**:
```
Agent in chat: "Here's the full blog post draft:

[entire 500-word post dumped into chat]"
← THIS IS WRONG
```

### What goes in chat vs. files:

| In Chat (short) | In Files (long) |
|-----------------|-----------------|
| 2-3 sentence summary of what was created | Full draft/post content |
| Key decisions and trade-offs | Edited versions |
| Questions needing user input | Detailed analysis |
| Feedback highlights (bullet points) | Full review with line-by-line notes |
| Status updates | Generated artifacts |

### File naming for agent output:
- Drafts: `shared/drafts/[topic-slug].md`
- Reviews: `shared/reviews/[topic-slug]-review.md`
- Edited versions: `shared/drafts/[topic-slug]-v2.md`
- Final versions: move to appropriate permanent location (growth/, customers/artifacts/)

## Anti-Patterns (NEVER DO)

- **NEVER** process content that was pasted into chat - redirect to shared/
- **NEVER** dump generated content (posts, drafts, analyses) into chat - write to files
- **NEVER** ask the user to paste content ("Please share the content")
- **NEVER** say "Here's the full draft:" followed by the entire post in chat
- **NEVER** provide line-by-line edits in chat - write the edited version to a file

## Examples

### Example 1: User Shares a Reference Article
```
User: "I saved the CNBC article about Monday.com to shared/. Write a post about it."

Agent:
1. Read shared/ directory → find the article file
2. Read the article from file
3. Write the post draft to shared/drafts/monday-com-moat.md
4. In chat: "Draft saved to shared/drafts/monday-com-moat.md.
   I focused on [angle]. Key points: [2 bullets].
   Want me to adjust the angle or tone?"
```

### Example 2: User Pastes Content in Chat (REDIRECT)
```
User: "Here's my blog post: [500 words of content pasted]"

Agent: "I see you've shared the content directly in chat.
Please save it as a file in shared/ (e.g., shared/my-draft.md)
and let me know. I'll read it from there to keep our conversation clean."
```

### Example 3: Agent Creates Content
```
User: "Write a LinkedIn post about the deep vs. wide product strategy"

Agent:
1. Read growth/content-ideas.md for the narrative angle and outline
2. Write the draft to shared/drafts/deep-vs-wide.md
3. In chat: "Draft saved to shared/drafts/deep-vs-wide.md.
   I used the pain→insight→framework→CTA format.
   Opens with 'Your product serves 5 segments. None of them love it.'
   Ready for your review."
```

### Example 4: Agent Reviews Content
```
User: "Review the post I dropped in shared/"

Agent:
1. Read shared/ → find the post
2. Read the post from file
3. Write detailed review to shared/reviews/[post-name]-review.md
4. In chat: "Review saved to shared/reviews/[post-name]-review.md.
   Top 3 findings:
   - [Finding 1]
   - [Finding 2]
   - [Finding 3]
   Check the review file for the full analysis."
```

## Why This Matters

- **Context window**: Long content in chat wastes tokens and pushes conversation history out
- **Clean conversation**: Chat stays focused on decisions, not content walls
- **Reusability**: Files can be referenced, versioned, and iterated on
- **Traceability**: File-based content has paths and timestamps
- **User's explicit request**: The user has asked for this workflow. Respect it.
