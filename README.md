# ContextGuard by Jag

ContextGuard by Jag is a local-first desktop and CLI app for keeping AI-agent
memory healthy.

It helps people inspect, search, clean, and understand long-lived context used
by tools such as Claude Code, Codex, Cursor, Cline, Aider, and repo-local agent
rule files. The goal is simple: help humans catch stale rules, duplicates,
contradictions, oversized memory, broken links, and unsafe notes before an AI
assistant acts on them.

## What It Helps With

- Scan local markdown memory and rule files.
- Review findings with clear file, line, evidence, and remediation details.
- Search across model, project, path, rule, severity, evidence, and help text.
- View and edit memory files with human approval, diff preview, backups, and a
  Trail of actions.
- Visualize how models, projects, files, findings, and rules relate.
- Let MCP-capable assistants inspect local scan results and guide people through
  cleanup without uploading private memory.

## Public Repo Contents

This public repo is for:

- product README
- MCP setup and safety docs
- public help docs
- release assets and updater metadata when releases are published

This repo does not host the proprietary application source code.

## Docs

- `docs/MCP.md` - local MCP server setup and tool list.
- `docs/PUBLIC_HELP.md` - human-facing help for what ContextGuard can do.

## Free App and Support

ContextGuard is a free app from Jag Journey, LLC, built in a giving spirit to
help people work with AI more safely. If it helps, please star this repo or
support continued development through Jag Journey donations.

## Privacy Stance

Memory often contains project, client, operations, and workflow details.
ContextGuard is local-first by default, transparent about edits, and conservative
about writes. Changes to long-lived memory should stay human-reviewed.
