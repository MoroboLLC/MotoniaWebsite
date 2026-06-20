# Motonia — Landing Page

The official landing page for **Motonia**, the sportbike app for 3D navigation and live
group rides. A single, fast, self-contained static page. Part of **Morobo LLC**.

- **Live app:** [App Store](https://apps.apple.com/us/app/motonia/id6760694800) · [Google Play](https://play.google.com/store/apps/details?id=com.motonia.android)
- **Domain:** motonia.org (served via GitHub Pages)

## Structure

```
index.html          # the page
styles.css          # all styles (self-hosted fonts declared here)
site.webmanifest    # PWA manifest
CNAME               # custom domain for GitHub Pages (motonia.org)
assets/
  motonia-logo.png  # real app logo (teal globe, transparent background)
  icon-512.png      # 512px icon (apple-touch / social preview)
  favicon.png       # 128px favicon
  fonts/            # self-hosted Sora + Inter (woff2) — no external requests
```

## Local preview

Any static server works, e.g.:

```bash
python -m http.server 5050
# then open http://localhost:5050
```

## Adding the cinematic video background

The page is built black and ready for footage. To use a looping motorcycle clip:

1. Drop `hero.mp4` (and optionally a `poster.jpg` first frame) into `assets/`.
2. In `index.html`, uncomment the `<video class="bg-video">` block inside `.bg`.

The `.bg-overlay` already darkens the footage so the white text stays legible.
Keep the clip short, muted, and compressed (1080p, a few MB) for fast loading.

## Deploy to GitHub Pages (motonia.org)

1. Create a GitHub repo (e.g. `motonia-website`) and push this folder to it.
2. Repo **Settings → Pages**: set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. Under **Custom domain**, enter `motonia.org` (the `CNAME` file already pins this).
4. At your domain registrar, point DNS at GitHub Pages:

   **Apex (`motonia.org`) — A records:**
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
   **(optional IPv6) — AAAA records:**
   ```
   2606:50c0:8000::153
   2606:50c0:8001::153
   2606:50c0:8002::153
   2606:50c0:8003::153
   ```
   **`www` subdomain — CNAME record:** `<your-username>.github.io`

5. Back in Settings → Pages, tick **Enforce HTTPS** once the certificate is issued
   (can take a few minutes to an hour after DNS propagates).
