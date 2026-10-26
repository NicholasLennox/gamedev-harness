# {{Project Name}}: notes for Claude

- Read `README.md` and `docs/vision.md` before proposing design or architecture changes.
- Design pillars in `README.md` break ties. Flag ideas that conflict with them.
- Record decisions in `docs/decisions.md` with the *why*.
- When the user shares a design idea or something they learned, use the `journal` skill (notes go in `journal/`).
- When the user wants to rethink a system, use the `design` skill. It updates `docs/design/`, and appends the reasoning to `docs/design-log.md` (read that log before changing a design doc).
- To turn a design into work (GitHub issues or tickets), use the `feature` skill.
- Patch notes live in `CHANGELOG.md`; use the `patch-notes` skill.
## Coding principles

- **KISS:** pick the most straightforward, clearest way to do it. Readable beats clever.
- **YAGNI:** don't build generic tools, pipelines or abstractions until they're actually needed.
- **DRY, loosely:** remove obvious duplication, but don't abstract early. Two similar copies are fine. Extract on the third, and only if it makes the code simpler. When DRY and KISS conflict, KISS wins.

## Working notes
- Verify claims about other games and tools before writing them into docs.
