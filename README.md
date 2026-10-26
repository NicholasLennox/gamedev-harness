# gamedev-harness

A Claude plugin for prototyping games, from a weekend game jam to a long-running side project.

Talk through your idea (rambling is fine) and Claude sets up a light framework around it: a pitch and design pillars, a roadmap where every milestone is playable, a design journal, feature tickets, patch notes, and an engine project it can build in. **No slash commands needed: just talk.**

I built it for my own projects. It's free for anyone to use, fork or learn from.

## The workflow

| Step | Say something like… | Skill | What happens |
|---|---|---|---|
| 1. Pitch it | "I want to make a game where…" | `new-project` | Turns your description into short docs: pitch, pillars, influences, core loop, roadmap, decisions |
| 2. Pick an engine | "I'm going to use Unity" | `engine-setup` | Creates the engine project in `src/`, and installs Unity's Claude Code plugin so Claude can drive the Editor |
| 3. Build a feature | "make the greybox hero a feature" | `feature` | Breaks a design into a feature with a task checklist, filed as a GitHub issue (or ready to paste into Jira) |
| 4. Capture ideas | "journal this: …", or paste a video link | `journal` | Saves an idea or lesson as a tidy note in `journal/` |
| 5. Rethink a system | "let's talk about loot, no junk items" | `design` | Updates that system's design doc and logs why it changed |
| 6. Ship it | "patch notes", "cut 0.2" | `patch-notes` | Keeps `CHANGELOG.md` up to date and bumps the version |

Claude picks the skill from what you say. To force one, type `/gamedev-harness:<skill>` followed by whatever you want to say.

## What you get

```
MyGame/
├── README.md        pitch and design pillars
├── CLAUDE.md        how Claude should work in this project
├── CHANGELOG.md     patch notes
├── docs/
│   ├── vision.md    influences, core loop, scope
│   ├── roadmap.md   milestones, each one playable
│   ├── decisions.md decision log and open questions
│   ├── design-log.md  history of design changes (for Claude)
│   └── design/      one short doc per game system
├── journal/         ideas and lessons
└── src/             the engine project
```

The docs stay short on purpose (about 1,000 words to start), so you spend your time making the game rather than writing about it.

## Install

| How | Works in |
|---|---|
| **claude.ai → Customize → Plugins → Add marketplace → `NicholasLennox/gamedev-harness`** (recommended) | Your whole account: web, desktop and mobile, plus Claude Code when signed in |
| `claude plugin marketplace add NicholasLennox/gamedev-harness`, then `claude plugin install gamedev-harness@nicholaslennox` | Claude Code on one machine |
| Download the zip from [Releases](https://github.com/NicholasLennox/gamedev-harness/releases) | Manual: upload it in claude.ai, or unzip and run `claude --plugin-dir <folder>` |

Use Claude Code for `new-project`, `engine-setup` and `feature`, since they create files and run tools. On web and mobile, `journal` hands you the note to save yourself.

## Developing the plugin

- A plugin is a folder with `.claude-plugin/plugin.json` and `skills/<name>/SKILL.md` files: plain instructions and templates for Claude. This repo is also the marketplace that lists it.
- Try changes locally with `claude --plugin-dir ./plugins/gamedev-harness`.
- To release: note the change in [CHANGELOG.md](CHANGELOG.md), bump `version` in `plugins/gamedev-harness/.claude-plugin/plugin.json`, and push. Each new minor version (0.6, 0.7…) publishes a GitHub release with the zip automatically.

## Maybe later

- Concept art → Blender → engine, possibly as a [plugin dependency](https://code.claude.com/docs/en/plugins/dependencies).
- Engines beyond Unity in `engine-setup`.
- Notion sync for the journal.
