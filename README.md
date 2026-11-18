# Visualization and Graphics Lab

This is the website repository for the **Visualization and Graphics Lab (VGL)** at the [**University of San Francisco**](https://www.usfca.edu/), published at <https://vgl.cs.usfca.edu/>.

The site is built with [Jekyll](https://jekyllrb.com/) and hosted on [GitHub Pages](https://pages.github.com/). Pushing to `master` publishes the site automatically, usually within a minute or two.

## Repository layout

| Path | What it is |
|---|---|
| `_data/papers.yml` | All publications, posters, books, and chapters (shown on the Research and Home pages) |
| `_data/people.yml` | Faculty bios, photos, and profile links (shown on the About page) |
| `_posts/` | Blog / news posts |
| `index.html`, `about.html`, `research.html`, `blog/index.html` | Page templates and introductory text |
| `_includes/` | Shared pieces: `head.html` (meta tags, fonts, icons), `navbar.html`, `footer.html`, `postbox.html` (blog post card), `citation.html` (formats one publication) |
| `_layouts/` | `default.html` for pages, `posts.html` for blog posts |
| `css/main.scss` | Bulma customization (USF colors, fonts) |
| `css/vgl.css` | Small site-specific CSS overrides |
| `_sass/bulma/` | Vendored copy of [Bulma](https://bulma.io/) 0.6.2 (do not edit) |
| `images/` | Faculty photos and the site logo |
| `assets/` | PDFs, posters, and images linked from posts and papers |

## Common updates

### Add a publication

Add an entry anywhere under `publications:` in `_data/papers.yml`; order doesn't matter because entries are sorted by date when the site is built. The newest three also appear under **Recent Papers** on the home page.

```yaml
  - title   : 'Paper Title'
    authors :
      - 'Student Name'
      - '<u>Alark Joshi</u>'    # wrap lab members in <u></u> to highlight them
      - '<u>Sophie Engle</u>'
    cite    : '<em>Proceedings of the Venue (ABBR)</em>, <strong>Best Paper Award</strong>'
    pages   :                   # optional
      - 1
      - 10
    date    : 2026-10-01        # YYYY-MM-DD; use 01 for an unknown day
    nomonth : true              # optional; show only the year when the month is unknown
    etal    : true              # optional; append "et al." to a truncated author list
    links   :                   # optional
      - link: 'https://doi.org/...'
        icon: 'fas fa-link'
        name: 'Publisher page'  # tooltip and screen-reader label
      - link: 'https://www.cs.usfca.edu/~apjoshi/papers/....pdf'
        icon: 'fas fa-file-pdf'
        name: 'PDF'
```

Conventions for link icons:

| Link | `icon` | `name` |
|---|---|---|
| DOI / publisher page | `fas fa-link` | `Publisher page` |
| PDF / preprint | `fas fa-file-pdf` | `PDF` or `Preprint` |
| Slides | `fas fa-file-powerpoint` | `Slides` |
| Code repository | `fab fa-github` | `Code repository` |
| Project website | `fas fa-globe` | `Website` |
| Video | `fas fa-video` | `Video` |
| Book | `fas fa-book` | `Book` |
| Award (no link) | `fas fa-trophy` with `link: false` | e.g. `Best Paper Award` |

Tips:

- Inside single-quoted values, write an apostrophe as two apostrophes: `'Bloom''s Taxonomy'`.
- Write `&` as `&amp;` in titles and venues.
- Prefer `https://doi.org/...` links and PDFs hosted on a faculty site or in `assets/`. Avoid Google Drive links, which break when sharing settings change.

### Add or update a person

Edit `_data/people.yml`. Each person has `first`, `last`, `image` (a file in `images/`, about 192×192 px or larger and square), `about` (bio paragraph), and a list of `links`, each with a `name`, `link`, and `icon`. Common icons: `fas fa-globe` (website), `fab fa-bluesky`, `fab fa-github`, `fas fa-graduation-cap` (Google Scholar), `fas fa-envelope` (email).

### Add a blog post

Create a file in `_posts/` named `yyyy-mm-dd-short-title.html` (or `.md` for Markdown), with this front matter:

```yaml
---
layout: posts
title: Our Paper Was Accepted at VIS 2026
author: Alark Joshi
icon: fas fa-thumbs-up    # any Font Awesome icon, shown beside the post
---

<p>Post content, written in HTML using Bulma classes (or Markdown in a .md file).</p>
```

The five most recent posts appear on the home page, and the blog shows five posts per page.

### Archive an old post

When a post is about something time-sensitive (job openings, course listings, meeting schedules, events) and that thing has passed, add `archived: true` to its front matter instead of deleting it:

```yaml
---
layout: posts
title: Spring 2017 Lab Meetings
author: Sophie Engle
icon: fas fa-calendar-alt
archived: true
---
```

Archived posts stay at the same URL but show an **Archived** tag and a notice that the information is no longer current.

### Icons

Icons come from [Font Awesome 6](https://fontawesome.com/search?m=free) (free set), loaded in `_includes/head.html`. Older Font Awesome 5 names such as `fas fa-file-alt` still work. Use `fas` for solid icons and `fab` for brand icons.

### Links

Use `https://` for all links. For pages on this site, use Liquid's `relative_url` filter, e.g. `{{ "/research.html" | relative_url }}`; note the quotes around the path. Alark's site is `https://www.cs.usfca.edu/~apjoshi/` (the bare `cs.usfca.edu` host no longer resolves).

## Local setup

GitHub Pages uses a [specific version](https://pages.github.com/versions/) of Jekyll, pinned by the `github-pages` gem in the `Gemfile`. You need Ruby 3.x and Bundler.

```sh
bundle install                    # first time only (and after updating the github-pages gem)
bundle exec jekyll serve --watch  # then open http://localhost:4000
```

If you see `Could not find proper version of jekyll`, run `bundle install` again; this usually means the gems are missing or out of date. Running `bundle update github-pages` brings your local versions in line with GitHub Pages.

Before pushing a larger change, it's worth checking the build output for errors and spot-checking the Home, Research, About, and Blog pages locally.
