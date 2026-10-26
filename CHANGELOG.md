# Changelog

Notable changes, newest first. Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- MIT licence.

### Changed
- `engine-setup`: notes on smoke-testing Play mode from the CLI (auto-tick, Game view input focus), and on handing playtesting to the user.
- `engine-setup`: sets up VS Code as the Unity code editor (Unity extension, .NET SDK, default solution).

## [0.6.0] - 2026-10-26

### Added
- `engine-setup` skill: records the engine choice, installs Unity's Claude Code plugin if missing, and creates the Unity project in `src/`.

### Changed
- README rewritten for anyone using the plugin: the workflow, what you get, how to install.
- `engine-setup` prefers a Unity 6 LTS and documents how to drive the Editor from the CLI.

### Fixed
- Issues filed by `feature` use full GitHub links, since relative links break in issue bodies.

## [0.5.0] - 2026-10-26

### Added
- `feature` skill: turns a design into a feature with a task checklist, filed as a GitHub issue or ready to paste into Jira.
- `patch-notes` skill: keeps `CHANGELOG.md` in Keep a Changelog format and cuts versions.
- New projects get a `CHANGELOG.md`.

### Changed
- GitHub releases use this changelog for their notes.

## [0.4.0] - 2026-10-26

### Added
- `design` skill: iterates a system's design doc and appends the reasoning to an agent-facing `docs/design-log.md`.
- A GitHub release with the plugin zip for each new minor version.

### Changed
- `new-project` writes one or two design docs of ~250 words, ~1,000 words in total.
- `journal` offers a design iteration instead of editing design docs.

## [0.3.0] - 2026-10-26

### Changed
- `new-project` asks once, then writes docs and an empty `src/`. No engine setup.

## [0.2.3] - 2026-10-26

### Changed
- `new-project` interviews the user before scaffolding.

## [0.2.2] - 2026-10-26

### Changed
- Author metadata; marketplace renamed to `nicholaslennox`.

## [0.2.1] - 2026-10-26

### Added
- KISS / YAGNI / loose-DRY coding principles in the `CLAUDE.md` template.

## [0.2.0] - 2026-10-26

### Added
- Skills trigger from natural language, no slash command needed.
- Unity project folder setup in `new-project`.
- Plugin how-to in the README.

## [0.1.0] - 2026-10-26

### Added
- `journal` and `new-project` skills.
