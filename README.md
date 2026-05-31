# Finnish Digital Observatory

Website for the Finnish Digital Observatory research infrastructure, built with Jekyll and Bootstrap 5. Deployed automatically to GitHub Pages.

**Live site:** https://finnish-digital-observatory.github.io

## Structure

```
_config.yml           # Site settings and navigation
_layouts/
  default.html        # Base layout with Bootstrap navbar
index.md              # Home page
about.md              # About page
projects/
  index.md            # Projects overview
  data-donation.md    # Data Donation project
code/
  index.md            # Code overview
  finnish-online-forums.md  # Finnish Online Forums
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

Make sure GitHub Pages is configured to use **GitHub Actions** as the source under Settings → Pages.

## Adding pages

1. Create a new `.md` file in the relevant directory
2. Add front matter:
   ```yaml
   ---
   layout: default
   title: Your Page Title
   ---
   ```
3. To add it to the navbar, update `_config.yml` under `nav:` and edit the navbar in `_layouts/default.html`
