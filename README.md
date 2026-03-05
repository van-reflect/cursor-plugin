# Reflect Memory — Cursor Plugin

Cross-agent memory for AI tools. Read, write, browse, and search your shared memory layer directly from Cursor.

Reflect Memory gives your AI tools a shared long-term memory. Anything saved from ChatGPT, Claude, Gemini, or Cursor is accessible everywhere. This plugin connects Cursor to that memory via MCP.

## Setup

### 1. Get your API key

Sign up at [reflectmemory.com](https://www.reflectmemory.com) and generate an API key from the dashboard.

### 2. Install the plugin

Install from the [Cursor Marketplace](https://cursor.com/marketplace) or add the MCP server manually:

**Via Cursor Settings:**

1. Open Cursor Settings (Cmd/Ctrl + ,)
2. Go to **Features** → **Model Context Protocol**
3. Click **Add new MCP server**
4. Name: `reflect-memory`, Type: `stdio`
5. Command: `npx`, Args: `["-y", "reflect-memory-mcp"]`
6. Set env `REFLECT_MEMORY_API_KEY` to your key

**Via project config (`.cursor/mcp.json`):**

```json
{
  "mcpServers": {
    "reflect-memory": {
      "command": "npx",
      "args": ["-y", "reflect-memory-mcp"],
      "env": {
        "REFLECT_MEMORY_API_KEY": "your-key-here"
      }
    }
  }
}
```

### 3. Restart Cursor

Restart Cursor for the MCP server to load.

## Tools

| Tool | Description |
|------|-------------|
| `get_latest_memory` | Get the most recent memory. Supports optional tag filter. |
| `get_memory_by_id` | Retrieve a single memory by UUID. |
| `browse_memories` | List memory summaries with filtering and search. |
| `get_memories_by_tag` | Get full memory content by tag(s). |
| `write_memory` | Save a new memory with title, content, tags. |

## Usage

Ask Cursor naturally:

- "Pull the latest memory"
- "What's the latest from ChatGPT?"
- "Browse all my memories"
- "Search memories for authentication"
- "Save this to memory"
- "Write a memory about the new billing system"

## How it works

Reflect Memory is a shared context layer. When you write a memory from Cursor, ChatGPT can read it — and vice versa. Memories are tagged, searchable, and versioned.

## Requirements

- Node.js 18+
- A Reflect Memory API key

## License

MIT
