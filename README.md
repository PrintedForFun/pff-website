# PrintedForFun website

Static site for PrintedForFun, hosted on GitHub Pages at https://printedforfun.com. No build step and no external requests (fonts, scripts, trackers).

| File | Purpose |
| --- | --- |
| `index.html` | Landing page: services, projects gallery, contact |
| `impressum.html` | Legal notice / Impressum (§ 5 DDG) |
| `privacy.html` | Privacy policy (GDPR) |
| `404.html` | Not-found page |
| `assets/styles.css` | All styles; brand colours are the tokens at the top |
| `assets/work/` | Project images: `name.jpg` (max 1600 px) and `name-800.jpg` (thumbnail) |
| `assets/og-image.jpg` | 1200×630 preview image for links shared on social media |
| `assets/icon-*.png` | Favicons generated from `logo.png` |
| `CNAME`, `robots.txt`, `sitemap.xml`, `site.webmanifest` | Domain and search engine files |

`_originals/` holds the full-resolution source images locally and is git-ignored.

Preview locally: `python -m http.server 8000`, then open http://localhost:8000.

## Adding a project image

1. Export a JPEG at max 1600 px wide as `assets/work/<name>.jpg` and an 800 px copy as `assets/work/<name>-800.jpg`.
2. Copy an existing `<figure class="shot">` block in `index.html` and update the paths, `width`/`height` (of the 800 px file), `alt` and caption.
3. Add `<lastmod>` updates to `sitemap.xml` if the page changed significantly.

## Deploy

1. Push to `main` on GitHub.
2. Repo → **Settings → Pages** → Source: *Deploy from a branch*, `main` / `/ (root)`.
3. Custom domain: `printedforfun.com` (already in `CNAME`). Enable **Enforce HTTPS** once the certificate is issued.

### Cloudflare DNS

Add four `A` records for `printedforfun.com` pointing to GitHub Pages:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

and a `CNAME` record `www` → `<github-username>.github.io`.

Set the records to **DNS only** (grey cloud) until GitHub has issued the HTTPS certificate. If you switch the proxy on afterwards, set Cloudflare **SSL/TLS** mode to **Full (strict)** to avoid redirect loops.
