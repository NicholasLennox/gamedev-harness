---
name: journal
description: Capture a game design idea or a development lesson as a tidy note. Use when the user says "journal this", "note this idea", "log a lesson", shares a design video/short/reel link, or describes something they learned (about game design, Unity, Blender, tooling, AI workflows) that they want to keep. Input is often a dictated ramble.
argument-hint: "[link or rambling thought]"
---

# Journal

Turn the user's input into one note. Input: $ARGUMENTS (or the recent conversation if empty).

## 1. Decide the kind

- **idea**: game design inspiration (a mechanic, a principle, a video from a designer, "what if…").
- **lesson**: something learned while building (a Unity gotcha, a Blender export setting, a prompt that worked, a mistake not to repeat).

## 2. Get the content

| Input | Do |
|---|---|
| Typed/spoken thought | Use it directly. It may ramble, so distil it rather than transcribing it |
| YouTube link | If `yt-dlp` is available: `yt-dlp --write-auto-subs --sub-langs en --skip-download -o "%(title)s" <url>` in a temp/scratch dir, then read the `.vtt`. Otherwise fetch the page for the title/description and ask the user for the key point |
| Instagram / TikTok link | No public captions. If `yt-dlp` and `whisper` / `faster-whisper` are available, download the audio and transcribe it. Otherwise ask the user to describe it in a sentence. Don't fight the platform |
| Article link | Fetch and summarise |

Check claims against sources where cheap (e.g. who a designer is, how a mechanic works in the cited game). Mark anything unverified.

## 3. Write the note

Use [templates/idea.md](templates/idea.md) or [templates/lesson.md](templates/lesson.md).

- **With a filesystem** (Claude Code): save to `journal/YYYY-MM-DD-<slug>.md` in the current project. Create `journal/` if it's missing. If the note clearly affects a design doc (e.g. `docs/design/*.md`), add a one-line link under that doc's open questions.
- **Without one** (claude.ai chat, mobile): reply with the finished note in a markdown block so the user can save it later.

## 4. Reply

One or two lines: what was captured and where it was saved. Don't repeat the whole note back.
