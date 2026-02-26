# OpenTEAM Option 1 Demo (GitHub-native, data-driven cards)

This repo is a *testable* starter that:
- Stores content as JSON in `src/content/**`
- Builds static pages with Eleventy (11ty)
- Provides a no-code Admin UI at `/admin` via Decap CMS
- Deploys to GitHub Pages automatically (GitHub Actions)

## Run locally
```bash
npm install
npm run dev
```
Open: http://localhost:8080

## Deploy to GitHub Pages
1. Create a new GitHub repo and push this code to the `main` branch.
2. GitHub → **Settings → Pages** → Source: **GitHub Actions**
3. Push to `main`. The included workflow builds and deploys.

## Admin UI (Decap CMS)
1. Edit `src/admin/config.yml` and set:
   - `repo: YOUR_GITHUB_USER/YOUR_REPO`
2. Commit + push.
3. Visit:
   - `https://YOUR_GITHUB_USER.github.io/YOUR_REPO/admin/`

> Decap’s GitHub backend requires OAuth configuration. If you want, I can provide a “copy/paste” OAuth setup checklist for GitHub Pages.

## Content structure
- Projects: `src/content/projects/*.json`
- Tools: `src/content/tools/*.json` (includes `assessment` object)
- Datasets: `src/content/datasets/*.json` (includes `assessment` object)


## Troubleshooting: blank page / missing CSS on GitHub Pages
GitHub Pages serves project sites under a subpath like:
`https://USER.github.io/REPO/`

If your site uses absolute paths like `/assets/...`, they will 404.
This starter sets `ELEVENTY_PATH_PREFIX` during the GitHub Actions build, and uses `| url` in templates so links work under `/REPO/`.

If you fork/rename the repo, just redeploy — the workflow uses the repo name automatically.
