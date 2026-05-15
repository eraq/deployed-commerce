---
title: "Colophon"
date: 2026-05-09
draft: false
---

This site is built with [Hugo](https://gohugo.io/) and hosted on [Cloudflare Pages](https://pages.cloudflare.com/). Every commit to the `main` branch on GitHub triggers an automatic build and deploy, typically live within 30 seconds.

## Stack

| Layer | Tool |
|---|---|
| Static site generator | Hugo 0.157.0 (extended) |
| Theme | [Stack](https://github.com/CaiJimmy/hugo-theme-stack), via git submodule |
| Hosting | Cloudflare Pages |
| DNS & SSL | Cloudflare (auto-provisioned) |
| Source | [GitHub](https://github.com/eraq/deployed-commerce), public and reproducible |

## Philosophy

The stack here is deliberately minimal. No database, no server-side runtime, no CMS dashboard to maintain. Content lives as Markdown files in a git repository, versioned, portable, and straightforward to reason about.

Cloudflare's global CDN handles delivery. SSL is automatic. The entire build pipeline is a single command:

```bash
hugo --gc --minify
```

The source repository is intentionally public. The site is a working example of the infrastructure it writes about.

## Authoring

Posts are written in Markdown, authored locally in an IDE, and merged to `main` via pull request. One `.md` file per post under `content/posts/`, no proprietary formats, no lock-in.

## Theme

The theme is [Stack](https://github.com/CaiJimmy/hugo-theme-stack) by Jimmy Cai, included as a git submodule. Local overrides live in the `layouts/` directory and take precedence over the theme without modifying the submodule directly.
