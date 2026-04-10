# Copilot Instructions

This is a Hugo static site for [rayspock.com](https://rayspock.com) — a personal blog and portfolio.

## Commands

- **Dev server** (with drafts): `make run` → runs `hugo -D server`
- **Production build**: `hugo --minify`
- **Deploy**: Automatic via GitHub Actions on push to `main` — builds with Hugo 0.149.0 extended and deploys to the `gh-pages` branch

## Architecture

- **Theme**: `hello-friend-ng`, included as a git submodule at `themes/hello-friend-ng`
- **Content types**:
  - `content/page/` — static pages (about, work)
  - `content/posts/<slug>/` — blog posts as page bundles (each post is a directory with `index.md` + co-located assets)
- **Custom overrides**: `layouts/partials/extra-head.html` injects Hotjar tracking and sets the default theme via `localStorage`
- **Custom CSS**: `static/css/blog.css`
- **Site config**: `config.yaml` (single file, no environment splits)

## Content Conventions

New posts go in `content/posts/<slug>/index.md` as page bundles. Use `hugo new posts/<slug>/index.md` to scaffold from the archetype (sets title, date, `draft: true`).

Standard frontmatter for posts:
```yaml
---
title: "Post Title"
date: YYYY-MM-DD
tags: ["tag1", "tag2"]
share_img: posts/<slug>/<image-file>
summary: "Brief summary shown in previews"
draft: true
---
```

- Post images are co-located in the same directory as `index.md`
- `share_img` path is relative to the `content/` directory
- Remove `draft: true` before merging to `main` so the post is published
