# ttp (TizenTube, pinned)

A pinned, patched build of the [TizenTube](https://github.com/reisxd/TizenTube) userscript for a privately patched TizenTube Cobalt APK.

The upstream app loads `cdn.jsdelivr.net/npm/@foxreis/tizentube/dist/userScript.js` without a version or integrity check. The patched APK loads `userScript.js` from the root of this repo through jsDelivr at a fixed commit instead, so the script only changes when the APK is rebuilt with a new commit.

## Source

- Upstream: https://github.com/reisxd/TizenTube, commit `f99945a84ff767bf14ad8c1146e8e3fd49a3d628` (2026-10-17, v1.15.2)
- Full patched source: `source/`
- Changes (also in `tizentube-pinned.patch`), modified by max-devzs on 2026-11-05:
  - `features/updater.js`: update checker removed (no calls to GitHub releases)
  - `resolveCommand.js`: `InstallAppFromURL` call removed
  - `ui/settings.js`: updater menu hidden
  - `config.js`: DeArrow off by default (an existing saved config keeps its old value)
- Unchanged upstream behaviour: SponsorBlock (on by default) calls `sponsor.ajay.app` with a 4-character hash prefix of the video ID; when YouTube shows its unsupported-device page, the script sets a spoofed TV user agent and reloads.
- Build: `cd source/mods && npm ci --ignore-scripts && npm run build`, then copy `source/dist/userScript.js` to the repo root.

Bundled dependencies (i18next, core-js, qrcode-npm, whatwg-fetch) are MIT licensed.

Licensed GPL-3.0-only, like upstream (see `LICENSE`).
