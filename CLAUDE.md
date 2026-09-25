# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build & Dev Commands

- `npm start` — local dev server with live reload (drafts included)
- `npm run build` — production build to `_site/`
- `npm run debug` — build with Eleventy debug logging
- `npm run debugstart` — dev server with debug logging

Node version: 16 (see `.nvmrc`).

## Architecture

This is an [Eleventy (11ty) v2](https://www.11ty.dev/) static site — a personal portfolio/blog for a mobile and game developer. It deploys to GitHub Pages via a CI workflow that builds and pushes to `gh-pages`.

### Content Structure

All content lives in `content/` with three collections, each defined by a `*.11tydata.js` file that sets the tag and layout:

- `content/blog/` — blog posts, tagged `posts`
- `content/games/` — game portfolio entries, tagged `games`
- `content/works/` — app/work portfolio entries, tagged `works`

All collections use `layouts/post.njk` layout. Top-level pages (`index.md`, `about/`, `blog.njk`, `games.njk`, `works.njk`, `tags.njk`) use `layouts/home.njk` or `layouts/base.njk`.

### Post Frontmatter

Posts use YAML frontmatter with `title`, `date`, `description` (optional), `tags`, and `draft: true` for drafts. Drafts are only included during `serve`/`watch` mode, never in production builds (handled by `eleventy.config.drafts.js`).

### Key Config Files

- `eleventy.config.js` — main config: plugins, filters, markdown-it-anchor setup, passthrough copy, directory mappings
- `eleventy.config.images.js` — `{% image %}` shortcode (avif/webp/auto, lazy loading) and `{% video %}` shortcode (loads from external assets URL in `_data/metadata.js`)
- `eleventy.config.drafts.js` — draft post filtering logic
- `_data/metadata.js` — site metadata (title, URL, author, external assets base URL)

### Templates

Templates use Nunjucks (`.njk`). Markdown files are pre-processed with Nunjucks (`markdownTemplateEngine: "njk"`). Layouts are in `_includes/layouts/`, partials in `_includes/`.

### Static Assets

`public/` contents are copied to site root (CSS, images, CNAME, favicon). Prism.js theme CSS is copied from `node_modules`.

### Media Embedding

The `eleventy-plugin-embed-everything` plugin auto-embeds YouTube links (and other media) placed directly in markdown content — no shortcode needed.

## Deployment

- **GitHub Pages**: CI workflow (`.github/workflows/eleventy_build.yml`) builds on push/PR to `main` and deploys `_site/` to `gh-pages` branch
- **Netlify**: configured via `netlify.toml` with Lighthouse performance thresholds (all set to 1.0)
