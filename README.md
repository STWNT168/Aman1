# English Dojo Tracker (英語道場)

A single-file progress tracker for Aman Sir's Complete English Course — belt ranks, XP, streaks, weak-topic flags with revision notes, and unlockable "seals" (badges). No build step, no backend: everything runs in one `index.html` and saves to your browser's `localStorage`.

## Use it

Just open `index.html` in a browser, or host it for free with GitHub Pages:

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under "Build and deployment", set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Save — your tracker will be live at `https://<your-username>.github.io/<repo-name>/`.

## Features

- 15 grammar chapters, 61 pre-seeded videos (renameable — edit the title inline to match the real video)
- Tap a chapter to expand/collapse it
- Check off videos as watched — earns XP and progresses your belt rank
- Flag a topic as weak (⚑) to reveal a notes field for what to revise
- Daily study streak, tracked automatically when you check something off
- 9 unlockable seals for milestones (first video, 25%/50%/100% progress, streak length, etc.)
- Filter by All / Unwatched / Watched / Weak / Seals
- Export your progress to a JSON backup file, and import it back later or on another device
- Add or delete individual video rows per chapter

## Installing as an app

The repo includes a real `manifest.json`, `icons/` (192px, 512px, and a maskable 512px version), and a `sw.js` service worker that caches the app shell for offline use. Once it's hosted (e.g. via GitHub Pages), most browsers will offer an "Install" / "Add to Home Screen" prompt, and it'll run full-screen and work offline like a native app.

**Icons showing a 404?** Double-check that the whole `icons/` folder was actually pushed/uploaded — dragging individual files into the GitHub web UI can silently skip folders. Confirm you can browse to `https://<username>.github.io/<repo>/icons/icon-192.png` directly; if that 404s, the folder isn't in the deployed branch. A `git add -A && git commit && git push` from a full local clone (rather than the web upload UI) avoids this.

**Updating the site later?** If you edit `index.html`, bump `CACHE_NAME` in `sw.js` (e.g. `eigo-dojo-v1` → `eigo-dojo-v2`) so returning visitors get the new version instead of a stale cached copy.

## Data & privacy

Progress is stored only in your browser's `localStorage`, under the key `eigo-dojo-state`. Nothing is sent anywhere. Clearing your browser data (or using a different browser/device) will reset it — use **Export backup** periodically if you want a copy, and **Import backup** to restore it.

## Customizing

- **Chapters/video counts**: edit the `CHAPTERS` array near the top of the `<script>` block in `index.html`.
- **Belt thresholds/colors**: edit the `BELTS` array.
- **Seals**: edit the `BADGES` array (each has an `icon`, `name`, `desc`, and a `check(stats)` function).

## License

MIT — do whatever you like with it.
