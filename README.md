# www-livive-net

Public GitHub Pages artifact for **https://www.livive.net/**.

This repo is generated — do not hand-edit it. The source catalog, media, and
build pipeline live in the private `backend-livive-net` repo. Running
`node publish.mjs` there writes the site into this checkout:

- `index.html`, `projects.json`, `previews.json`
- `p/<key>/` static project pages, `sitemap.xml`, `robots.txt`
- `thumbnails/`, `previews/`, `audio/`
- `404.html`, `status.html`, `status.json`, `og.png`, `favicon.ico`

`CNAME` (`www.livive.net`) and `README.md` are maintained here by hand.
