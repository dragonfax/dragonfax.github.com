# CLAUDE.md

## What This Repository Is

This is the source for "Zero, but True", a personal blog by Jason Stillwell, served via GitHub Pages at jason-stillwell.com. It uses **Hugo** with the **PaperMod** theme.

## Build & Preview

- `hugo server` — local dev server with live reload at localhost:1313
- `hugo server --buildDrafts` — include draft posts
- `hugo` — build static site to `public/`

## Creating a New Post

```bash
hugo new content posts/my-new-post.md
```

Then edit `content/posts/my-new-post.md` and set `draft: false` when ready to publish.

## Project Structure

- `content/posts/` — blog posts (Markdown)
- `content/about.md` — about page
- `hugo.toml` — site configuration
- `layouts/partials/comments.html` — Giscus comments override
- `static/` — static files (CNAME, favicon, images)
- `themes/PaperMod/` — theme (git submodule, don't edit directly)
- `.github/workflows/hugo.yaml` — GitHub Actions deployment

## Deployment

Automatic via GitHub Actions on push to `master`. The workflow builds with Hugo and deploys to GitHub Pages.

## Key Config

- Permalink pattern: `/blog/YYYY/MM/DD/slug/`
- Theme: PaperMod (git submodule)
- Comments: Giscus (GitHub Discussions-based)
- No analytics
