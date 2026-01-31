# Sandboxed.sh Library

Configuration library for AI coding assistants. Contains skills, commands, and
MCP server configs that sync to Claude Code, Codex, and other tools.

## Structure

```
├── skill/              # Reusable skills (SKILL.md + references/)
├── command/            # Slash commands (markdown files)
├── mcp/                # MCP server configurations (servers.json)
├── init-script/        # Initialization scripts for workspaces
├── workspace-template/ # Workspace templates
└── script/             # Sync scripts
```

## Quick Start

Sync library contents to your local AI tool configs:

```bash
# Sync everything
python3 script/sync.py

# Dry run (preview changes)
python3 script/sync.py --dry-run

# Sync only specific content
python3 script/sync.py --skills-only
python3 script/sync.py --commands-only
python3 script/sync.py --mcp-only

# Prune orphaned items
python3 script/sync.py --prune
```

## Creating Skills

Skills are directories in `skill/` containing a `SKILL.md`:

```markdown
---
name: my-skill
description: Trigger this skill when user asks about X
---

Instructions for the AI agent...
```

Add reference files in `skill/my-skill/references/` for additional context.

## Creating Commands

Commands are markdown files in `command/`:

```markdown
---
description: What this command does
---

Prompt template for the command...
```

## MCP Configuration

Add servers to `mcp/servers.json`:

```json
{
  "my-server": {
    "command": "npx",
    "args": ["-y", "my-mcp-server"]
  }
}
```

## Sync Targets

The sync script writes to:

| Content  | Claude Code           | Codex/Opencode         |
| -------- | --------------------- | ---------------------- |
| Skills   | `~/.claude/skills/`   | `~/.codex/skills/`     |
| Commands | `~/.claude/commands/` | `~/.codex/prompts/`    |
| MCP      | `~/.claude.json`      | `~/.codex/config.toml` |
