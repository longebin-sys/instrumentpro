# InstrumentPro Toolbox

A mobile-first, installable field toolbox for instrumentation technicians — unit conversion, calibration (pressure, RTD/thermocouple, analytical), level DP, flow, electrical, tube bending, commissioning checklists, a fault-finding guide, tag scanning with OCR, and field reports. Works offline once installed.

## Files in this repo

| File | Purpose |
|---|---|
| `index.html` | The entire app (HTML/CSS/JS in one file) |
| `manifest.json` | PWA manifest — lets the app be installed/saved to a home screen |
| `service-worker.js` | Caches the app shell so it works offline once installed |
| `icons/` | App icons (various sizes + a maskable Android icon + favicon) |

No build step, no dependencies to install — it's a static site.

## Hosting on GitHub Pages

1. Push this whole folder to a GitHub repo (keep `index.html`, `manifest.json`, `service-worker.js`, and `icons/` all in the same top-level folder — the paths inside the app are relative).
2. In the repo, go to **Settings → Pages**.
3. Under **Source**, choose the branch (usually `main`) and folder `/ (root)`.
4. Save. GitHub will give you a URL like `https://yourusername.github.io/your-repo-name/`.
5. Open that URL — the app should load fully styled with icons.

**Important:** Service workers and install prompts only work over **HTTPS** (GitHub Pages is HTTPS by default) — they will not work if you just double-click `index.html` locally from disk (`file://`). To test locally with full PWA behavior, run a local server, e.g.:

```bash
python3 -m http.server 8000
```

then open `http://localhost:8000`.

## Installing it as an app

- **Android (Chrome/Edge):** open the site, tap the **Install App** button under Settings, or use the browser's own "Install app" / "Add to Home Screen" menu option.
- **iPhone/iPad (Safari):** tap the Share icon, then **Add to Home Screen** — iOS doesn't support the automatic install prompt, so this is the way to do it there.
- **Desktop (Chrome/Edge):** an install icon will appear in the address bar.

Once installed, it opens full-screen (no browser bar) and keeps working without a signal, since the app shell is cached locally.

## Updating the app later

If you edit `index.html` (or anything else) after it's already installed on a device, bump the version number in `service-worker.js`:

```js
const CACHE_NAME = 'instrumentpro-cache-v1'; // change to v2, v3, etc.
```

This forces installed copies to fetch the new version instead of serving the old cached one.

## Data storage

All calibration history, saved tags, uploaded file names, and settings are stored in the browser's `localStorage` on-device only — nothing is sent to a server. Clearing browser data (or using "Clear Data" in Settings) will erase them.
