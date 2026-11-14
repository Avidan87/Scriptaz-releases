# Scriptaz — public downloads & update feed

This repository is the **public** download channel for [Scriptaz](https://github.com/Avidan87/Scriptaz)
(the app's source code is private). It hosts three things:

- **Installers** — `Scriptaz.dmg` (macOS) and `Scriptaz-Setup.exe` (Windows), as release assets per version tag (`v1.1.0`, …).
- **Data pack** — `scriptaz-data-v2.sqlite.gz`, the Scripture library the app downloads on first run, as a release asset on the `data-v2` tag.
- **`latest.json`** — the auto-update feed the app polls. Served raw from this repo's `main` branch.

## Publishing a new version
1. Build the installers and bump `__version__` in the app to e.g. `1.1.0`.
2. Create a release here tagged `v1.1.0` and upload `Scriptaz.dmg` + `Scriptaz-Setup.exe`.
3. Compute each file's SHA-256:  `shasum -a 256 Scriptaz.dmg`
4. Edit `latest.json`: set `version`, `notes` (what the user reads), the two `url`s (the `v1.1.0` assets), and the two `sha256`s.
5. `git commit && git push`. Running apps pick it up within ~12h (or on next launch).

The app only prompts when `version` here is newer than the installed version.
`min_supported` forces an update for versions below it.
