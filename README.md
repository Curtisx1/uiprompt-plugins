# UIPrompt plugins for coding agents

Plan every page of your UI in [UIPrompt](https://uiprompt.app), then let your
coding agent build exactly that. This plugin gives your agent:

- **The UIPrompt connector:** your projects, briefs and brand files, over MCP.
  You sign in with your UIPrompt account the first time it connects.
- **A UIPrompt skill:** how to build from a brief (sections in order, exact copy
  word for word, your real logo files) and how to plan new pages on your canvas.

Connecting needs a paid UIPrompt plan. The [editor demo](https://uiprompt.app/projects/demo)
needs no account.

## Claude Code

```bash
claude plugin marketplace add Curtisx1/uiprompt-plugins
claude plugin install uiprompt@uiprompt
```

Then run `/mcp` in Claude Code and sign in to UIPrompt.

## Codex

```bash
codex plugin marketplace add Curtisx1/uiprompt-plugins
```

Then install UIPrompt from the Plugins Directory and sign in.

## Cursor

Add this repository as a marketplace in Cursor's plugin settings, then install
UIPrompt from the marketplace panel and sign in.

## Any agent with skills

The skill works on its own in any agent that supports Agent Skills:

```bash
npx skills add Curtisx1/uiprompt-plugins
```

Add the connector separately: the MCP server URL is `https://uiprompt.app/api/mcp`.
Setup for each agent: [Claude Code](https://uiprompt.app/integrations/claude-code),
[Codex](https://uiprompt.app/integrations/codex),
[Cursor](https://uiprompt.app/integrations/cursor),
[GitHub Copilot](https://uiprompt.app/integrations/github-copilot),
[Windsurf](https://uiprompt.app/integrations/windsurf),
[Gemini CLI](https://uiprompt.app/integrations/gemini-cli).

## What's in this repository

| Path                                                             | For                                       |
| ---------------------------------------------------------------- | ----------------------------------------- |
| `plugins/uiprompt/skills/uiprompt/SKILL.md`                      | The skill, shared by every agent          |
| `plugins/uiprompt/.claude-plugin/plugin.json`, `.mcp.json`       | Claude Code                               |
| `plugins/uiprompt/plugin.json`, `mcp.json`                       | Codex (the portable Agent Plugins format) |
| `plugins/uiprompt/.cursor-plugin/plugin.json`, `cursor.mcp.json` | Cursor                                    |
| `.claude-plugin/`, `.agents/plugins/`, `.cursor-plugin/`         | Each agent's marketplace listing          |

## License

MIT
