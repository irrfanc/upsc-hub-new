# UPSC Command Hub — PWA

Installable version of your hub (all 4 apps: Prelims Tracker, Prelims Command, Mains Command, Writing Practice — still one self-contained `index.html`, now with an app icon, offline support, and "Install" prompts on desktop/mobile).

## Files
- `index.html` — the app itself
- `manifest.json` — name, icons, theme color, display mode
- `sw.js` — service worker (caches everything so it works fully offline after first load)
- `icons/` — all icon sizes incl. maskable variants for Android

## Important: PWAs require a real server (not double-clicking the file)
Browsers only allow service workers / "Add to Home Screen" over **HTTPS or localhost** — never over `file://`. Opening `index.html` directly will still work as a normal page, just without install/offline features.

### Fastest way to test locally
```
cd upsc-hub-pwa
python3 -m http.server 8080
```
Then open `http://localhost:8080` in Chrome/Edge — you'll see an install icon in the address bar (desktop) or an "Add to Home Screen" prompt (mobile).

### Deploy for real (pick one, all free, all drag-and-drop)
- **Netlify Drop**: app.netlify.com/drop → drag the whole `upsc-hub-pwa` folder in. Done.
- **Vercel**: `vercel` CLI or vercel.com → import the folder.
- **GitHub Pages**: push the folder to a repo → enable Pages on the `main` branch.

Once it's live on any of these, open the link on your phone and use "Add to Home Screen" — it'll behave like a native app icon, launch full-screen, and keep working offline.

## Updating later
If you change `index.html`, bump `CACHE_NAME` in `sw.js` (e.g. `upsc-hub-v2`) so returning users actually get the new version instead of a stale cached copy.
