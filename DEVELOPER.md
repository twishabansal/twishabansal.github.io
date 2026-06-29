# DEVELOPER.md

Context and instructions for working on this blog (for humans and AI agents).

## Overview

Personal blog for Twisha Bansal, hosted on GitHub Pages.

- **Live URL:** https://twishabansal.github.io/
- **Repo:** `twishabansal/twishabansal.github.io` (public; must keep this exact name — it's a GitHub Pages *user site*, served at the root domain)
- **Generator:** [Hugo](https://gohugo.io/) (extended) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme
- **Theme is a git submodule** at `themes/PaperMod` — clone with `git clone --recurse-submodules`, or run `git submodule update --init --recursive` after a plain clone.

## Deployment

Deployment is fully automated. Every push to `main` triggers `.github/workflows/hugo.yml`, which builds the site with Hugo and deploys to GitHub Pages (~1 min). There is no manual deploy step and no `gh-pages` branch — Pages is configured with `build_type=workflow`.

Do **not** commit the `public/` directory; it's generated and gitignored.

## Adding a new post

1. Create the file:
   ```bash
   hugo new content posts/my-post-title.md
   ```
   The filename becomes the URL slug (`/posts/my-post-title/`). Use lowercase-with-hyphens.

2. Edit the frontmatter and write content below the `+++` block:
   ```markdown
   +++
   date = '2026-06-29T18:00:00-07:00'
   draft = false          # MUST be false to publish
   title = 'My Post Title'
   tags = ['tag1', 'tag2']
   +++

   Markdown content here.
   ```
   Key fields: set `draft = false`, give it a real `title` and `tags`.

3. Preview locally (optional):
   ```bash
   hugo server -D          # -D shows drafts; open http://localhost:1313/
   ```

4. Publish:
   ```bash
   git add content/posts/my-post-title.md
   git commit -m "post: my post title"
   git push
   ```

## Images

- Global assets: drop in `static/` (e.g. `static/images/foo.png`), reference as `/images/foo.png`.
- Per-post assets: use a [page bundle](https://gohugo.io/content-management/page-bundles/) (a folder per post with `index.md` + images).

## Configuration

Site-wide settings (title, bio, social links, menu, theme options) live in `hugo.toml`. The `baseURL` is `https://twishabansal.github.io/` and must match the live URL — do not change it unless the repo/hosting changes.

## Local build check

```bash
hugo --gc --minify     # builds to public/, mirrors what CI does
```

## Prerequisites

- Hugo extended (CI pins `0.148.2` in `.github/workflows/hugo.yml`; keep local version close to avoid drift).
- Git.
