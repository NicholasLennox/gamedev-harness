# gamedev-harness: notes for Claude

- Keep skills, templates and READMEs terse.
- When you change the plugin, add a line under `## [Unreleased]` in `CHANGELOG.md`.
- To release, use the `patch-notes` skill to turn `Unreleased` into a version and bump `version` in `plugins/gamedev-harness/.claude-plugin/plugin.json`. Minor for a new or reworked skill, patch for tweaks. Pushing a new minor version publishes a GitHub release.
