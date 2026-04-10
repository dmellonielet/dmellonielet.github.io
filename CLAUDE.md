# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build & Development Commands

```bash
# Install dependencies
bundle install

# Local development server
bundle exec jekyll serve

# Production build (outputs to public/)
bundle exec jekyll build
```

## Architecture Overview

This is a personal blog/portfolio site for Nielet D'mello (Security Engineer) built with **Jekyll 3.6+** and the **Minima ~2.5 theme**, hosted on GitHub Pages at dmellonielet.com.

**Key configuration:**
- `_config.yml` — site title "Kaleidoscope", custom output to `public/` (not the default `_site/`), 25 posts per page pagination
- `Gemfile` — pure Ruby/Jekyll project; no Node.js. Plugins: jekyll-feed, jekyll-paginate, jekyll-seo-tag, jekyll-sitemap, jemoji
- `CNAME` — custom domain: dmellonielet.com

**Content:**
- `_posts/` — Markdown blog posts with YAML front matter (tags supported)
- `about.md` — Author bio page
- `posts/index.html` — Paginated post listing
- `images/` — Post images and favicon assets

**Custom includes:**
- `_includes/custom-head.html` — Favicon and PWA manifest (`site.webmanifest`) declarations
- `_includes/read_time.html` — Calculates estimated read time (words ÷ 135, minimum 1 min)

**New post front matter format:**
```yaml
---
layout: post
title: "Post Title"
date: YYYY-MM-DD
tags: [tag1, tag2]
---
```

**CI:** Travis CI runs `bundle exec jekyll build` on commits to master; `public/` is cleaned before each build.
