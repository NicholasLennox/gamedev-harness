---
name: design
description: Iterate on a game system's design doc. Use when the user wants to rethink, refine, or talk through a system ("let's talk about loot", "maybe no junk items", "iterate the economy with that journal note"), or accepts a journal note's offer to iterate. Updates the doc in docs/design/, records settled decisions, and appends to an agent-facing design log. Input is often a dictated ramble.
argument-hint: "[system, and what you're thinking]"
---

# Design iteration

Iterate on a system's design from: $ARGUMENTS (or the recent conversation if empty).

## 1. Find the system

- Match the input to a doc in `docs/design/`. If none fits, create `docs/design/<system>.md` from [templates/system.md](templates/system.md).
- Read that doc, the pillars in `README.md`, `docs/decisions.md`, and recent `docs/design-log.md` entries for this system.
- If the input names or obviously relates to a journal note, read that too.

## 2. Distil the change

The user is usually thinking out loud. Sort what they said:

- **Settled** ("no junk items"): goes into the doc as current design.
- **Leaning** ("maybe tiers"): goes into open questions, with the leaning in *italics*.
- **Conflicts with a pillar:** flag it in the reply. Don't silently apply it.

Don't ask follow-up questions. Research reference games only if the change depends on how they work.

## 3. Update the files

- **The design doc:** edit it so it reads as the *current* design, not a history. Drop text the change replaces. Keep it under ~250 words.
- **`docs/decisions.md`:** add a row for anything settled that's worth not re-arguing.
- **The journal note** (if one was used): set `status:` to `adopted` or `considered`.
- **`docs/design-log.md`:** create it from [templates/design-log.md](templates/design-log.md) if missing, then **append** one entry. Never edit old entries.

```
## YYYY-MM-DD · <system> · source: conversation | journal/<file>.md
- Changed: <what the doc says now that it didn't>
- Why: <the user's reasoning, in their terms>
- Dropped: <alternatives rejected or text removed, so they aren't lost>
```

The log is for agents, not people: terse, complete, append-only. It's where the reasoning behind the current doc lives, so be generous with "Why" and "Dropped".

## 4. Reply

Two or three lines: what changed in which doc, any pillar conflict, and the open questions still left for this system.
