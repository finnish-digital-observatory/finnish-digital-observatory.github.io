# Finnish Digital Observatory

Website for the Finnish Digital Observatory research infrastructure, built with Jekyll and Bootstrap 5. Deployed automatically to GitHub Pages.

**Live site:** https://finnish-digital-observatory.github.io

## Structure

```
_config.yml              # Site settings and plugins
_layouts/
  default.html           # Base layout — navbar auto-built from content/ folder structure
_includes/
  download.html          # Reusable download button
_data/
  people.yml             # People list, rendered on the About page
content/                 # All pages live here — folder structure drives the navbar
  index.md               # Home page
  about.md               # About page
  projects/
    index.md             # Projects section landing page
    data-donation.md     # Sub-page under Projects
  code/
    index.md             # Code section landing page
    finnish-online-forums.md
```

## Local development

**Requirements:** Ruby 3.x, Bundler

```bash
bundle install
bundle exec jekyll serve
```

The site will be available at http://localhost:4000.

## Deployment

Pushing to `main` triggers the GitHub Actions workflow (`.github/workflows/deploy.yml`), which builds the site and deploys it to GitHub Pages.

Make sure GitHub Pages is configured to use **GitHub Actions** as the source: Settings → Pages → Source → GitHub Actions.

## How the navbar works

The navbar is built automatically from the `content/` folder — no configuration needed.

- **Files directly in `content/`** (e.g. `content/about.md`) become top-level nav items.
- **Subfolders** (e.g. `content/projects/`) become dropdown menus. The folder's `index.md` title and URL are used for the dropdown toggle; all other `.md` files in the folder become dropdown items.

Items are sorted alphabetically by title. If you want a custom order, add `nav_order: 1` (etc.) to a page's front matter — ordered pages appear first, unordered pages follow alphabetically.

## Adding a top-level page

Create a file directly in `content/`:

```yaml
---
layout: default
title: My Page
permalink: /my-page/
---
```

It will appear in the navbar automatically.

## Adding a section with sub-pages

Create a subfolder and an index page for it:

```
content/
  my-section/
    index.md          ← section landing page, used as the dropdown toggle
    my-sub-page.md    ← appears in the dropdown
```

Minimum front matter for each file:

```yaml
---
layout: default
title: Page Title
permalink: /my-section/          # for index.md
---
```

```yaml
---
layout: default
title: Sub-page Title
permalink: /my-section/my-sub-page/
---
```

## Adding downloadable files

Place PDFs, datasets, or other files alongside the relevant page in `content/`:

```
content/projects/data-donation/report.pdf
```

They are served at `/content/projects/data-donation/report.pdf`.

Link inline:

```markdown
[Download report](/content/projects/data-donation/report.pdf)
```

Or use the download button include:

```liquid
{% include download.html file="/content/projects/data-donation/report.pdf" label="Download Report" %}
```

## Managing people (About page)

Edit `_data/people.yml`. Each entry supports:

```yaml
- name: Firstname Lastname
  affiliation: University Name
  picture: https://example.com/photo.jpg
  profile: https://example.com/profile
```

The About page renders all entries as a grid of circular avatars automatically.
