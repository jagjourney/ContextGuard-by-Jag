# ContextGuard MCP Server

ContextGuard includes a local stdio MCP server so MCP-capable LLM clients can inspect the same memory
folders the human is reviewing. The goal is not remote automation. The goal is a careful assistant
view into local memory health, with the human staying in control.

## Start the server

From a built checkout:

```powershell
cargo run -p contextguard -- mcp --root D:/laragon/www/jag-llm-memory-janitor
```

After installing the CLI binary:

```powershell
contextguard mcp --root D:/laragon/www/jag-llm-memory-janitor
```

Read tools are enabled by default. Save/delete tools are blocked unless the human deliberately starts
the server with write access:

```powershell
contextguard mcp --root D:/laragon/www/jag-llm-memory-janitor --allow-write
```

## Client configuration shape

Use the command above as a stdio MCP server in any MCP-capable client. The common shape is:

```json
{
  "mcpServers": {
    "contextguard": {
      "command": "contextguard",
      "args": ["mcp", "--root", "D:/laragon/www/jag-llm-memory-janitor"]
    }
  }
}
```

For development before the binary is on PATH:

```json
{
  "mcpServers": {
    "contextguard-dev": {
      "command": "cargo",
      "args": ["run", "-p", "contextguard", "--", "mcp", "--root", "D:/laragon/www/jag-llm-memory-janitor"]
    }
  }
}
```

## Tools

| Tool | Write? | Purpose |
|---|---:|---|
| `contextguard_help` | No | Explains workflow, safety model, and tool usage. |
| `contextguard_discover_locations` | No | Finds common Claude, Codex, Cursor, AppData, and profile memory paths. |
| `contextguard_scan` | No | Runs the ContextGuard detector pipeline over markdown files. |
| `contextguard_list_memory_files` | No | Lists editable markdown files under a memory or project folder. |
| `contextguard_read_memory_file` | No | Reads a markdown memory file. |
| `contextguard_explain_memory_file` | No | Summarizes headings, risk signals, and human review actions. |
| `contextguard_preview_memory_edit` | No | Shows changed lines for a proposed full-file replacement. |
| `contextguard_save_memory_file` | Yes | Saves a markdown file only when `--allow-write` and `confirm=SAVE_WITH_BACKUP` are both present. |
| `contextguard_delete_memory_file` | Yes | Deletes a markdown file only when `--allow-write` and `confirm=DELETE_WITH_BACKUP` are both present. |

## Human-in-the-loop workflow

1. Ask the LLM to call `contextguard_discover_locations`.
2. Pick the folder together with the human.
3. Ask the LLM to call `contextguard_scan`.
4. Ask it to list and read the relevant memory file.
5. Ask it to explain the memory in plain language.
6. Ask it to preview an edit with `contextguard_preview_memory_edit`.
7. Review the changed lines in the client and/or ContextGuard app.
8. Only after approval, restart with `--allow-write` if needed.
9. Save with `confirm=SAVE_WITH_BACKUP` or delete with `confirm=DELETE_WITH_BACKUP`.
10. Record the backup path in Trail or the project notes.

## Safety stance

- The server uses stdio and local files. It does not upload memory.
- Write/delete operations are opt-in at server launch.
- Existing markdown files are backed up under the local ContextGuard data folder before save/delete.
- The server only edits files ending in `.md`.
- Assistants should show the target path and diff before asking the human to approve a write.

## Why this matters

The desktop app helps the human see and edit memory. MCP lets an AI helper see the same local facts
instead of relying on screenshots, stale assumptions, or pasted snippets. That makes the assistant
better at explaining what is wrong, proposing safer wording, and walking a non-coder through the
cleanup without taking control away from the human.
