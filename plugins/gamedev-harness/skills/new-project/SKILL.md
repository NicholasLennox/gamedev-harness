---
name: new-project
description: Start a new game project by interviewing the user about their game, then setting up design docs (README with pillars, vision, roadmap, decision log), a journal folder, CLAUDE.md, and the engine project folder (Unity by default). Use when the user wants to create, start, or set up a new game / game dev project, even if they describe it in a long spoken ramble.
argument-hint: "[name and/or a spoken brain dump of the idea]"
---

# New game project

Set up a new game project from: $ARGUMENTS

## 1. Interview first, build later

**Don't create any files until the interview is done.** Start by talking to the user about their game, like a curious design partner would. Their answers are usually dictated and rambling, so let them ramble. You'll distil it later.

- If `$ARGUMENTS` is empty, open warmly and ask them to tell you about the game, any way they like.
- If it already holds a brain dump, play back the gist in a line or two, then pick up the most interesting gap.
- Ask **one or two open questions per turn** in plain text. Build on what they just said instead of working down a checklist. Don't use multiple-choice menus for creative questions.
- Feel free to suggest things ("sounds like Hades meets Stardew. Is the farming the main thing or the break between runs?"), but the ideas stay theirs.

Over the conversation, cover:

- **The fantasy:** what the player does and feels. What makes it *theirs*?
- **Inspirations:** 2–3 games, and what to **take** and **leave** from each.
- **Core loop:** what the player does minute to minute, and what brings them back.
- **Scope:** solo or team, platform, single- or multiplayer, the smallest version worth playing.
- **Why this project:** what they want to learn or prove. This shapes the roadmap.
- **Pillars:** two or three tie-breakers for when ideas conflict. Suggest them from what you've heard and let the user adjust.
- **Name** (no spaces is easiest, e.g. `RTSCraft`) and **engine** (default **Unity**; Godot, Unreal or "none yet" are fine, see step 4). Ask these last, briefly. A working name is fine.

Wrap up once you have enough to fill the templates, usually 3–6 exchanges. If the user says "just set it up", stop and leave `TODO`s for the gaps. To wrap up, give a short summary (pitch, inspirations with take/leave, core loop, pillars, scope, name, engine) and the folder you'll create it in, then ask "anything to change before I set it up?" Build only after they confirm.

## 2. Check the folder

Look at what's already here.

- If the current directory already holds other projects (e.g. a `GameDev/` folder full of games), create the project in a new subfolder `<Name>/` and say so in the summary.
- **Never overwrite an existing file.** Skip it and mention it.

## 3. Docs

Copy each file from [templates/](templates/) to the same relative path in the project, filling in the placeholders from what the user said. Leave clear `TODO`s where something is unknown:

- `README.md`, `CLAUDE.md`
- `docs/vision.md`, `docs/roadmap.md`, `docs/decisions.md`
- `journal/.gitkeep`

Where the pitch makes it relevant, add a short doc under `docs/design/` per major system (what reference games do, options, a recommendation, open questions). Research the reference games; don't rely on memory.

## 4. Engine folder

Layout: docs at the repo root, the engine project in its own subfolder `<Name>-<Engine>/` (e.g. `RTSCraft-Unity/`). Keeps the docs out of the engine's import path.

**Unity:**
1. Copy [templates/unity.gitignore](templates/unity.gitignore) to `.gitignore` at the repo root, replacing `{{UnityFolder}}` with the folder name. Merge if a `.gitignore` exists.
2. Look for an installed editor: `C:\Program Files\Unity\Hub\Editor\<version>\Editor\Unity.exe` on Windows, `/Applications/Unity/Hub/Editor/<version>/Unity.app/Contents/MacOS/Unity` on macOS.
   - **Found:** ask which version if there are several (prefer the newest LTS), then run `"<Unity.exe>" -batchmode -quit -createProject "<repo>/<Name>-Unity"`. This takes a minute or two. Then tell the user to open it via Unity Hub → **Add → Add project from disk**.
   - **Not found:** don't create the folder (Unity Hub wants to create it itself). Tell the user: in Unity Hub, **New project** → pick a template (e.g. Universal 3D) → **Project name** `<Name>-Unity` → **Location** this repo's folder.

**Other engines:** write `.gitignore` entries for that engine, and tell the user how to create the project into `<Name>-<Engine>/`. Don't generate engine files by hand.

Don't write game code or pipelines. This skill only sets up the project (YAGNI).

## 5. Wrap up

- Reply with a short tree of what was created and the one next step (usually "create/open the Unity project").
- Offer to `git init` and push to a **private** GitHub repo. Only do it if the user says yes.
