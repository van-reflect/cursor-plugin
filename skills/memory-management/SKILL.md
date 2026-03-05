---
name: memory-management
description: Manage cross-agent memories through Reflect Memory. Use when the user asks to save project state, pull the latest memory, browse memories, or search for context from other AI tools.
---

# Memory Management Skill

## When to use

- User asks to "save this to memory" or "write a memory"
- User asks to "pull the latest memory" or "what's the latest from ChatGPT"
- User asks to "browse memories" or "list what I have saved"
- User asks to "search memories for [topic]"
- User wants to share context between AI tools (ChatGPT, Claude, Gemini, Cursor)

## Instructions

### Writing memories

1. Structure the memory with a clear title in "Topic — Summary" format
2. Use structured content: Change, Reason, Impact, Open Questions
3. Tag generously with relevant categories
4. Set `allowed_vendors: ["*"]` unless the user restricts access

Example write:
```
Title: "Auth System — Migrated from magic-link to Clerk OAuth"
Tags: ["architecture", "auth", "decision"]
Content: "Change: Replaced custom magic-link auth with Clerk OAuth...\nReason: ..."
```

### Reading memories

- For "pull latest" → use `get_latest_memory` tool
- For "browse" or "list" → use `browse_memories` tool with filter "all"
- For "memories about X" → use `get_memories_by_tag` with relevant tags
- For "search for X" → use `browse_memories` with filter "search" and the term

### Cross-agent context

Reflect Memory is a shared layer across AI tools. When the user mentions "what does ChatGPT know" or "pull from Claude", they mean: retrieve the latest memories written by those tools. All memories are accessible regardless of which tool wrote them when `allowed_vendors` is `["*"]`.
