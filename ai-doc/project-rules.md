# Project rules — personal page

Repository overlay for this static personal site.

Voice and biography live in [about-me.md](about-me.md). The published site lives at the **repository root**. This file records stack, layout, and how to publish.

---

## Project identity

| Item | Value |
|------|-------|
| Kind | Personal introduction page |
| Audience | Classmates, hosts, anyone who cares to meet the author |
| Stack | Plain HTML + CSS (no build step, no framework) |
| Source | Repository root (`index.html`, `css/`, `pictures/`) |
| Copy source | [about-me.md](about-me.md) |
| Hosting | Cloudflare Pages or GitHub Pages — **zero extra folder config** |

---

## Why HTML + CSS

A single-page static site is the best fit:

- Opens as files, works offline, and deploys by pushing the repo.
- Cloudflare Pages and GitHub Pages both look for `index.html` at the repo root by default.
- No Node, no CMS, no database, no monthly plugin tax.

**WordPress** can display the same HTML, but it is heavier than this page needs (PHP, themes, updates). Prefer a static host. If WordPress is required later, paste the markup into a Custom HTML block and copy `css/styles.css` into Appearance → Additional CSS, then fix image URLs.

Do not add React, a bundler, or a CSS framework unless asked.

---

## Repository map

```
index.html             ← homepage (hosts look here)
css/styles.css         ← all styling
pictures/              ← portraits and other images
.nojekyll              ← tell GitHub Pages this is static HTML, not Jekyll
ai-doc/
  about-me.md          ← biography and voice (edit first)
  project-rules.md     ← this file
```

Published site files stay at the repo root so Cloudflare Pages (output `/`) and GitHub Pages (source `/`) find them with no settings.

Agent notes live in `ai-doc/`, not `doc/` or `docs/`. GitHub Pages’ optional publish folder is `/docs`; we do not use that name.

Relative links in `index.html` (`css/styles.css`, `pictures/…`) stay valid because those folders sit next to the homepage.

---

## Content rules

- Keep the working first name, age, and story in [about-me.md](about-me.md). The HTML should follow that file, not invent a second biography.
- Replace the placeholder name **Lena**, the portrait, and the contact links before publishing.
- Portrait in use: `pictures/me_smiling_01.png` (cutout). Original upload: `pictures/me_smiling_01.jpg`.
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
python3 -m http.server 8080
```

Then open `http://127.0.0.1:8080/`.

Or open `index.html` directly in a browser.

---

## Publish (zero config)

Leave host defaults. Do not set an output directory of `src` (that folder is gone).

**Cloudflare Pages:** connect the Git repo. Production branch `main`. Build command empty. Output directory `/` or empty (repo root).

**GitHub Pages:** Settings → Pages → Deploy from a branch → `main` → `/ (root)`.

`.nojekyll` at the repo root stops GitHub from running Jekyll, so `ai-doc/*.md` is not turned into extra site pages. Direct URLs under `/ai-doc/` can still fetch those files if someone knows the path; they are notes, not the homepage.

---

## Required context

Before changing the page, read:

1. This file
2. [about-me.md](about-me.md)
3. `index.html` and `css/styles.css`

Link between docs; do not duplicate long biography text into this file.
