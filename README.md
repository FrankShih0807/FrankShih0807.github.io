# frankshih0807.github.io

Personal academic website for Frank Shih. Built on the [al-folio](https://github.com/alshedivat/al-folio) Jekyll template.

---

## Quick deploy (first time)

### 1. Create the GitHub repo
On GitHub, create a new **public** repo named exactly:

```
FrankShih0807.github.io
```

Do **not** initialize it with a README — we already have one.

### 2. Push this folder to it

From inside this directory (`/Users/frankshih/Cowork/personal-site`):

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/FrankShih0807/FrankShih0807.github.io.git
git push -u origin main
```

### 3. Enable GitHub Pages with Actions
1. Go to the repo on GitHub → **Settings** → **Pages**.
2. Under **Build and deployment** → **Source**, pick **GitHub Actions**.
3. al-folio ships with a ready-made workflow at `.github/workflows/deploy.yml`, so the first push should trigger a build automatically.

Within a few minutes your site will be live at:

```
https://frankshih0807.github.io
```

---

## Where to edit content

| What to change          | File / folder                              |
|-------------------------|--------------------------------------------|
| Name, email, site title | `_config.yml`                              |
| About-page bio + photo  | `_pages/about.md` (photo at `assets/img/prof_pic.jpg`) |
| Research news updates   | `_news/announcement_*.md` (one file per item) |
| Publications            | `_bibliography/papers.bib`                 |
| CV sections (web page)  | `_data/cv.yml` (al-folio format)           |
| Master CV (all variants)| `cv.master.yml` (repo root — source of truth for PDFs) |
| Social links            | `_data/socials.yml`                        |
| Blog posts              | `_posts/YYYY-MM-DD-title.md`               |

### Drop your headshot
Save as `assets/img/prof_pic.jpg` (JPG or PNG), ~500×500px works well.

### Add your CV PDF
Save as `assets/pdf/frank_shih_cv.pdf`. The Download-PDF button on `/cv` will pick it up automatically.

---

## Local preview (optional)

al-folio ships with a Docker setup, which is by far the easiest way to preview locally.

```bash
docker compose pull
docker compose up
# then open http://localhost:8080
```

Without Docker, you need Ruby + Bundler:

```bash
bundle install
bundle exec jekyll serve
```

---

## CV workflow

- `cv.master.yml` at the repo root is the **source of truth** for all CV variants.
  Every entry is tagged with an `audience:` list (`academic`, `grant`, `industry`, etc.).
- `_data/cv.yml` is an al-folio-shaped view of the same information — it drives the web `/cv` page.
- PDF variants (coming next) will be built by [RenderCV](https://rendercv.com/) from `cv.master.yml`.

When you update the CV, edit `cv.master.yml` first. The web version and PDFs are re-derived from it.
