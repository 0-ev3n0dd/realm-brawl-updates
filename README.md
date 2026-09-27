# Realm Brawl updates

Update builds for **Realm Brawl** (the Windows one-click bundle). This repository holds no game source,
only [releases](https://github.com/0-ev3n0dd/realm-brawl-updates/releases).

Each release has three assets:

| asset | what |
|---|---|
| `manifest.json` | `version`, `build`, `sha256` + `size` of `app.zip`, `minLauncher`, `launcherVersion`, `launcherSha256`, `notes`, `publishedAt` |
| `app.zip` | the contents of the bundle's `app\` folder (game code + `version.json`; no Node.js runtime, no tunnel) |
| `start.ps1` | the matching launcher (installed launchers replace themselves when `launcherVersion` is newer) |

The launcher (`launcher\start.ps1`) reads the stable URLs
`https://github.com/0-ev3n0dd/realm-brawl-updates/releases/latest/download/manifest.json` and `.../app.zip`
on every start, verifies the sha256, and swaps `app` -> `app.prev`, `app.new` -> `app`.
`launcher\rollback.bat` switches back to the previous version.

Releases are made by `publish.sh` from the build machine.
