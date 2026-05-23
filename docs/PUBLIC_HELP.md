# ContextGuard Public Help

ContextGuard by Jag helps people inspect and clean the context that AI assistants
use across projects. It is local-first by default because memory files can
contain private project, client, and operations details.

## What People Can Do

1. Add a folder, project, AppData location, or model memory directory.
2. Scan markdown memory and repo rule files.
3. View the actual memory files found in the scan.
4. Search across model, project, path, rule, finding, evidence, and help text.
5. Review findings such as stale context, oversized indexes, duplicates,
   contradictions, broken links, and possible secrets.
6. Preview edits before changing long-lived memory.
7. Save or delete markdown memory files only after review.
8. Keep a Trail of human actions, backups, and review decisions.
9. Use the graph to see how models, projects, rules, files, and findings relate.
10. Connect an MCP-capable assistant to the local MCP server for guided help.

## Human-in-the-Loop Stance

ContextGuard is not meant to silently rewrite memory. The person decides what is
true. The app helps by finding risk, explaining impact, previewing changes, and
creating backups before disk writes.

## MCP Assistant Help

The local MCP server lets assistants see structured scan results without screen
sharing or pasted file chunks.

```powershell
contextguard mcp --root D:/path/to/project-or-memory-folder
```

Read-only tools are enabled by default. Write tools require:

- starting the server with `--allow-write`
- explicit confirmation strings
- a backup before save or delete

See `docs/MCP.md` for the full MCP tool list and client configuration shape.

## Updates

Public releases provide installer assets, release notes, signed updater
artifacts, and `latest.json` updater metadata when releases are available.

The About screen includes a manual update check. When a signed update is
available, ContextGuard downloads it from the public GitHub release feed,
installs it, and relaunches.

## Free App and Support

ContextGuard is a free app from Jag Journey, LLC, built in a giving spirit to
help people work with AI more safely. If it helps, people are encouraged to star
the public GitHub repo or support continued development through donations. The
public GitHub repo is for public docs, MCP/help information, release assets, and
update delivery. It is not a source-code host.
