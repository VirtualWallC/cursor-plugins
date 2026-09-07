# Claude Code marketplace

This repo is primarily a Cursor plugin marketplace (`.cursor-plugin/marketplace.json`).
`.claude-plugin/marketplace.json` exposes the same repo to Claude Code for the
plugins that also carry a `.claude-plugin/plugin.json`.

Currently exposed: `pstack` (48 skills, 2 agents).

## Install

```bash
claude plugin marketplace add VirtualWallC/cursor-plugins
claude plugin install pstack@cursor-plugins
```

For a local checkout, use the path instead:

```bash
claude plugin marketplace add ./
```

After changing plugin files, refresh the installed copy:

```bash
claude plugin marketplace update cursor-plugins && claude plugin update pstack
```

## Adding another plugin

1. Add `<plugin>/.claude-plugin/plugin.json` (`name`, `description`, `version`;
   point `skills` at any skill dirs outside the auto-discovered `skills/`).
2. Add an entry to `.claude-plugin/marketplace.json` with `source: "./<plugin>"`.
3. Verify with `claude plugin validate .`.

Claude Code auto-discovers `commands/`, `agents/`, `skills/`, `hooks/hooks.json`
and `.mcp.json`. Cursor-only frontmatter keys (`mode`, `icon`, `color`,
`reminder`, `is_background`) are ignored rather than rejected.
