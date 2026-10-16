# Sector ZerØ — custom icon + offline-ready PWA

This folder is a web app package intended to be hosted over HTTPS (for example, GitHub Pages). It keeps the supplied game HTML, adds a custom Sector ZerØ icon/manifest, and adds a service worker that caches the game page and successfully loaded external resources for later offline use.

## Install/update on Android
1. Upload **the contents of this folder** to the root of your existing GitHub Pages repository, replacing the old `index.html` and adding `manifest.webmanifest`, `service-worker.js`, and the `icons` folder.
2. Wait for the site to redeploy, then open the same HTTPS game URL in Chrome while online.
3. Reload once if necessary, launch the game and wait for it to fully load. The service worker saves the page and external files the game requests.
4. If the old installed app still shows the old icon, remove that old home-screen app and install it again from Chrome's menu. The new install should use the custom icon.
5. To test offline, visit the game online first, fully load it, then enable Airplane mode and reopen the installed app.

## Offline limitations
- The original game imports Three.js and web fonts from CDNs. This package uses a runtime cache for those resources; they must successfully load once while online before they can be available offline.
- If a CDN changes its URL or a resource never loaded during the online session, that resource may not be cached. Fonts are optional; the browser can fall back to system fonts.
- This package was assembled but cannot be tested on your specific phone from this environment. Please test Airplane mode before relying on offline play.
- Do not open `index.html` as a raw local file and expect PWA installation/offline caching; the service worker requires an HTTPS origin (localhost is the usual development exception).
