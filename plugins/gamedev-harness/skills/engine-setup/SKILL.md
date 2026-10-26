---
name: engine-setup
description: Set up the engine project for a game, and the tooling Claude needs to drive the engine. Use when the user picks or mentions an engine ("I'm going to use Unity", "let's make this in Unity", "set up the Unity project"), or asks to create the project in src/.
argument-hint: "[engine, e.g. Unity]"
---

# Engine setup

Set up the engine from: $ARGUMENTS (or the recent conversation if empty).

## 1. Say what you'll do

Before running anything, tell the user in two or three lines: which engine, which tools you'll check or install, and where the project will go. Then go ahead. Don't wait for a reply unless something below needs their consent.

## 2. Record the choice

Add or fill the engine row in `docs/decisions.md` (e.g. `D-001 | Unity + C# | <why>`), and update `src/README.md`.

## 3. Unity

1. **Unity CLI:** find `unity` (`unity --version`). Unity Hub installs it to `%LOCALAPPDATA%\Unity\bin` on Windows, which may not be on PATH in an already-open shell. Missing: point the user to Unity Hub, or the install script in `unity skill show`.
2. **Unity's Claude Code plugin:** check `claude plugin list` for `unity@unity-agent-plugin`. If it's missing:
   ```
   claude plugin marketplace add Unity-Technologies/unity-agent-plugin
   claude plugin install unity@unity-agent-plugin
   ```
   If `claude` isn't on PATH (the VS Code extension), its binary is in the extension folder under `resources/native-binary/`. Inside VS Code, the user can also use `/plugins` → Marketplaces.
3. **Editor:** pick the installed Unity 6 version (`unity editors -i`), preferring an LTS. If none, ask the user to install the latest Unity 6 LTS from Unity Hub. Installing accepts Unity's EULA, so that's their call.
4. **Create the project** in `src/<Name>/` (URP, with the Pipeline package so Claude can drive the Editor):
   ```
   unity projects create <Name> --path src --editor-version <ver> --template com.unity.template.urp-blank --with-pipeline --no-cloud --open
   ```
5. **Git:** add Unity ignores for `src/<Name>/` (`Library/`, `Temp/`, `Obj/`, `Build/`, `Builds/`, `Logs/`, `UserSettings/`, generated `*.csproj`/`*.sln`/`*.slnx`, `.vs/`, `.vscode/`).
6. **Check the connection:** `unity status --until-ready --project-path src/<Name>` should show the Editor as `ready`. From here on, drive the Editor with `unity command` rather than hand-editing scene or prefab files (see `unity skill show`).

7. **VS Code as the code editor** (if the user codes in VS Code):
   - Set it as Unity's script editor: `unity command eval --code 'Unity.CodeEditor.CodeEditor.SetExternalScriptEditor(@"<path to Code.exe>"); Unity.CodeEditor.CodeEditor.CurrentEditor.SyncAll(); return 0;'`. This needs the *Visual Studio Editor* package (`com.unity.ide.visualstudio`) 2.0.20 or later; not the legacy *Visual Studio Code Editor* package.
   - Install Microsoft's Unity extension: `code --install-extension visualstudiotoolsforunity.vstuc`. It brings C# and C# Dev Kit with it.
   - C# Dev Kit needs a .NET SDK, not just a runtime (`dotnet --list-sdks`). If none is installed, ask the user to accept Dev Kit's install prompt, or install the current LTS SDK.
   - If the open VS Code folder is above the Unity project, set `"dotnet.defaultSolution": "<path>/<Name>.slnx"` in that folder's `.vscode/settings.json`.

**Driving the Editor, what works:**
- Copy `.cs`, `.asmdef` and `.inputactions` files into `Assets/`, then `unity command eval --code 'UnityEditor.AssetDatabase.Refresh(); return 0;'` and `unity command recompile`.
- Build scenes, prefabs and materials with a C# script run by `unity command eval_file --file <path>`. Use fully qualified type names, and keep the script outside the project.
- Check errors with `unity command console.get --level warning`. Grouped command names take a dot (`console.get`, not `get`).
- Smoke-test with `unity command start` and `stop`, `simulate_key --key W --action down|up`, `simulate_pointer --action move|down|up|click`, and `screenshot --view game`. First run `unity command editor set_auto_tick` and `set_run_in_background --enable true`, or an unfocused Editor barely advances. Simulated keys only reach the game while the Game view has focus, so treat a smoke test as a check for errors and visuals, and hand the real playtest to the user. Restore `set_run_in_background --enable false` afterwards.

**Known failures:**
- Creation fails with `Failed to decompress … template` and a missing `Editor/Data/Tools/7z.exe`: the Editor install is incomplete. Ask the user to reinstall it, or to install a Unity 6 LTS instead.

## 4. Other engines

Not covered yet. Record the decision, create the project in `src/` with the engine's own CLI if it has one, and say what was left manual.

## 5. Reply

What's installed, where the project is, and that it's ready for a first feature (the `feature` skill).
