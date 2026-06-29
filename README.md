# twishabansal.github.io

Source for my personal blog, live at **https://twishabansal.github.io/**.

Built with [Hugo](https://gohugo.io/) (extended) and the
[PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, hosted on
GitHub Pages. Every push to `main` is built and deployed automatically by the
GitHub Actions workflow in `.github/workflows/hugo.yml` — there is no manual
deploy step.

## Run locally

The PaperMod theme is a git submodule, so clone with submodules:

```bash
git clone --recurse-submodules https://github.com/twishabansal/twishabansal.github.io.git
cd twishabansal.github.io
hugo server -D          # http://localhost:1313/ (-D includes drafts)
```

(After a plain clone, run `git submodule update --init --recursive`.)

## Add a post

```bash
hugo new content posts/my-post.md     # then set draft = false and write
git add content/posts/my-post.md
git commit -m "post: my post"
git push                               # auto-deploys in ~1 min
```

See [`DEVELOPER.md`](./DEVELOPER.md) for the full workflow, including frontmatter
fields, images, and configuration.

## Layout

- `content/posts/` — blog posts (Markdown)
- `hugo.toml` — site config (title, menu, theme options)
- `static/` — images and other static assets
- `themes/PaperMod/` — theme (git submodule)
- `.github/workflows/hugo.yml` — build + deploy to GitHub Pages
