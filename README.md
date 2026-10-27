# PrintedForFun website

Static landing page for PrintedForFun, hosted on GitHub Pages. No build step and no external requests (fonts, scripts, trackers).

| File | Purpose |
| --- | --- |
| `index.html` | Landing page with contact and social links |
| `impressum.html` | Legal notice / Impressum (§ 5 DDG) |
| `privacy.html` | Privacy policy (GDPR) |
| `404.html` | Not-found page |
| `assets/` | Stylesheet and logo |
| `CNAME` | Custom domain for GitHub Pages (one line, e.g. `example.com`) |

Preview locally: `python -m http.server 8000`, then open http://localhost:8000.

## Deploy

1. Push to `main` on GitHub.
2. Repo → **Settings → Pages** → Source: *Deploy from a branch*, `main` / `/ (root)`.
3. Same page → **Custom domain**: enter the domain (this writes/uses `CNAME`), then enable **Enforce HTTPS** once the certificate is issued.

### Cloudflare DNS

For the apex domain (`example.com`) add four `A` records pointing to GitHub Pages:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

and a `CNAME` record `www` → `<github-username>.github.io`.

Set the records to **DNS only** (grey cloud) until GitHub has issued the HTTPS certificate. If you switch the proxy on afterwards, set Cloudflare **SSL/TLS** mode to **Full (strict)** to avoid redirect loops.
