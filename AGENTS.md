# Agent Guide — HugoBlox Academic CV Site

> This file helps AI coding agents understand, navigate, and modify this project safely and effectively.

---

## Project Overview

This is a **HugoBlox Academic CV** starter template — a static site built with [Hugo](https://gohugo.io/) and the [HugoBlox](https://hugoblox.com/) framework. It produces a personal academic/portfolio website (bio, publications, projects, talks, courses, blog) from plain Markdown and YAML files.

- **Repository purpose**: Personal academic website
- **Primary audience**: Researchers, academics, PhD students
- **License**: MIT
- **Content language**: English (with optional multi-language support)

---

## Technology Stack

| Component | Version / Tool | Purpose |
|-----------|----------------|---------|
| **Static Site Generator** | Hugo Extended 0.161.1 | Builds the site from Markdown/YAML |
| **Framework** | HugoBlox Kit (Go modules) | Academic theme, blocks, and integrations |
| **CSS Framework** | Tailwind CSS 4.x | Utility-first styling |
| **CSS Build Tool** | `@tailwindcss/cli` | Tailwind CLI for Hugo asset pipeline |
| **Package Manager** | pnpm 10.14.0 | Node.js dependency management |
| **Search** | Pagefind 1.4.x | Static search index generation |
| **Runtime** | Node.js 22 | Required for Tailwind and Pagefind |
| **Go** | 1.19+ (CI uses 1.21–1.23) | Hugo module resolution |
| **Hosting** | GitHub Pages (default) | Static site deployment |

### Hugo Modules (Go)

The site imports HugoBlox modules via `go.mod`:

- `github.com/HugoBlox/kit/modules/blox` — Core blocks and theme
- `github.com/HugoBlox/kit/modules/integrations/netlify` — Netlify integrations (headers, redirects)
- `github.com/HugoBlox/kit/modules/slides` — Markdown-based slide decks (reveal.js)

---

## Project Structure

```
.
├── config/_default/          # Hugo configuration
│   ├── hugo.yaml             # Core Hugo settings (baseURL, outputs, imaging, taxonomies)
│   ├── params.yaml           # HugoBlox parameters (identity, theme, layout, SEO, analytics)
│   ├── menus.yaml            # Navigation menu items
│   ├── languages.yaml        # Language/i18n configuration
│   └── module.yaml           # Hugo module imports and mount points
├── content/                  # All site content (Markdown + YAML front matter)
│   ├── _index.md             # Homepage — a landing page composed of "blocks"
│   ├── authors/              # Author profiles (rendered as pages when enabled)
│   ├── blog/                 # Blog posts
│   ├── publications/         # Academic papers (with BibTeX, DOI linking)
│   ├── projects/             # Project showcase pages
│   ├── events/               # Talks, workshops, conferences
│   ├── courses/              # Course documentation (docs layout)
│   ├── slides/               # Markdown-based slide decks
│   └── experience.md         # Experience/resume landing page
├── data/
│   └── authors/
│       └── me.yaml           # Author metadata (bio, education, skills, social links)
├── layouts/
│   └── _partials/            # Custom layout overrides (e.g., HTML hooks)
├── assets/
│   └── media/                # Site media assets processed by Hugo pipeline
├── static/
│   └── uploads/              # Static files served as-is (e.g., PDFs)
├── .github/workflows/         # CI/CD automation
├── hugoblox.yaml             # HugoBlox project metadata (template ID, deploy target, Hugo version)
├── go.mod                    # Go module dependencies
├── package.json              # Node.js dependencies and scripts
├── netlify.toml              # Netlify build configuration (alternative host)
└── pnpm-lock.yaml            # pnpm lockfile
```

### Content Types & Conventions

All content lives in `content/` as Markdown files with **YAML front matter**.

| Content Type | Location | Key Front-Matter Fields |
|--------------|----------|------------------------|
| **Homepage** | `content/_index.md` | `type: landing`, `sections:` (array of blocks) |
| **Author** | `data/authors/me.yaml` | `schema: hugoblox/author/v1`, name, bio, affiliations, links |
| **Blog Post** | `content/blog/<slug>/index.md` | `title`, `date`, `authors`, `tags`, `image` |
| **Publication** | `content/publications/<slug>/index.md` | `authors`, `publication_types`, `abstract`, `doi`, `featured` |
| **Project** | `content/projects/<slug>/index.md` | `title`, `date`, `links`, `tags` |
| **Event/Talk** | `content/events/<slug>/index.md` | `event_name`, `event_start`, `location`, `slides` |
| **Course** | `content/courses/<course>/<page>.md` | `type: docs`, `linkTitle` |
| **Slides** | `content/slides/<slug>/index.md` | `type: slides`, `slides.theme` |

**Images**: Place `featured.jpg` or `featured.png` inside the content folder alongside `index.md` to associate a thumbnail.

**BibTeX**: Publications can include a `cite.bib` file in the same folder for citation metadata. A `publications.bib` at repo root triggers an automated import workflow.

---

## Build & Development Commands

### Prerequisites

- Hugo Extended 0.161.1+ ([install guide](https://gohugo.io/installation/))
- Node.js 22+
- pnpm 10.14.0+ (or use `corepack`)
- Go 1.19+ (for Hugo modules)

### Local Development

```bash
# Install Node dependencies
pnpm install

# Start development server with live reload
pnpm run dev
# Equivalent to: hugo server --disableFastRender
# Site will be available at http://localhost:1313
```

### Production Build

```bash
# Full build: compile site + generate search index
pnpm run build
# Equivalent to:
#   hugo --minify
#   pagefind --site public
```

### Hugo Commands (Direct)

```bash
# Development server
hugo server --disableFastRender

# Production build
hugo --minify

# Build with baseURL override
hugo --minify --baseURL "https://example.com/"

# Clean build cache
hugo --gc --minify
```

### Pagefind Search Index

```bash
# Generate search index after a Hugo build
pnpm run pagefind
# Equivalent to: pagefind --site public
```

---

## Configuration Reference

### `hugoblox.yaml`

Project-level metadata for HugoBlox tooling:

- `build.hugo_version`: Pin the Hugo version (`0.161.1`)
- `deploy.host`: Deployment target — `github-pages` (default), `netlify`, `vercel`, `cloudflare`, or `none`
- `template.id`: `academic-cv`

### `config/_default/params.yaml`

Primary site customization file. Key sections:

- `hugoblox.identity.*` — Site name, tagline, description, social accounts
- `hugoblox.theme.*` — Light/dark mode, color pack, custom colors
- `hugoblox.header.*` — Navbar style, search, theme toggle, CTA
- `hugoblox.footer.*` — Footer style
- `hugoblox.seo.*` — Title overrides, AI crawler guidance (`llms.txt`)
- `hugoblox.content.*` — Math rendering, TOC, reading time, citation style
- `hugoblox.analytics.*` — Google Analytics, Plausible, Fathom, etc.
- `hugoblox.search.*` — Enable/disable site search
- `hugoblox.comments.*` — Giscus / Disqus

### `config/_default/hugo.yaml`

Core Hugo settings:

- `baseURL`: Set to your production domain
- `defaultContentLanguage`: `en`
- `taxonomies`: `authors`, `tags`, `publication_types`
- `outputs.home`: `HTML`, `RSS`, `headers`, `redirects`, `backlinks`
- `imaging.quality`: `90`
- `ignoreFiles`: Jupyter checkpoints, R Markdown cache

---

## Content Authoring Patterns

### Homepage Blocks

The homepage (`content/_index.md`) is a **landing page** composed of reusable blocks under `sections:`:

```yaml
sections:
  - block: resume-biography-3
    content:
      username: me   # References data/authors/me.yaml
    design:
      background:
        gradient_mesh:
          enable: true
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders: [publications]
        featured_only: true
    design:
      view: article-grid
      columns: 2
```

Common blocks: `resume-biography-3`, `collection`, `markdown`, `cta-card`, `resume-experience`, `resume-skills`, `resume-awards`, `resume-languages`.

### Author Profile

Author data is stored in `data/authors/<username>.yaml` with schema `hugoblox/author/v1`:

```yaml
schema: hugoblox/author/v1
slug: me
is_owner: true
name:
  display: Dr. Alex Johnson
  given: Alex
  family: Johnson
role: Senior AI Research Scientist
bio: |
  Research scientist at ...
affiliations:
  - name: Meta AI
    url: https://ai.meta.com/
links:
  - icon: brands/github
    url: https://github.com/example
education:
  - degree: PhD Computer Science
    institution: Stanford University
    start: 2015-09-01
    end: 2019-06-30
```

To publish author profile pages, remove the `build.render: never` settings from `content/authors/_index.md`.

### Publications

Each publication is a folder in `content/publications/<slug>/` containing:

- `index.md` — Publication metadata
- `featured.jpg` (optional) — Thumbnail
- `cite.bib` (optional) — BibTeX citation data
- `<filename>.pdf` (optional) — PDF download

Front matter supports: `authors`, `publication_types` (CSL standard), `abstract`, `doi`, `featured`, `links` (pdf, code, dataset, slides, video).

### Shortcodes

HugoBlox provides rich shortcodes for content:

- `{{< toc >}}` — Table of contents
- `{{< button url="..." text="..." >}}` — Styled buttons
- `{{< cards >}}` / `{{< card >}}` — Card grids
- `{{< icon name="..." >}}` — Icons
- `{{< figure src="..." >}}` — Figures

---

## CI/CD & Deployment

All automation is in `.github/workflows/`.

### `deploy.yml`

- **Trigger**: Push to `main`, or manual dispatch
- **Jobs**:
  1. `config` — Reads `hugoblox.yaml` to determine deploy host
  2. `build` — Reuses `build.yml` to compile the site
  3. `deploy` — Deploys to GitHub Pages (only if `deploy.host == 'github-pages'`)

### `build.yml`

- **Trigger**: Pull requests to `main`, reusable workflow call, manual dispatch
- **Steps**: Checkout → Setup Node/pnpm → Setup Hugo → Install deps → Build (`hugo --minify`) → Pagefind index → Upload artifact
- **Caching**: Go modules, `node_modules/`, and Hugo `resources/` are cached

### `upgrade.yml`

- **Trigger**: Weekly schedule (Monday 05:00) or manual dispatch
- **Action**: Runs `hugoblox upgrade` to update Go modules, then creates a pull request
- Skipped if repo owner is `HugoBlox`

### `import-publications.yml`

- **Trigger**: Push to `main` when `publications.bib` changes, or manual dispatch
- **Action**: Uses the Python `academic` CLI to convert `publications.bib` into `content/publications/`, then opens a pull request

### `internal-readme-news.yml`

- **Trigger**: Weekly schedule
- **Action**: Updates README news section from HugoBlox RSS feed
- Only runs on the `HugoBlox` organization repository; safe to delete for end users

### Netlify (Alternative Host)

`netlify.toml` provides a complete build configuration with verbose logging, Hugo/Pagefind build steps, and deploy-preview/branch-deploy contexts.

---

## Code Style Guidelines

- **Front matter**: Use YAML (not TOML) for all content metadata
- **Indentation**: 2 spaces in YAML and Markdown
- **File naming**: Use kebab-case for directories (`conference-paper/`, `data-visualization/`)
- **Images**: Prefer `featured.jpg` or `featured.png` placed next to `index.md`
- **Markdown**: Standard CommonMark + HugoBlox extensions (callouts, buttons, icons)
- **Callouts**: Use GitHub/Obsidian-style alert syntax:
  ```markdown
  > [!NOTE]
  > Important information here.
  ```
- **Dates**: Use ISO 8601 (`2023-10-24`) or RFC 3339 for datetimes
- **Comments**: Use YAML comments `#` in config; use HTML comments `<!-- -->` in Markdown

---

## Testing & Validation

There is **no automated test suite** in this repository. Validation is performed via:

1. **Local build**: Run `hugo --minify` locally and check for warnings/errors
2. **CI build**: The `build.yml` workflow validates every pull request
3. **Visual inspection**: Use `pnpm run dev` and review at `http://localhost:1313`
4. **Pagefind index**: After build, verify `public/pagefind/` exists

Common issues to watch for:
- Missing `@tailwindcss/cli` dependency (Hugo >= 0.161.0 requires it)
- Hugo module resolution failures (run `hugo mod get` and `hugo mod tidy`)
- Invalid YAML front matter (use a YAML linter)

---

## Security Considerations

- **No secrets in repo**: Do not commit API keys, tokens, or passwords
- **Analytics**: Configure analytics IDs in `params.yaml` (Google Analytics, Plausible, etc.)
- **Comments**: Giscus requires a public GitHub repo; Disqus requires a shortname
- **CSP / Security headers**: Configurable in `params.yaml` under `hugoblox.security` (requires Netlify integration for header injection)
- **Frame options**: Default is `allow` (enables iframe embedding); set to `sameorigin` or `deny` as needed
- **GitHub Actions**: Workflows use least-privilege permissions (`contents: read`, `pages: write`)

---

## Agent Quick Reference

| Task | How |
|------|-----|
| Add a new blog post | Create `content/blog/<slug>/index.md` with front matter |
| Add a publication | Create `content/publications/<slug>/index.md` + optional `cite.bib` and `featured.jpg` |
| Update author bio | Edit `data/authors/me.yaml` |
| Change site colors | Edit `config/_default/params.yaml` → `hugoblox.theme.colors` |
| Add navigation link | Edit `config/_default/menus.yaml` → `main:` |
| Add analytics | Edit `config/_default/params.yaml` → `hugoblox.analytics` |
| Customize homepage | Edit `content/_index.md` → `sections:` blocks |
| Override a partial | Create file in `layouts/_partials/` matching HugoBlox partial path |
| Update Hugo version | Edit `hugoblox.yaml` → `build.hugo_version` and `.github/workflows/build.yml` |
| Change deploy target | Edit `hugoblox.yaml` → `deploy.host` |

---

## Useful Links

- [HugoBlox Documentation](https://docs.hugoblox.com/)
- [Hugo Documentation](https://gohugo.io/documentation/)
- [HugoBlox Kit Repository](https://github.com/HugoBlox/kit)
- [Academic File Converter (BibTeX)](https://github.com/GetRD/academic-file-converter)
- [Discord Community](https://discord.gg/z8wNYzb)
