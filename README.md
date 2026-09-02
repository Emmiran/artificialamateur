# Artificial Amateur

Personal blog about learning to use AI. Built with [Astro](https://astro.build), deployed to GitHub Pages at [artificialamateur.com](https://artificialamateur.com).

## Writing a post

Add a new Markdown file to `src/content/blog/`, e.g. `src/content/blog/my-post.md`:

```md
---
title: 'My Post Title'
description: 'One sentence describing the post.'
pubDate: 2026-09-15
---

Post content goes here, written in Markdown.
```

Push to `main` and the site rebuilds and deploys automatically (see [Deployment](#deployment)).

## Commands

Run from the project root:

| Command             | Action                                      |
| :------------------- | :------------------------------------------ |
| `npm install`         | Install dependencies                        |
| `npm run dev`         | Start local dev server at `localhost:4321`  |
| `npm run build`       | Build the production site to `./dist/`      |
| `npm run preview`     | Preview the production build locally        |

## Deployment

This repo deploys to GitHub Pages via the workflow in [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml), which runs automatically on every push to `main`.

One-time setup after pushing this repo to GitHub:

1. In the repo, go to **Settings → Pages**, and under "Build and deployment" set **Source** to **GitHub Actions**.
2. Still under **Settings → Pages**, add `artificialamateur.com` as the custom domain (the `public/CNAME` file already contains it, so this should be pre-filled) and enable **Enforce HTTPS** once it's available.
3. At your domain registrar, point DNS at GitHub Pages:
   - Add an `A` record for the root domain (`@`) to each of: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Or, if you want `www.artificialamateur.com` to work too, add a `CNAME` record for `www` pointing to `<your-github-username>.github.io`
4. DNS propagation can take anywhere from a few minutes to a few hours.

## Project structure

```text
├── public/              # static assets (favicon, CNAME)
├── src/
│   ├── content/blog/    # blog posts (Markdown)
│   ├── pages/            # routes (index, blog, about, rss)
│   ├── components/
│   └── layouts/
├── astro.config.mjs
└── .github/workflows/deploy.yml
```

Built on the official [Astro blog starter template](https://github.com/withastro/astro/tree/main/examples/blog).
