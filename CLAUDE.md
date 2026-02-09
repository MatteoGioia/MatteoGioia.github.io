# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Personal academic website for Matteo Gioia (PhD student in Data Science). Built with Jekyll using the [al-folio](https://github.com/alshedivat/al-folio) theme (v0.14.6). Hosted on GitHub Pages.

## Build & Preview Commands

```bash
# First-time setup (macOS — needs Homebrew ruby)
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
bundle install

# Local preview (serves at localhost:4000)
bundle exec jekyll serve

# Build only (no server)
bundle exec jekyll build
```

## Architecture

The site uses the al-folio theme committed directly (not as a gem or remote theme). All theme files (`_layouts`, `_sass`, `_includes`, `_plugins`, `assets/`) are in the repo and can be edited in-place.

### Key directories
- `_pages/` — site pages (about, blog, publications, projects, cv, 404)
- `_posts/` — blog posts (Markdown with YAML front matter)
- `_bibliography/papers.bib` — BibTeX publications (rendered by jekyll-scholar)
- `_news/` — announcement items shown on the homepage
- `_projects/` — project cards shown on the projects page
- `_data/` — YAML data files (socials, cv, coauthors, repositories)
- `assets/img/` — images including `prof_pic.jpg` (profile photo) and `publication_preview/`
- `assets/json/resume.json` — JSON Resume data for the CV page

### Layout chain
- `_layouts/about.liquid` — homepage layout (profile image, bio, news, selected papers, latest posts)
- `_layouts/page.liquid` — generic page layout
- `_layouts/post.liquid` — blog post layout
- `_layouts/bib.liquid` — individual bibliography entry template
- `_layouts/cv.liquid` — CV page layout (reads from `_data/cv.yml` and `assets/json/resume.json`)

### Styling
- `assets/css/main.scss` — entry point; imports from `_sass/` (variables, themes, layout, base, distill)
- `_sass/` — theme SCSS partials

### Key config (`_config.yml`)
- `first_name: Matteo`, `last_name: Gioia`
- `url: https://matteogioia.github.io`
- Scholar config highlights `Gioia` surname in publication lists
- `imagemagick.enabled: false` — set to true if ImageMagick is installed for responsive images
- Blog, publications, projects, and CV pages are enabled via nav items in their front matter

## Conventions

- Pages use `nav: true` and `nav_order: N` in front matter to appear in the navbar
- Publications are managed via `_bibliography/papers.bib` — use `selected={true}` for homepage display
- News items in `_news/` use `inline: true` for short announcements
- Profile image should be named `prof_pic.jpg` in `assets/img/`
- Publication preview images go in `assets/img/publication_preview/`
- Social links are configured in `_data/socials.yml`
