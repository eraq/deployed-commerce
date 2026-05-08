# Deployed Commerce

A technical blog about commerce infrastructure, self-hosting, and developer tools.
Live at [deployedcommerce.com](https://deployedcommerce.com).

This repo is intentionally transparent — the site itself is a working example of the
stack described in its posts. Everything here is public and reproducible.

---

## Stack

| Layer | Tool |
|---|---|
| Static site generator | [Hugo](https://gohugo.io/) 0.147.1 extended |
| Theme | [PaperMod](https://github.com/adityatelange/hugo-PaperMod) via git submodule |
| Hosting | [Cloudflare Pages](https://pages.cloudflare.com/) |
| DNS / SSL | Cloudflare (auto-provisioned) |
| Domain | deployedcommerce.com (registered with Cloudflare) |
| Source | This repo — every commit to `main` autodeploys |

---

## How It Works

Cloudflare Pages watches this repo. Every commit to `main` triggers a build:

```bash
hugo --gc --minify
```

The `public/` output directory is served globally via Cloudflare's CDN. Build time
is typically under 30 seconds. SSL is automatic.

The theme (PaperMod) is a git submodule — it is not vendored into this repo directly.
Cloudflare Pages fetches it at build time via `git submodule update --init --recursive`.

---

## Repository Structure
deployed-commerce/
├── content/
│   ├── posts/          # Blog posts — one .md file per post
│   └── about.md        # About page
├── themes/
│   └── PaperMod/       # Theme submodule (do not edit directly)
├── layouts/            # Local overrides — copy theme files here to customize
├── static/             # Static assets (images, favicon, etc.)
├── archetypes/         # Post templates
├── hugo.toml           # Site configuration
└── .gitignore

To override any theme component without modifying the submodule, copy the relevant
file from `themes/PaperMod/layouts/` into the matching path under `layouts/` and
edit your copy. Hugo uses local layouts first.

---

## Adding Content

The primary authoring workflow is via the GitHub web UI — no local tooling required.

1. Navigate to `content/posts/` in this repo on GitHub
2. Click **Add file → Create new file**
3. Name the file `your-post-slug.md`
4. Use this frontmatter:

```markdown
---
title: "Your Post Title"
date: YYYY-MM-DD
draft: false
tags: ["tag1", "tag2"]
description: "One sentence summary shown in post listings."
---

Your content here. Standard Markdown.
```

5. Commit directly to `main` — the site redeploys automatically

---

## Local Development

Local tooling is only needed for structural or theme changes, not for writing posts.

**Requirements:**
- A Linux host (this project uses a Proxmox VM accessed via VS Code SSH)
- Hugo 0.147.1 extended (see [Hugo Updates](#hugo-updates) below)

**Local preview:**

```bash
git clone --recurse-submodules https://github.com/eraq/deployed-commerce.git
cd deployed-commerce
hugo server -D --bind 0.0.0.0 --port 1313
```

The `--bind 0.0.0.0` flag is required when running inside a VM with VS Code port
forwarding. Forward port `1313` in VS Code and open `http://localhost:1313` in your
local browser.

---

## Hugo Updates

Hugo is installed manually from the official GitHub releases (extended edition).
It is **not** managed by apt — do not run `sudo apt install hugo`.

**Check current version:**

```bash
hugo version
which hugo   # should be /usr/local/bin/hugo
```

**Upgrade Hugo:**

Replace `X.Y.Z` with the target version from
[Hugo releases](https://github.com/gohugoio/hugo/releases):

```bash
HUGO_VERSION=X.Y.Z
wget https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz
tar -xzf hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz
sudo mv hugo /usr/local/bin/hugo
rm hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz
hugo version
```

Also update the `HUGO_VERSION` environment variable in your Cloudflare Pages build
settings to match.

**Update PaperMod theme:**

```bash
git submodule update --remote themes/PaperMod
git add themes/PaperMod
git commit -m "Update PaperMod theme"
git push
```

Check [PaperMod's README](https://github.com/adityatelange/hugo-PaperMod) after
updating — the minimum Hugo version requirement may have increased.

---

## Cloudflare Pages Build Settings

| Setting | Value |
|---|---|
| Build command | `hugo --gc --minify` |
| Output directory | `public` |
| `HUGO_VERSION` | `0.147.1` |
| `HUGO_ENVIRONMENT` | `production` |

These are set in the Cloudflare Pages dashboard under **Settings → Environment variables**.