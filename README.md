# webs-aight

Source for [derekwakefield.com](https://derekwakefield.com), built with [Quarto](https://quarto.org) and deployed via GitHub Pages.

## Edit and preview locally

```powershell
quarto preview
```

The site builds at `http://localhost:4444`. Edit any `.qmd` file and the page reloads automatically.

## Pages

- `index.qmd` — Home (About + Background)
- `research.qmd` — Dissertation, publications, working papers
- `teaching.qmd` — Awards and courses
- `service.qmd` — Service positions, SOCA, PRESS
- `cv.qmd` — CV (links to `assets/cv.pdf`)
- `now.qmd` — Now page, updated monthly
- `writing.qmd` — Longer-form posts, listed from `posts/`

## Add a writing post

Create a new file in `posts/`, e.g. `posts/2026-05-15-some-thoughts.qmd`:

```yaml
---
title: "Some thoughts on something"
date: "2026-05-15"
description: "One-sentence summary that shows up in the listing."
---

Body goes here.
```

It appears automatically on `writing.qmd` once you push.

## Update Now

Edit `now.qmd`. Replace the current month with the new one. Move the previous month's content into the "Past months" section.

```powershell
git add now.qmd
git commit -m "May 2026 Now"
git push
```

## Deploy

Every push to `main` triggers `.github/workflows/publish.yml`, which builds the site with Quarto and publishes the result to the `gh-pages` branch. GitHub Pages serves that branch at https://derekwakefield.com.

Manual one-off publish (rarely needed):

```powershell
quarto publish gh-pages
```

## Repo layout

```
webs-aight/
├── _quarto.yml             # Site config (nav, theme, footer)
├── index.qmd               # Home
├── research.qmd
├── teaching.qmd
├── service.qmd
├── cv.qmd
├── now.qmd
├── writing.qmd
├── styles.css              # Light styling layered over Cosmo theme
├── README.md
├── .gitignore
├── assets/
│   ├── cv.pdf              # Drop your current CV here
│   └── headshot.jpg        # Drop a ~600x600 headshot here
├── posts/                  # Writing posts (one .qmd file per post)
└── .github/
    └── workflows/
        └── publish.yml     # Auto-deploy on push
```

## Theme

Currently using [Cosmo](https://bootswatch.com/cosmo/) (light) and [Darkly](https://bootswatch.com/darkly/) (dark, auto-toggled by reader preference). Change in `_quarto.yml` under `format.html.theme`.
