# tizentube-pinned

A pinned, patched build of the [TizenTube](https://github.com/reisxd/TizenTube) userscript for a privately patched TizenTube Cobalt APK.

The upstream app loads `cdn.jsdelivr.net/npm/@foxreis/tizentube/dist/userScript.js` without a version or integrity check. The patched APK loads `userScript.js` from this repo through jsDelivr at a fixed commit instead, so the script only changes when this repo changes.

## Source

- Upstream: https://github.com/reisxd/TizenTube, commit `f99945a84ff767bf14ad8c1146e8e3fd49a3d628` (2026-10-17, v1.15.2)
- Changes: `tizentube-pinned.patch`
  - `features/updater.js`: update checker removed (no calls to GitHub releases)
  - `resolveCommand.js`: `InstallAppFromURL` call removed
  - `config.js`: DeArrow off by default
- Build: `cd mods && npm ci --ignore-scripts && npm run build` (output `dist/userScript.js`)

Licensed GPL-3.0-only, like upstream (see `LICENSE`).
