# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is an academic personal website built with **Jekyll** using the **al-folio** theme. The site is hosted on GitHub Pages and showcases publications, projects, CV, news, and blog posts.

## Development Commands

### Local Development

**Standard Setup (with Ruby/Bundler installed):**
```bash
bundle install
bundle exec jekyll serve --lsi
```
The site will be available at `http://localhost:4000`

**Docker Setup (recommended on Windows):**
```bash
docker-compose up
```
The site will be available at `http://localhost:8080`

**Custom Docker Build:**
```bash
docker-compose -f docker-local.yml up
```

### Building for Production

```bash
export JEKYLL_ENV=production
bundle exec jekyll build
```
The built site will be in the `_site/` directory.

**Alternative build (for non-GitHub Pages hosting):**
```bash
bundle exec jekyll build --lsi
```

## Architecture

### Content Structure

- **`_config.yml`**: Main configuration file containing site settings, social links, theme options, and plugin configurations
- **`_pages/`**: Static pages (about, CV, publications, teaching)
- **`_posts/`**: Blog posts in Markdown with front matter
- **`_projects/`**: Project descriptions and showcases
- **`_news/`**: News/announcements displayed on the homepage
- **`_bibliography/`**: BibTeX files for publications (main file: `papers.bib`)

### Theme Components

- **`_layouts/`**: HTML layout templates (about, post, page, distill, archive, cv, etc.)
- **`_includes/`**: Reusable HTML components (header, footer, navigation, social links, etc.)
- **`_sass/`**: SCSS stylesheets for theming
- **`assets/`**: Static assets organized by type:
  - `css/`, `js/`: Compiled styles and scripts
  - `img/`: Images
  - `pdf/`: PDF files (papers, CV, etc.)
  - `bibliography/`: Bibliography-related files

### Custom Plugins

Located in `_plugins/`:
- `details.rb`: Custom details/summary functionality
- `external-posts.rb`: Fetches external blog posts
- `hideCustomBibtex.rb`: Filters BibTeX fields

### Jekyll Collections

Configured in `_config.yml`:
- **news**: Announcements/updates (displayed on homepage)
- **projects**: Project portfolio (displayed on projects page)

## Key Configuration

### Site Personalization

Edit `_config.yml` to update:
- Personal information (name, email, bio)
- `url` and `baseurl` for deployment
- Social media links (GitHub, LinkedIn, Twitter, Scholar, etc.)
- Scholar configuration for publication author highlighting

### Publications

Publications are auto-generated from `_bibliography/papers.bib`. Custom BibTeX keywords available:
- `abbr`: Conference/journal abbreviation
- `pdf`, `code`, `slides`, `poster`: Links to resources
- `abstract`: Expandable abstract text
- `bibtex_show`: Show BibTeX entry

Co-author information goes in `_data/coauthors.yml`.

### Theme Customization

- Colors: Edit `_sass/_themes.scss` (change `--global-theme-color`)
- Dark mode: Enabled by default (`enable_darkmode: true`)
- Layout options: `_config.yml` (navbar, footer, max width)

## Deployment

### GitHub Pages (Automatic)

The site auto-deploys via GitHub Actions (`.github/workflows/deploy.yml`) on pushes to `master` or `main` branch.

**Prerequisites:**
1. Repository name must be `<username>.github.io` for user pages
2. GitHub Actions enabled in repository settings
3. Workflow permissions set to "Read and write"
4. GitHub Pages source set to `gh-pages` branch

### Manual Deployment

Trigger manually via Actions → Deploy → Run workflow

## Important Notes

- **LSI (Latent Semantic Indexing)**: The `--lsi` flag enables related posts feature using the `classifier-reborn` gem. May fail on minimal blog posts with only stop words.
- **Related Posts**: Configured in `_config.yml` under `related_blog_posts`. Can be disabled per-post with `related_posts: false` in front matter.
- **Jekyll Environment**: Use `JEKYLL_ENV=production` for production builds to enable optimizations and analytics.
- **Docker Port**: Default is 8080 for Docker setup. Edit `docker-compose.yml` to change.
- **Pre-commit Hooks**: `.pre-commit-config.yaml` is configured for the project.

## Content Guidelines

- Blog posts use kramdown Markdown with GFM (GitHub Flavored Markdown) input
- Posts support math (MathJax), code highlighting, Distill.pub styling, diagrams (jekyll-diagrams), and embedded media
- Images should be placed in `assets/img/`
- PDFs (papers, posters, etc.) go in `assets/pdf/`
