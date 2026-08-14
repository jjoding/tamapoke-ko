# TamaPoke web installer

A one-click page that flashes the firmware and loads the sprites from the browser
(Chrome/Edge), with no Arduino or drivers. It uses
[ESP Web Tools](https://esphome.github.io/esp-web-tools/) to flash and **Web
Serial** to push the sprites to the SD with the firmware's `PUT` protocol (the
same one as `tools/send_sd.py`).

## Contents

- `index.html` — the page (flashing + sprite loader).
- `manifest.json` — ESP Web Tools config (points at the firmware).
- `firmware/tamapoke.bin` — combined firmware, flashable at `0x0`.
- `sprites.pak` — all the sprites in one bundle (TPAK), so the page sends them in
  one click. **Generated** by `tools/pack_bundle.py` (gitignored by default — see
  *Hosting the sprites* below).

## Regenerate

After changing the firmware or the sprites:

```bash
bash tools/build_web.sh        # recompiles -> firmware/tamapoke.bin AND rebuilds sprites.pak
```

## Test locally

Web Serial and ESP Web Tools need a **secure context**: `https://` or
`http://localhost`. To test:

```bash
cd web && python3 -m http.server 8000
# open http://localhost:8000 in Chrome/Edge
```

## End-user flow

1. **First install:** visit the [original TamaPoke installer](https://socquique.github.io/TamaPoke/web/)
   first, install the original firmware, then load its sprites and confirm that
   the board works.
2. Return to this page and install the Korean firmware **without erasing**.
   This preserves the save data and the sprites already copied to the microSD.
3. The Korean page is firmware-only and has no sprite installation area. Install
   sprites from the original page in step 1.
4. Restart (PWR button) → choose your starter and play.

Never select full **Erase** when switching from the original firmware to the
Korean firmware unless a complete save reset is intended.

A hidden "pick them manually" option lets advanced users send their own `.bin`.

## Hosting the sprites

`sprites.pak` is large and should not be uploaded to the Korean repository. The
page downloads it from the original project host:

```text
https://socquique.github.io/TamaPoke/web/sprites.pak
```

Install the original sprites first as described above. To make
the one-click sprite loader work on a real deployment, the original host must
permit cross-origin requests. If it does not, use the original installer for
the sprite step. Do not copy or re-host the bundle without checking the
original project's terms.

Older alternative hosting options (not used by this release) were:

- **Commit it** — add `web/sprites.pak` to git and serve it from Pages. Simple,
  but doubles the repo's sprite size.
- **Release asset** — attach `sprites.pak` to a GitHub Release and change the
  `fetch('sprites.pak')` URL in `index.html` to the release URL (keeps the repo
  small; watch out for CORS on the asset host).

All sprites are from PMD SpriteCollab, CC BY-NC (non-commercial sharing with
attribution is allowed); see [`../CREDITS.md`](../CREDITS.md).

## Deploy (GitHub Pages)

1. Repo settings → Pages → serve from `main`, folder `/web` (or move `web/` to
   `docs/`). Pages gives HTTPS automatically.
2. URL ends up at `https://<user>.github.io/<repo>/`.

> **Pages on private repos** needs GitHub Pro/Team. If you make the repo
> **public** to use Pages for free, decide about the sprites first (see above and
> CREDITS).

## Limitations

- Desktop **Chrome/Edge** only (Web Serial isn't in Firefox/Safari).
