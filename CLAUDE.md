# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The source for the live personal site at **https://elliottevans.github.io**. It is a **single static file, `index.html`** — hand-written HTML, CSS (one `<style>` block), and vanilla JavaScript (one `<script>` block). No build step, no framework, no `node_modules`, no package manager. Edit the file, open it in a browser, commit, push.

This repo previously held the compiled output of a React (CRA) app; it was consolidated to this one file. Do not reintroduce a build toolchain unless explicitly asked.

## Structure

```
index.html   ← the whole site
assets/      ← logos (PNG), resume.pdf, favicon.ico
```

`index.html` reads top to bottom: `<style>` in the head, then content sections in visual order (navbar → hero → about → experience timeline → projects → publications → footer), then the `<script>`.

## Deploy (important)

This is a GitHub **user site** (`<username>.github.io`), so **any push to `master` auto-deploys** — there is no build to run and no Pages config to change. Live within ~1 min; watch the repo's Actions tab. There is no staging branch: `master` is production.

## Editing notes

- **Content is inline, not data-driven.** Each section's text lives directly in its HTML. The career timeline (9 entries) and the publications list (9 articles) are literal markup — there is no config file.
- **Styling is CDN + inline.** Bootstrap 5 and Font Awesome 5.4.1 load from a CDN; everything custom (gradient hero, starfield, timeline, typography scale) is in the one `<style>` block. Full styling requires internet.
- **The hero gradient must keep `background-size: 1200% 1200%` in the inline `style` attribute**, alongside the `background:` shorthand. If `background-size` is moved to a CSS class, the inline `background:` shorthand resets it to `auto`, turning the slow single-color drift into a static full-rainbow. This bug already happened once.
- **The starfield** is a ~700-entry `box-shadow` list on `#stars` (and `#stars:after`). It was generated; don't hand-edit individual coordinates.
- **Projects are fetched live** from the GitHub API on page load. Repo names are in `SPECIFIC_REPOS` in the `<script>`. `svn_url` from the API is the repo's HTML URL. Unauthenticated requests are rate-limited (~60/hr per IP), so cards may briefly not render during heavy reloads — not a bug.
