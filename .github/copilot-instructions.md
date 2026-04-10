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

## Work Page (Resume) — `content/page/work.md`

The work page is a resume/portfolio. It has two sections separated by `---`:
1. **Professional projects** (top) — paid work, team roles, employer projects
2. **Side/open-source projects** (bottom) — personal or community contributions

**Structure of each entry:**
```markdown
### Project Name

One sentence: what the product does for its users (not tech-focused).

- **Role signal** — Accomplished [X] by doing [Z], resulting in [measurable Y].
- Additional bullet per distinct contribution.

![](/img/<project>.gif)
```

**Bullet formula — use the XYZ pattern:**
> "Accomplished **[X]** as measured by **[Y]**, by doing **[Z]**"

Every bullet should answer: *what did you do, how did you do it, and so what?* If a bullet lacks an outcome, add one or cut it.

**Signals to include (where true):**
- Scope: team size, user count, revenue/cost impact
- Scale: requests/sec, data volume, number of services
- Ownership level: "sole engineer", "tech lead across 5 engineers", "end-to-end ownership"
- Complexity: "legacy monolith", "zero-downtime migration", "regulated/compliance context"

**Writing rules:**
- Use `###` (h3) for all project headings — never `##` or `#`
- Lead each bullet with a strong past-tense verb: **Architected, Led, Designed, Built, Reduced, Increased, Migrated, Integrated, Owned** — never "Responsible for", "Helped with", or "Worked on"
- Bold the key technical noun in each bullet (e.g. `**event-driven microservices**`, `**CI/CD pipeline**`)
- One idea per bullet; 3–6 bullets per project
- Tech stack lives in the summary table — don't repeat it exhaustively in bullets; mention a technology in a bullet only when the *choice* was notable

**What to avoid:**
- Vague adjectives without evidence: "scalable", "robust", "high-performance" — show the number instead
- Passive voice: "was responsible for", "was involved in"
- Generic verbs: "worked on", "assisted", "participated"
- Orphan bullets with no outcome: "Implemented X" — add "which reduced Y by Z%"
- "Golang" — always write **Go** in markdown content

**Summary table at the top:**
- First column: project name as an anchor link `[Name](#anchor)`
- Second column: comma-separated tools/technologies (highest-signal first)
- Anchor slugs are lowercase, spaces replaced with `-` (e.g. `#payment-plan-advisor`)

**Images:**
- Place GIFs/images in `static/img/`
- Reference as `![](/img/<filename>)` — no alt text currently used
- Prefer GIFs for interactive/UI-heavy projects to show the product in action
