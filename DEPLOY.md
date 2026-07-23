# Deploying your portfolio to GitHub Pages

Your site is a single self-contained `index.html` (no build step). Live URL will be **https://armandcaft.github.io**.

## 1. Create the repository

Create a **public** repo named exactly:

```
armandcaft.github.io
```

(The `username.github.io` name is what makes it a GitHub Pages **user site**, served at the root domain automatically.)

## 2. Add the files

Put these at the **repo root**:

```
armandcaft.github.io/
├── index.html                        ← the site
└── assets/
    ├── Christian_Armand_Tchuente_CV_EN.pdf
    └── Christian_Armand_Tchuente_CV_FR.pdf
```

- **CV files:** export your two CVs (`.docx`) to **PDF** and name them exactly as above so the "Download CV" button works. (Or edit the two `href="assets/…"` paths in `index.html` to whatever you name them.)

Upload via **git**:

```bash
git init
git add .
git commit -m "Portfolio v1"
git branch -M main
git remote add origin https://github.com/Armandcaft/armandcaft.github.io.git
git push -u origin main
```

…or via the browser: **Add file → Upload files** on the repo page.

## 3. Enable Pages

For a `username.github.io` repo it usually goes live automatically. If not:
**Settings → Pages → Source = Deploy from a branch → `main` / `root` → Save.**
Give it ~1 minute, then visit **https://armandcaft.github.io**.

## 4. Two quick post-launch edits (recommended)

1. **Make the ArbreGénéa repo public** (it's your strongest piece). Then, in `index.html`, find the ArbreGénéa card's link line:

   ```html
   <div class="plinks"><span class="plink muted" data-i18n="common.privateRepo">Private repo — available on request</span></div>
   ```

   and replace it with a real link:

   ```html
   <div class="plinks"><a class="plink" href="https://github.com/Armandcaft/ArbreGenea" target="_blank" rel="noopener" data-i18n="common.viewRepo">View repository</a></div>
   ```

   (Same swap works for the Email Microservice and SFO cards if/when you make those public.)

2. **Add the READMEs** — commit each provided README as `README.md` at the root of its repo (FileStorageApi, ArbreGénéa, copilothrm-email).

## 5. Later (optional): custom domain

Buy a domain (e.g. `christiantchuente.dev`), then **Settings → Pages → Custom domain**, add it, and create the DNS records GitHub shows. GitHub provisions HTTPS automatically.

---

### Notes
- The site remembers the visitor's language choice (`localStorage`) and defaults to the browser language, falling back to English.
- Only make the Portfolio link on your CV "live" once the page is actually up — a 404 hurts more than no link.
