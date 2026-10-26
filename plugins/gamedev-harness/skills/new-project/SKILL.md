---
name: new-project
description: Start a new game project. Asks the user to describe their game, then sets up design docs (README with pillars, vision, roadmap, decision log), a journal folder, CLAUDE.md, and an empty src/ folder for the code. Use when the user wants to create, start, or set up a new game / game dev project, even if they describe it in a long spoken ramble.
argument-hint: "[working name and a brain dump of the idea]"
---

# New game project

Set up a new game project from: $ARGUMENTS

This skill only gets the ideas down. **Don't pick an engine, create engine projects, or write game code.** The user sets those up later.

## 1. Ask once

If `$ARGUMENTS` is empty, do nothing else first: no file listing, no searching, no setup. Reply with just this and wait:

> Tell me about your game. Give it a working name (a placeholder is fine), then describe it as much as you like: what the player does, the games and mechanics that inspired it, anything else on your mind.

If `$ARGUMENTS` already describes the game, skip straight to step 2.

Whatever comes back is usually dictated and rambling. Distil it; don't transcribe it. **Don't ask follow-up questions.** Anything missing becomes a `TODO` in the docs. If there's no name, use a short placeholder and say so.

## 2. Pick the folder

- If the current directory already holds other projects (e.g. a `GameDev/` folder of games), create the project in a new subfolder `<Name>/` (no spaces, e.g. `RTSCraft`).
- If it's empty, or clearly the user's folder for this game, use it directly.
- **Never overwrite an existing file.** Skip it and mention it.

## 3. Write the docs

Copy each file from [templates/](templates/) to the same relative path in the project, filling in the placeholders from what the user said. Suggest 2–3 pillars from what you heard. Leave clear `TODO`s where something is unknown:

- `README.md`, `CLAUDE.md`
- `docs/vision.md`, `docs/roadmap.md`, `docs/decisions.md`, `docs/design-log.md`
- `journal/.gitkeep`
- `src/README.md` (empty placeholder for the code or engine project)

For the one or two systems the user talked about most, add a doc under `docs/design/` (what the reference games do, options, a recommendation, open questions), each under ~250 words. Research the reference games; don't rely on memory. List any other systems as open questions in `decisions.md` instead.

**Keep it short.** Aim for under ~1,000 words across the whole project. Use bullets over prose. If a section needs a paragraph to explain, it's probably a TODO.

## 4. Wrap up

- Reply with a short tree of what was created and a few lines on the TODOs worth filling in next.
- Say the code goes in `src/`, whenever they're ready (create the engine project there, or ask Claude to).
- Offer to `git init` and push to a **private** GitHub repo. Only do it if the user says yes.
