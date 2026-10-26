---
name: new-project
description: Start a new game project. Sets up design docs (README with pillars, vision, roadmap, decision log), a journal folder, CLAUDE.md, and the engine project folder (Unity by default). Use when the user wants to create, start, or set up a new game / game dev project, even if they describe it in a long spoken ramble.
argument-hint: "[name and/or a spoken brain dump of the idea]"
---

# New game project

Set up a new game project in the **current directory** from: $ARGUMENTS

The input is often dictated and rambling. Distil it; don't transcribe it.

## 1. Gather (ask only for what's missing, in one go)

- **Name** (no spaces is easiest for folders, e.g. `RTSCraft`).
- **Pitch** and **2–3 inspiration games**.
- **Engine**: default **Unity**. Others (Godot, Unreal, none yet) are fine; see step 4.

## 2. Check the folder

Look at what's already here. **Never overwrite an existing file.** Skip it and mention it.

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
