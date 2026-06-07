# ReadSprint — Installable App (PWA)

Your 20-book reading sprint, packaged as an installable app that works offline.

## What's in this folder
- `index.html` — the app
- `manifest.json` — app name, icon, colors
- `sw.js` — service worker (offline support)
- `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` — app icons
- `icon.svg` — source icon (optional)

> A PWA must be served over **https** (or `localhost`). Opening `index.html`
> directly from your file system will run the app, but the *install* and
> *offline* features only switch on once it's hosted. Use one of the options below.

---

## Option A — Put it online for free (recommended, ~5 min)

### Netlify Drop (easiest, no account needed to start)
1. Go to **https://app.netlify.com/drop**
2. Drag this **entire folder** onto the page.
3. You get a live URL like `https://readsprint.netlify.app`.

### GitHub Pages
1. Create a repo, upload all files in this folder to the root.
2. Settings → Pages → Branch: `main` / root → Save.
3. Your URL: `https://<username>.github.io/<repo>/`

### Vercel
1. Install: `npm i -g vercel`
2. In this folder run: `vercel` and follow the prompts.

---

## Option B — Install on your phone
1. Open your hosted URL in **Safari (iPhone)** or **Chrome (Android)**.
2. **iPhone:** Share button → *Add to Home Screen*.
   **Android:** menu (⋮) → *Install app* / *Add to Home Screen*.
3. Launch it from your home screen — full screen, with its own icon, works offline.

---

## Option C — Test offline locally first
From this folder:
```
python3 -m http.server 8080
```
Open `http://localhost:8080` — the service worker will register and cache the app.

---

## Notes
- **Data storage:** progress, notes and points are saved in the browser's local
  storage on the device where you use it. It is *not* synced across devices and
  can be lost if you clear browser data. For cross-device cloud sync, the next
  step is adding a backend (e.g. Supabase) — ask and I'll wire it up.
- **Updating the app:** when you change `index.html`, bump `CACHE = "readsprint-v1"`
  in `sw.js` (e.g. to `v2`) so phones pick up the new version.
