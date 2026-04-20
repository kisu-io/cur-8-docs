# Deploy to GitHub Pages

The `docs/` folder is a static site. GitHub Pages can serve it directly with no build step.

## One-time setup

1. Push this repo to GitHub.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, pick **Deploy from a branch**.
4. Under **Branch**, pick `main` (or your default branch) and the `/docs` folder.
5. Click **Save**. Wait 30–60 seconds for the first deploy.

Your site will be live at `https://<user>.github.io/<repo>/`.

## Rebuilding

When you edit markdown in `07_wiki/`, rerun the build:

```bash
pip install markdown
python3 build_site.py
git add docs
git commit -m "Rebuild wiki"
git push
```

GitHub Pages will auto-redeploy on push.

## Notes

- `.nojekyll` is in this folder so GitHub Pages does not try to run Jekyll on the output.
- `style.css` is the single stylesheet shared by every page.
- `index.html` is rendered from `07_wiki/Home.md`.
- Dead `[[wikilinks]]` render in red with `(missing)` appended — fix the link target or the source page, then rebuild.
- Build script entry point: `build_site.py` at the repo root (one level up from `docs/`).
