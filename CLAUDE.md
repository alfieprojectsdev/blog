# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal blog built with Astro 5, deployed to `blog.ithinkandicode.space`. Uses the Astro Blog starter template with MDX support, RSS feed, and sitemap generation.

## Commands

```bash
npm run dev      # Start dev server at localhost:4321
npm run build    # Build production site to ./dist/
npm run preview  # Preview production build locally
```

## Architecture

**Content Collections**: Blog posts live in `src/content/blog/` as `.md` or `.mdx` files. The schema is defined in `src/content.config.ts` with required `title`, `description`, `pubDate` fields and optional `updatedDate`, `heroImage`.

**Pages**:
- `src/pages/index.astro` - Homepage
- `src/pages/about.astro` - About page
- `src/pages/blog/index.astro` - Blog listing
- `src/pages/blog/[...slug].astro` - Individual blog posts
- `src/pages/rss.xml.js` - RSS feed

**Layouts**: `src/layouts/BlogPost.astro` wraps blog post content.

**Global Constants**: Site title and description in `src/consts.ts`.

**Integrations**: MDX (`@astrojs/mdx`) and Sitemap (`@astrojs/sitemap`) are configured in `astro.config.mjs`.
