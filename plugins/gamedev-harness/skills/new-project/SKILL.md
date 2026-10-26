---
name: new-project
description: Scaffold a new game project's design docs and journal (README with pillars, vision, roadmap, decision log, journal folder, CLAUDE.md).
argument-hint: "[project name] [one-line pitch]"
disable-model-invocation: true
---

# New game project

Set up the docs scaffold in the **current directory** for: $ARGUMENTS

1. Look at what's already here. **Never overwrite an existing file.** Skip it and mention it.
2. If the user gave a pitch or a brain dump, use it to fill the templates. Otherwise ask for a one-line pitch and 2–3 games it's inspired by, then fill in what you can and leave clear `TODO`s.
3. Copy each file from [templates/](templates/) to the same relative path in the project, filling in the placeholders:
   - `README.md`: pitch, pillars, docs map
   - `CLAUDE.md`: instructions for future Claude sessions
   - `docs/vision.md`, `docs/roadmap.md`, `docs/decisions.md`
   - `journal/.gitkeep`
4. Where the pitch makes it relevant, add a doc under `docs/design/` per major system (e.g. combat, economy). Keep each one short: what reference games do, the options, a recommendation, open questions. Research reference games rather than relying on memory.
5. Don't create code, engine projects, or pipelines. This skill only sets up the docs (YAGNI).
6. Reply with a short tree of what was created.
