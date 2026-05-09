# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Jekyll 4.3.3 static site for HALOHUB., LTD, deployed at https://halohub.vn (see `CNAME`). Note: `README.md` mentions `halohub.io` but the live host and `_config.yml` `url` are `halohub.vn` — treat `_config.yml`/`CNAME` as the source of truth.

## Commands

```bash
bundle install                  # install Ruby gems (first time / after Gemfile changes)
make serve                      # = bundle exec jekyll serve --livereload (dev server with live reload)
bundle exec jekyll build        # one-shot build into _site/
```

There is no test suite, linter, or JS build step — assets are loaded from CDNs (Bootstrap 5, Swiper 8, jQuery) in `_includes/head.html`, and the only local stylesheet is `assets/css/main.css`.

## Architecture

The site is small and entirely data-driven; a few patterns are worth knowing before editing:

- **Single layout, page-controlled chrome.** Every page uses `_layouts/default.html`, which composes `head.html` → `navbar.html` → `banner.html` → content → `footer.html`. Two front-matter switches alter the layout:
  - `show_banner: true` — renders the hero banner (`_includes/banner.html` is gated by `include.show`).
  - `hide_content: true` — suppresses `{{ content }}` (the home page uses this so `index.md` body is ignored in favor of the banner).

- **Navigation comes from `_data/toc.yml`, not from pages.** Adding a new page (e.g. under `pages/`) does *not* make it appear in the navbar. You must also add a `{ title, url }` entry to `_data/toc.yml`. The `GAMES` entry is currently commented out there — uncommenting it is how the games section gets re-exposed.

- **Pages live in `pages/` with explicit `permalink`.** `pages/about.md` sets `permalink: about` so it resolves to `/about`. Follow this convention for new top-level pages rather than relying on Jekyll's default path-based permalinks.

- **Lists rendered from `_data/*.yml`.**
  - `_data/contact.yml` drives social icons in `footer.html` (each entry has `show_on_footer` to toggle visibility) and the contact list rendered by `pages/about.md`. Icons must exist as SVGs at `assets/img/icons/{icon}.svg`.
  - `_data/games.yml` lists games (currently `mole-maniacs`) but there is no game page or layout yet — the data and `assets/img/mole-maniacs/` screenshots exist ahead of the page. If building game pages, expect to add a layout + iterate over `site.data.games`.

- **`_includes/swiper.html` is opt-in.** It initializes a Swiper carousel but is not included from `default.html`; pages that need a slider must `{% include swiper.html %}` themselves and provide the matching `.swiper` markup.

- **Root-level non-Jekyll files** (`app-ads.txt`, `googlef90fcf7169ae8acf.html`, `CNAME`, favicons under `assets/favicons/`) are served verbatim and used for ad-network / search-console / DNS verification — leave them alone unless explicitly updating those integrations.
