# UIPrompt

Plan every page of your UI in [UIPrompt](https://uiprompt.app), then let your
coding agent build exactly that: every section in page order, your exact copy
word for word, your brand colors, fonts and logo files, and the stack you
chose. The agent can also lay out new pages on your UIPrompt canvas from a
description or a screenshot, for you to review before any code is written.

![UIPrompt](assets/logo.png)

## What's included

- **The UIPrompt connector.** A remote MCP server at
  `https://uiprompt.app/api/mcp`. Nothing is installed or run on your machine.
- **The UIPrompt skill.** Instructions for your agent: how to build from a
  brief (sections in order, exact copy wins, real logo files, nothing extra)
  and how to plan a page on your canvas.

There are no hooks, scripts, commands or bundled programs.

## Getting started

1. Install the plugin. In Claude Code:

   ```
   /plugin install uiprompt --marketplace Curtisx1/uiprompt-plugins
   ```

   In Codex or Cursor, add `Curtisx1/uiprompt-plugins` as a marketplace and
   install UIPrompt from it.

2. The first time the agent connects, sign in with your UIPrompt account. The
   connector uses OAuth, so there are no API keys to copy. In Claude Code, run
   `/mcp` and choose UIPrompt to sign in.
3. Ask your agent something like:
   - "Build the home page from my UIPrompt project."
   - "Plan a pricing page in UIPrompt from this screenshot."
   - "Use my UIPrompt brand kit for the header and footer."

Calling the connector's tools needs a paid UIPrompt plan. The
[editor demo](https://uiprompt.app/projects/demo) needs no account.

## What the plugin sends and fetches

Everything goes to one place: UIPrompt's own server, `https://uiprompt.app`,
over HTTPS, signed in as you.

- **Reads:** your UIPrompt projects, the brief for a project (stack, design
  tokens, sections and components with their copy), your brand kits, and your
  logo files, which the skill tells the agent to save into your codebase.
- **Writes:** when you ask the agent to plan pages, it creates and edits
  projects, sections, components and connections in your UIPrompt account.
- **Design tokens from a website:** if you ask for them, UIPrompt's server
  reads the public page you name and returns its colors and fonts.

The plugin itself stores nothing and sends nothing anywhere else. Your
agent's own data handling is up to the agent you use. See UIPrompt's
[privacy policy](https://uiprompt.app/privacy-policy) and
[terms of service](https://uiprompt.app/terms-of-service).

## Support

Setup guides: [Claude Code](https://uiprompt.app/integrations/claude-code),
[Codex](https://uiprompt.app/integrations/codex),
[Cursor](https://uiprompt.app/integrations/cursor). Questions and problems:
[uiprompt.app/contact](https://uiprompt.app/contact).

## License

MIT. See [LICENSE](LICENSE).
