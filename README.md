# gamedev-harness

A personal Claude plugin for game projects.

| Skill | Run it | Does |
|---|---|---|
| `journal` | `/gamedev-harness:journal <link or thought>`, or just say "journal this…" | Turns an idea, video link, or lesson learned into a note in `journal/` |
| `new-project` | `/gamedev-harness:new-project <name> <pitch>` | Scaffolds README, pillars, vision, roadmap, decision log, `journal/`, `CLAUDE.md` |

## How it works (short version)

This folder is a **marketplace** (`.claude-plugin/marketplace.json`) holding one **plugin** (`plugins/gamedev-harness/`). Each skill is a `SKILL.md` with its templates next to it.

## Use it

- **Try locally:** `claude --plugin-dir ./plugins/gamedev-harness`
- **Every device:** push this folder to GitHub, then on claude.ai go to **Customize → Plugins → Add → Add marketplace** and enter `<you>/gamedev-harness`. It syncs to web/desktop/mobile chat and to Claude Code on the same account.
- **Claude Code only (alternative):** `claude plugin marketplace add <you>/gamedev-harness`, then `claude plugin install gamedev-harness@nick-gamedev`

## Test on a fresh project

1. Make an empty folder and open Claude Code in it.
2. `/gamedev-harness:new-project TestGame "a tiny tower defense"`
3. `/gamedev-harness:journal https://youtube.com/...`

## Later (only when needed)

- `blender` skill / bundled Blender MCP config (`.mcp.json`) once the art pipeline is proven in RTSCraft.
- Notion MCP for the journal, if notes need to live outside the repo.
- Change the plugin or add a skill → bump `version` in `plugin.json` → push.
