# Blog

Quarto blog; posts are Jupyter notebooks.

## Prerequisites

- Quarto CLI 1.10.18
- Python 3 with `jupyter` and `ipykernel`, for Python posts
- Deno 2 with its Jupyter kernel (`deno jupyter --install`), for Deno posts

Preview locally:

```
quarto preview
```

## Adding a post

Put the notebook at `posts/<slug>/<slug>.ipynb`. Its first cell is a raw cell
holding the front matter:

```
---
title: "Post title"
date: "YYYY-MM-DD"
---
```

Run the notebook before committing: Quarto renders the outputs stored in the
`.ipynb` rather than executing cells, so CI needs no kernels. The project sets
`execute: freeze: auto`; if a render writes `_freeze/`, commit it too.

## Deploying

Pushing to `main` runs `.github/workflows/publish.yml`, which renders the site
and pushes it to the `gh-pages` branch.

## Manual setup

After the first successful run, enable Pages for the repository: Settings →
Pages → source "Deploy from a branch", branch `gh-pages`, folder `/`.
