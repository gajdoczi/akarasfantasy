# RIFT DRAFT — Render deployment

This folder is set up to deploy as a static site on [Render](https://render.com).

## Option A — Blueprint (recommended, one click)

1. Push this folder (`index.html`, `render.yaml`) to a GitHub/GitLab repo.
2. In the Render dashboard: **New → Blueprint**, point it at the repo.
3. Render reads `render.yaml` and creates a **Static Site** called `rift-draft` automatically — no build command needed, it just serves `index.html`.
4. Deploy. You'll get a URL like `https://rift-draft.onrender.com`.

## Option B — Manual static site (no render.yaml needed)

1. Push the repo (just `index.html` is enough).
2. Render dashboard → **New → Static Site**.
3. Build command: *(leave blank)*
4. Publish directory: `.`
5. Deploy.

## Notes

- This is a pure client-side app (HTML/CSS/JS, no server code), so any static host works the same way — Render, Netlify, GitHub Pages, Vercel, etc.
- Data (squads, matches, custom players, login) is saved with `localStorage` **in each visitor's own browser**. Deploying to a real `https://` URL actually makes this more reliable than opening the file directly (`file://` URLs have flaky/blocked localStorage in some browsers, notably Chrome).
- Because there's no backend/database, the "leaderboard" is still per-browser — two different people visiting the Render URL each see only their own saved squad, not each other's. If you want a real shared leaderboard across visitors, that needs an actual backend (e.g. a small Render **Web Service** with a database) — let me know if you want that built out.
