# www-livive-net

Public GitHub Pages artifact for **https://www.livive.net/**.

> **Generated repo — do not hand-edit.** The source catalog, media, pipeline, and
> QA live in the private `backend-livive-net` repo. This checkout is written by
> `node publish.mjs` there.

## What lives here

| Path | Source |
| --- | --- |
| `index.html` | `build_site.mjs` (interactive catalogue template) |
| `projects.json`, `previews.json` | backend catalogs (patched for publication) |
| `p/` | `_bootstrap/render.mjs` static project pages |
| `sitemap.xml`, `robots.txt` | `_bootstrap/render.mjs` |
| `404.html`, `status.html`, `status.json` | backend static assets + `monitor.py` output |
| `og.png`, `favicon.ico` | backend root |
| `thumbnails/`, `previews/`, `audio/` | backend media source |
| `CNAME` | maintained here by hand (`www.livive.net`) |
| `README.md` | maintained here by hand |

## Deploy

`.github/workflows/deploy.yml` publishes the repository root to GitHub Pages on
every push to `main`. `CNAME` binds the site to `www.livive.net`; no DNS change
is needed for normal publishes.

## Rebuild

From the backend:

```bash
node publish.mjs
git -C www-livive-net add -A
git -C www-livive-net commit -m "chore(publish): rebuild site"
git -C www-livive-net push origin main
```

CI can do the same via the `publish-www` workflow once `WWW_DEPLOY_TOKEN` is set.

## Rollback

Revert to a prior commit in this repo, then bump the backend submodule pointer:

```bash
git log --oneline
git revert <bad-commit>
git push origin main
```

## Notes

- `publish.mjs` does **not** overwrite `CNAME` or this README.
- `p/*` pages and `sitemap.xml` are generated from `projects.json`; adding a
  project requires a backend change, not a change here.
- If the site looks stale after a backend monitor commit, re-run `publish.mjs`
  in the backend and push.
