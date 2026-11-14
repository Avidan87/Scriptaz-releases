# Scriptaz — downloads & update feed

> # ⚠️ Pre-release — not for general use
> The builds published here are **work-in-progress betas** and **may contain
> serious bugs**. They exist for **testing only** and are **not a finished
> product**. Please do **not** rely on anything here for everyday use.
>
> **Download Scriptaz only when there is an official, stable release.** Until
> then, anything in this repository is experimental and used entirely at your own
> risk.

This repository is the **public** download channel for Scriptaz (the application's
source code is kept private). It hosts three things:

- **Installers** — `Scriptaz.dmg` (macOS) and `Scriptaz-Setup.exe` (Windows), as
  release assets under each version tag.
- **Data pack** — `scriptaz-data-v2.sqlite.gz`, the Scripture library the app
  downloads on first run, as a release asset on the `data-v2` tag.
- **`latest.json`** — the auto-update feed the app polls, served from this repo's
  `main` branch.

## Versioning
The version count **restarts on this channel.** Versions below `1.0.0` (the `0.x`
series) are **betas and may be unstable**. `1.0.0` will mark the **first official,
stable release** — the point at which Scriptaz is meant for everyday use.

## Publishing a new version
1. Build the installers and bump `__version__` in the app (e.g. `0.1.0 → 0.2.0`).
2. Create a release here tagged `v0.2.0` and upload `Scriptaz.dmg` + `Scriptaz-Setup.exe`.
3. Compute each file's SHA-256: `shasum -a 256 Scriptaz.dmg`
4. Edit `latest.json`: set `version`, `notes`, the two asset `url`s, and the two `sha256`s.
5. `git commit && git push`. Running apps pick it up within ~12h (or on next launch).

The app prompts only when `version` here is newer than what's installed.
`min_supported` forces an update for versions below it.
