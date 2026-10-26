# gamedev-harness

A personal Claude plugin for game projects. **You don't need slash commands: just talk.**

| Skill | Say something like… | Does |
|---|---|---|
| `journal` | "journal this: …", "log a lesson: …", or paste a video link | Turns an idea, video, or lesson learned into a note in `journal/` |
| `new-project` | "I want to start a new game project…" | Interviews you about the game, then sets up docs (pillars, vision, roadmap, decisions), `journal/`, `CLAUDE.md`, and a Unity project folder |

Claude picks the right skill from what you say. To force one, type `/gamedev-harness:new-project` (or `:journal`) and keep talking after it. Everything after the command is passed in.

## How plugins work (short version)

- A **plugin** is a folder with `.claude-plugin/plugin.json` plus `skills/<name>/SKILL.md` files. A skill is just instructions and templates for Claude.
- A **marketplace** is a catalog: a repo with `.claude-plugin/marketplace.json` that lists plugins and where they live. Claude doesn't discover plugins on its own. You add the catalog once, then install plugins from it.
- This repo is both: the catalog at the root, and the one plugin under `plugins/gamedev-harness/`.

## Install

| Where you add it | Available in |
|---|---|
| **claude.ai → Customize → Plugins → Add → Add marketplace → `NicholasLennox/gamedev-harness`** (recommended) | Your **account**: web, desktop and mobile chat, plus Claude Code when signed in |
| `claude plugin marketplace add NicholasLennox/gamedev-harness` then `claude plugin install gamedev-harness@nicholaslennox` | Claude Code on **that one machine** only |
| `claude --plugin-dir ./plugins/gamedev-harness` | One Claude Code session (for editing the plugin) |

Chat on web and mobile can't write files, so there the journal skill gives you the note to save instead.

## Update

Edit → bump `version` in `plugins/gamedev-harness/.claude-plugin/plugin.json` → push. In claude.ai, use **Check for updates**, or turn on **Sync automatically**, on the marketplace.

## Out of scope (on purpose)

- Concept art → Blender models. That needs a separate Blender MCP server, so it lives per project. Revisit once it's proven in RTSCraft.
- Notion sync for the journal.
