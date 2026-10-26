# gamedev-harness

A personal Claude plugin for game projects. **You don't need slash commands: just talk.**

| Skill | Say something like… | Does |
|---|---|---|
| `journal` | "journal this: …", "log a lesson: …", or paste a video link | Turns an idea, video, or lesson learned into a note in `journal/` |
| `design` | "let's talk about loot…", "maybe no junk items", or "yes" when a journal note offers to iterate | Updates that system's doc in `docs/design/`, logs settled decisions, and appends the reasoning to `docs/design-log.md` (an agent-facing history) |
| `new-project` | "I want to start a new game project…" | Asks you to describe the game, then sets up docs (pillars, vision, roadmap, decisions), `journal/`, `CLAUDE.md`, and an empty `src/` folder |

Claude picks the right skill from what you say. To force one, type `/gamedev-harness:new-project` (or `:journal`) and keep talking after it. Everything after the command is passed in. `new-project` with nothing after it just asks you to tell it about your game.

## How `new-project` goes

1. **You describe the game.** Claude asks once for a working name (a placeholder is fine) and whatever you want to say about it, including the games and mechanics that inspired it. Ramble as much as you like. You can also put the description straight after the command.
2. **The setup.** Claude distils that into the docs and suggests a few pillars. It doesn't ask follow-up questions. Anything you didn't cover becomes a `TODO`.
3. **No engine yet.** The code goes in `src/` later. Create the engine project there yourself, or ask Claude to in a later prompt.

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
| Zip from [Releases](https://github.com/NicholasLennox/gamedev-harness/releases): upload it in claude.ai, or unzip and use `--plugin-dir` | Manual install, no marketplace |

Chat on web and mobile can't write files, so there the journal skill gives you the note to save instead. Use `new-project` in Claude Code, since it creates folders.

## Update

Edit → bump `version` in `plugins/gamedev-harness/.claude-plugin/plugin.json` → push.

A new minor version (0.5, 0.6…) gets a GitHub release with the zip automatically. Patch bumps (0.4.1) don't.

## Maybe later

- Concept art → Blender → engine, possibly as a [plugin dependency](https://code.claude.com/docs/en/plugins/dependencies).
- Notion sync for the journal.
