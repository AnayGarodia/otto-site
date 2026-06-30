# Otto website

Static landing page for Otto. Pure HTML/CSS — no build step.

- **Download button** → `https://otto-api.duckdns.org/otto/Otto-latest.dmg`
  (the DMG + Sparkle appcast are served by Caddy on the Otto backend box; `update.sh`
  publishes new releases there). The site never hosts the binary, so a deploy is instant
  and the download link always points at the latest release.
- **Version label** is fetched live from the appcast at load time.

## Deploy to Vercel (free)

The site is fully decoupled from the backend, so deploying is just hosting `index.html`.

1. Put this `site/` directory in its own GitHub repo (or keep it here and set the Vercel
   project's **Root Directory** to `site`).
2. vercel.com → **Add New → Project** → import the repo.
3. Framework preset: **Other**. Build command: none. Output dir: `.` (root).
4. Deploy. You get `https://<project>.vercel.app`.
5. Rename the project to claim a cleaner `*.vercel.app` subdomain under
   **Settings → Domains**.

No environment variables, no secrets — everything the page needs is public.

## Local preview

```sh
cd site && python3 -m http.server 8080   # → http://localhost:8080
```
