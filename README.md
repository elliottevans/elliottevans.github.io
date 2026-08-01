# elliottevans.github.io

The source for my personal site, live at **https://elliottevans.github.io**.

The **entire site is a single file: [`index.html`](index.html)** — plain HTML, CSS, and JavaScript. No build step, no framework, nothing to install.

## Files

```
index.html   ← the whole site: content, styling, and scripts
assets/      ← logos, resume.pdf, favicon
```

## Editing

Open `index.html` in any text editor. It reads top to bottom:

- **`<style>`** (in `<head>`) — all the styling
- **Content sections** — navbar, hero, about, career timeline, projects, publications, footer
- **`<script>`** (near the bottom) — the typewriter tagline, navbar scroll behavior, and the GitHub project fetch

To change wording, a job entry, or a publication, edit that section directly. To swap a logo or the resume, replace the file in `assets/`.

To preview locally before publishing, just open the file:

```bash
open index.html
```

Bootstrap and Font Awesome load from a CDN, so the fully-styled page needs an internet connection.

## Publishing

This repo is a GitHub **user site**, so it deploys automatically:

```bash
git add -A
git commit -m "Update site"
git push origin master
```

GitHub Pages rebuilds and serves the new `index.html` from `master` within about a minute (watch the **Actions** tab for the "pages build and deployment" run). Hard-refresh the live site (Cmd+Shift+R) to get past any cached copy.

## Projects section

The project cards are fetched live from the GitHub API on page load — see the `SPECIFIC_REPOS` list in the `<script>` at the bottom of `index.html`. Add or change repo names there.

---

Originally forked from [@hashirshoaeb](https://github.com/hashirshoaeb)'s developer portfolio (React); since rewritten as a single static page.
