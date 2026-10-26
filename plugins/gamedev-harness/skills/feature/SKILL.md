---
name: feature
description: Turn a design into buildable work, a feature with a task checklist, filed as a GitHub issue or ready to paste into Jira or another tracker. Use when the user says "make this a feature", "break this down", "create an issue/ticket for X", "what do we build first for loot", or wants to go from a design doc to actionable work.
argument-hint: "[system or feature, e.g. 'loot drops']"
---

# Feature

Turn a design into work from: $ARGUMENTS (or the recent conversation if empty).

A **system** (`docs/design/`) is what the game does, e.g. loot. A **feature** is a buildable, playable slice of one, e.g. "enemies drop items with rarity". One system yields several features.

## 1. Gather

Read the system's design doc, `docs/roadmap.md` (which milestone it belongs to), `docs/decisions.md`, and the pillars in `README.md`.

## 2. Define it

Fill in [templates/issue.md](templates/issue.md):

- **Title:** what the player can do, e.g. "Enemies drop items with rarity".
- **Done when:** one playable outcome, in the roadmap's style.
- **Tasks:** 2–6, each doable in one sitting and leaving the game runnable.
- **Out of scope:** what's deferred to a later feature.

Build from the doc's *current design*; don't invent design here. If an open design question blocks the feature, list it and suggest the `design` skill.

## 3. File it

- **GitHub** (`gh repo view` works): show the title(s) in a short list and create them on a yes. One issue per feature, with tasks as a checklist (GitHub shows checklist progress). Labels: `feature` plus the milestone (e.g. `M2`); create missing ones with `gh label create <name> --force`.
- **Otherwise**, or if the user names Jira or another tracker: reply with the filled template in a markdown block, ready to paste.

## 4. Reply

The issue link(s), or the pasteable block. Nothing else.
