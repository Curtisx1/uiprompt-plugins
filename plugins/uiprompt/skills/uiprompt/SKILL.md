---
name: uiprompt
description: Build UI from a UIPrompt plan, or plan pages in UIPrompt before building them. Use when the user mentions UIPrompt, a UIPrompt project or brief, asks to build a page or section "as planned", or wants a page planned (from a description or a screenshot) before any code is written.
---

# UIPrompt

UIPrompt is where a user plans their app's UI: pages, the sections on each
page in order, the components in each section with their exact copy, their
brand (colors, fonts, logo files) and their stack. You build from that plan
instead of guessing, and you can also lay out new pages in it.

The UIPrompt connector (the `uiprompt` MCP server) gives you the tools below.
If they aren't available, see [Without the connector](#without-the-connector).

## Building from a plan

1. Find the project. If the user didn't name one, call `list_projects` and ask
   which one, unless only one fits.
2. Call `get_agent_context` with the project id. It returns the brief: stack,
   design tokens, rules, and every section in page order with a prompt per
   component.
3. If the brief has a `<logo>` block, call `get_brand_logo` for each variant it
   lists (`main` for the header, `dark` for dark backgrounds, `icon` for the
   favicon and app icons). Save the files and use them as they are. Never
   redraw or approximate a logo.
4. Build it in the user's codebase, following their existing conventions and
   the stack the brief names.

While building:

- **Exact Copy is word for word.** If a component's prompt and its Exact Copy
  disagree, the Exact Copy wins.
- **Build only what's in the brief.** No extra sections, cards, badges, icons
  or filler copy. Respect each component's Forbidden Patterns.
- **Keep page order.** Sections appear in the order the brief gives.
- **Use the design tokens and brand.** The brief's colors and fonts, not
  defaults or close guesses.
- Frames marked as reference are context for you, not UI to render.

When you finish a page, say which sections you built and anything in the brief
you couldn't follow, rather than quietly changing it.

## Planning a page

When the user wants a page planned before it's built, or describes a page or
shares a screenshot to plan from:

1. `create_project`, or use their existing project. Call `set_project_stack`
   if the stack is known.
2. Optionally `get_design_tokens` for a reference site the user names.
3. `create_frame` for each section, in page order, with explicit
   x, y, width and height.
4. `add_component` for each atomic element (a heading, a button, an image),
   never one component for a whole section. Put the exact copy, layout hints
   and forbidden patterns in its `contentSpec`.
5. `group_components` after each logical cluster (a nav, a hero, a card grid,
   a button pair).
6. `add_connection` between sections in page order, then `get_project` to
   review.

Then stop and let the user review the plan in UIPrompt before building it.
Use copy the user gave you or that's in the screenshot; where you'd have to
invent copy, say so and leave it for them to fill in.

## Brand kits

`list_brands` lists the user's brand kits and `set_project_brand` makes a
project use one. A project on a kit gets its colors, fonts, look, logo and
brand rules from the kit.

## Without the connector

If the `uiprompt` tools aren't available:

- **The brief may be in the repo.** Look for `.uiprompt/brief.md` (with the same
  structure in `.uiprompt/skeleton.json`), which UIPrompt adds by pull request,
  and build from it as above. Logo files the brief names are in the repo too.
- **To connect,** the user adds the remote MCP server
  `https://uiprompt.app/api/mcp` to their agent and signs in with their UIPrompt
  account. Setup guides for each agent are at
  https://uiprompt.app/integrations/claude-code and the pages linked from it.
  Connecting needs a paid UIPrompt plan.
- **To start planning,** the editor demo needs no account:
  https://uiprompt.app/projects/demo
