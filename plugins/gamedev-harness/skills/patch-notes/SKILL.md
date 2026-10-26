---
name: patch-notes
description: Keep patch notes in CHANGELOG.md, for a game or any other repo (including this plugin). Use when the user says "patch notes", "changelog", "what changed since 0.4", "cut a version", "release", or bumps a version number.
argument-hint: "[version to cut, or empty to update Unreleased]"
---

# Patch notes

Update `CHANGELOG.md` from: $ARGUMENTS (empty means update `Unreleased`).

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). Newest version first. `## [Unreleased]` at the top collects changes until a version is cut. Use only the sections that have entries: **Added**, **Changed**, **Fixed**, **Removed**. In games, balance tweaks go under Changed.

## 1. Find what changed

- Last version: the newest `## [x.y.z]` heading, or the latest git tag. If there's no `CHANGELOG.md`, create it from [templates/CHANGELOG.md](templates/CHANGELOG.md) and start from the first commit.
- Since then: `git log --oneline`, closed issues if on GitHub (`gh issue list --state closed`), and new `docs/design-log.md` entries.

## 2. Write the entries

- One line per change, written for whoever plays or uses it: *what's different*, not how it was done.
- Merge related commits into one line. Skip housekeeping (typos, doc wording) unless someone would notice.
- Link issues where there is one (`#12`).

## 3. Cut a version (only when asked)

- Rename `Unreleased` to `## [x.y.z] - YYYY-MM-DD` and add a fresh empty `## [Unreleased]` above it.
- Pick the number by [SemVer](https://semver.org/): minor for new features, patch for fixes and tweaks.
- Bump it where the project keeps it: `version` in `.claude-plugin/plugin.json` for a Claude plugin, or `bundleVersion` in `ProjectSettings/ProjectSettings.asset` for Unity (Project Settings → Player → Version). If unsure where, say so.

## 4. Reply

One line: which section changed, and how many entries.
