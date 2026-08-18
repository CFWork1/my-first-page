# Project rules — personal page

Repository overlay for this static personal site.

Voice and biography live in [about-me.md](about-me.md). Site files live under `src/`. This file records stack, layout, and how to publish.

---

## Project identity

| Item | Value |
|------|-------|
| Kind | Personal introduction page |
| Audience | Classmates, hosts, anyone who cares to meet the author |
| Stack | Plain HTML + CSS (no build step, no framework) |
| Source | `src/` |
| Copy source | [about-me.md](about-me.md) |
| Hosting target | Cloudflare Pages (or any static host) |

---

## Why HTML + CSS

A single-page static site is the best fit:

- Opens as files, works offline, and deploys by uploading `src/`.
- Cloudflare Pages, GitHub Pages, Netlify, and similar hosts expect exactly this.
- No Node, no CMS, no database, no monthly plugin tax.

**WordPress** can display the same HTML, but it is heavier than this page needs (PHP, themes, updates). Prefer a static host. If WordPress is required later, paste the markup into a Custom HTML block and copy `src/css/styles.css` into Appearance → Additional CSS, then fix image URLs.

Do not add React, a bundler, or a CSS framework unless asked.

---

## Repository map

```
doc/
  about-me.md          ← biography and voice (edit first)
  project-rules.md     ← this file
src/
  index.html           ← the page
  css/styles.css       ← all styling
  pictures/            ← portraits and other images
```

All public assets belong under `src/`. Documentation belongs under `doc/` (not a hidden `.doc/` folder).

---

## Content rules

- Keep the working first name, age, and story in [about-me.md](about-me.md). The HTML should follow that file, not invent a second biography.
- Replace the placeholder name **Lena**, the portrait, and the contact links before publishing.
- Portrait in use: `src/pictures/me_smiling_01.png` (cutout). Original upload: `src/pictures/me_smiling_01.jpg`.
- Tone: warm, specific, and sincere. No corporate résumé voice, no fake humility, no exaggerated claims.
- Do not add sections (blog, portfolio, CV) unless asked.

---

## Design rules

- One page, semantic HTML (`header`, `main`, `section`, `footer`).
- Warm paper background, olive/sage accents (from the portrait shirt), editorial serif for the greeting, humanist sans for body text.
- Mobile-first. The photo and text stack on small screens.
- No JavaScript unless a real interaction needs it. Smooth scrolling is CSS.
- Keep contrast readable. Decorative blobs and frames must not hide text.

---

## Local preview

From the repo root:

```sh
# any static server pointed at src/
python3 -m http.server 8080 --directory src
```

Then open `http://127.0.0.1:8080/`.

Or open `src/index.html` directly in a browser.

---

## Publish (Cloudflare Pages)

1. Put this repo on GitHub (or upload `src/` in the Cloudflare dashboard).
2. Create a Pages project.
3. Build command: empty.
4. Output directory: `src`.

The site is then a public URL. Custom domains are optional.

---

## Required context

Before changing the page, read:

1. This file
2. [about-me.md](about-me.md)
3. `src/index.html` and `src/css/styles.css`

Link between docs; do not duplicate long biography text into this file.
