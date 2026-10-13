# Molecular Biology Notebook

A Jekyll site with three sections, built to run on GitHub Pages with no extra setup:

- **About**: introduction, research interests and a research timeline.
- **Weekly reflections**: grouped by lab in collapsible dropdowns, each lab with its own description.
- **Blog**: separate, for longer essays and open questions.

## Publish it (about 10 minutes)

1. Create a **public** GitHub repository named `YOUR-USERNAME.github.io`.
2. Upload everything in this folder (drag and drop in the web interface works).
3. In the repo go to **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
4. In `_config.yml` set `url: "https://YOUR-USERNAME.github.io"`. If your repo is named something else, also set `baseurl: "/repo-name"`.

## Where things live

| You want to change... | Edit this |
|---|---|
| Site title, tagline, your name, footer links | `_config.yml` |
| Order of entries (newest or oldest first) | `reflection_order` in `_config.yml` |
| The About text and research interests | `about.md` |
| The research timeline | `_data/timeline.yml` |
| Labs and their descriptions | `_data/labs.yml` |
| Menu items and the cards on the home page | `_data/nav.yml` |
| Colours, fonts, page width | `assets/css/tokens.css` |
| Look of a specific component | `assets/css/components.css` |
| Overall page frame (header, footer, `<head>`) | `_includes/header.html`, `footer.html`, `head.html`, `_layouts/default.html` |
| What one reflection or blog post page looks like | `_layouts/reflection.html`, `_layouts/post.html` |
| What a lab dropdown looks like | `_includes/lab-card.html` |
| What the home page shows | `index.html` (reorder or remove the `include` lines) |

Content and presentation are kept apart on purpose: your writing lives in `_reflections/`, `_posts/` and `_data/`, so you can redesign the layouts and CSS later without touching it.

## Add a weekly reflection

1. Copy `templates/reflection-template.md` into `_reflections/wu-geng-lab/`.
2. Rename it `YYYY-MM-DD-week-NN-short-title.md`.
3. Fill in the front matter (`lab` must match an `id` in `_data/labs.yml`) and write the entry.
4. Commit. The site rebuilds in about a minute and the entry appears under its lab.

## Add a blog post

Copy `templates/blog-post-template.md` into `_posts/`, rename it `YYYY-MM-DD-short-title.md`, and write. Posts appear on the Blog page and on the home page.

## Move to a new lab

1. In `_data/labs.yml`, add a new block at the top with a new `id`. On the old lab, set `current: false` and fill in `end`.
2. In `_data/timeline.yml`, add a matching entry at the top (and set `lab:` to the new `id` to link it).
3. Create a folder `_reflections/<new-id>/` (optional but tidy) and set `lab: <new-id>` in new entries.

The new lab opens by default on the Reflections page; older labs stay collapsed.

## Change the structure later

- **Add a section** (for example Projects or Reading list): create a page like `blog.html` with its own `permalink`, then add it to `_data/nav.yml`. The menu and the home cards update on their own.
- **Rename a section**: change `title` in `_data/nav.yml` and the `title` in that page's front matter.
- **Different layout for lab dropdowns**: edit `_includes/lab-card.html` (it is the only place that draws them).
- **Group reflections differently** (by topic or term instead of lab): add a field to the entry front matter and build a new include like `lab-card.html` that filters on it.

## Preview locally (optional)

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000. You can skip this and edit directly on GitHub.

## Habits worth keeping

- Write in your own words and cite what you read.
- Include what confused you, not just what you learned.
- Don't post unpublished data, or anything your PI hasn't approved, from work in the lab.
- Keep it regular. Small weekly entries add up to a convincing record.
