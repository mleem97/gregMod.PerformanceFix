# AGENTS.md — Notes for AI agents (gregMod.PerformanceFix)

Repo: gregMod.PerformanceFix · Status: **stub** (README only, no `.csproj`, no `src/` yet).

## Duties

1. **Read first:** `README.md` — only then make changes.
2. **Do not commit secrets** (keys, tokens, `.env`). Use keys only via environment variables.
3. **Preserve history:** no `push --force`, no history rewrite without instruction.
4. **Verify changes:** once a `.csproj` exists, build with `dotnet build gregMod.PerformanceFix.csproj -c Release` or `./build.sh PerformanceFix` from `ModRepositories/`.
5. **Keep docs in sync:** for new features update `README.md` + `CHANGELOG.md` (Unreleased).
6. **Conventions:** Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:` …), one logical change per commit.
7. **When unsure:** stop and ask instead of guessing — especially for deletes, migrations, CI.

## Scaffolding rules (when implementing the stub)

- Follow the sibling-mod layout: `gregMod.PerformanceFix.csproj` (`net6.0`,
  x64), `src/<Name>Mod.cs` (`MelonMod`), `references/` as absolute symlinks
  (run `../tools/sync-melon-assemblies.sh`), `VERSION`, `CHANGELOG.md`.
- **Never** call `QualitySettings.SetQualityLevel` (stomps game tiers —
  same rule as gregMod.Potato); use granular levers only: snapshot original
  → apply → restore, one failing lever never blocks the rest.
- Camera far plane stays untouched (gameplay).
- Never commit `references/*.dll`, `bin/`, or `obj/`.
- Every lever behind a MelonPreferences toggle, default off/safe.
