# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static personal resume site for Derrek Brack (blockchain developer). Plain HTML/CSS/JS — no package.json, no build step, no tests, no framework.

## Running locally

Open `index.html` directly in a browser, or serve the directory over HTTP (e.g. `python3 -m http.server`). There is no dev server, bundler, or lint tooling to run.

## Architecture

- `index.html` — single page with sections in fixed order: header, `projects`, `about`, `skills`, `experience`, `contact`, footer. Content is hard-coded; updating the resume means editing this file.
- `css/resume.css` — all styles. Design tokens are CSS custom properties at `:root` (`--black`, `--gray`, `--white`, `--blue`, `--border-gradient`, and `--font-96`/`--font-40`/`--font-32` which use `clamp()` for fluid type). Layout relies on utility classes (`flex-center`, `flex-start`, `flex-between`, `flex-list`) composed in markup rather than component-scoped rules.
- `js/resume.js` — currently empty placeholder; wired in at the bottom of `index.html` after the vendor scripts.
- `vendor/` — pinned third-party assets loaded via `<link>`/`<script>` tags, not a package manager: `fontawesome-free-5.15.4-web` (icons used throughout skills/social lists), `jquery`, and `jquery-easing`. Do not replace these with CDN links or npm installs without a reason — the site is intentionally dependency-free at runtime.
- `img/` — profile photo, SVG decorations (`Ring.svg`, `Check.svg`, `Dot.svg`, `ArrowUpRight.svg`), backgrounds, and `img/projects/` for project card thumbnails referenced from the projects section.

## Conventions

- Commented-out blocks in `index.html` (extra project cards, extra social links, extra skill icons) are templates kept for when more content is added — follow their shape rather than inventing new markup.
- Profile image and social-links block appear twice (header and contact section); keep them in sync when editing.
