# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A personal academic homepage (https://lhkhiem28.github.io) built with Jekyll on GitHub Pages, using a vendored fork of the Minimal Mistakes theme (the "academicpages" style setup). Pushing to `master` deploys it: GitHub Pages builds the site itself, and there is no CI or test suite.

## Commands

- Local preview: `bundle install`, then `bundle exec jekyll serve` (output goes to `_site/`, which is gitignored). The `Gemfile` pins the `github-pages` gem so the local build matches the GitHub build.
- Rebuild minified JS (only needed after editing `assets/js/_main.js` or `assets/js/plugins/*`): `npm install`, then `npm run build:js`. This regenerates `assets/js/main.min.js`, which is committed. The sources are excluded from the Jekyll build in `_config.yml`.

## Where content lives

Almost every edit is to content, not to theme code:

- `_pages/about.md`: the home page (`permalink: "/"`).
- Publications and experience: edit `_data/publications.yml` and `_data/experience.yml`, not the pages. Each YAML file is a list of groups (`- entries: [...]`), and a grey `<hr>` is drawn after each group. The field list is in a comment at the top of each file. `hidden: true` keeps an entry in the page source as an HTML comment without displaying it. To hide an entry, set this flag rather than deleting the entry. `_pages/publications.md` and `_pages/experience.md` contain only front matter and an `{% include %}`.
- `_includes/publication-list.md` and `_includes/experience-list.md` are Liquid templates. They emit Markdown, which kramdown then converts to HTML. The output matches the hand-written pages these templates replaced, so watch the whitespace control (`{%-` / `-%}`) when editing them. In particular, a blank line inside an experience list item breaks the list.
- `_data/navigation.yml`: top nav links. Commented-out entries are disabled sections.
- `_config.yml`: site metadata and the sidebar author profile (`author:` block: name, bio, avatar, Scholar link, email). `author.avatar` is resolved relative to `/assets/` (see `_includes/author-profile.html`). Jekyll does not hot-reload `_config.yml`, so restart `jekyll serve` after changing it.
- `assets/`: images and PDFs that pages link to (for example `assets/Thesis.pdf`).

## Theme code

`_layouts/`, `_includes/`, and `_sass/` hold the vendored theme. Pages default to the `single` layout with `author_profile: true` (set under `defaults` in `_config.yml`). The publications and experience pages use `layout: archive`. Unused theme parts (extra layouts and includes, sample data, Jekyll collections, Staticman comments, Font Awesome regular icons) have been removed. Before re-enabling a theme feature, check that the files it needs still exist.
