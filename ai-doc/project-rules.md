# Project rules — personal page

Repository overlay for this static personal site.

Voice and biography live in [about-me.md](about-me.md). The published site lives at the **repository root**. This file records stack, layout, and how to publish.

---

## Project identity

| Item | Value |
|------|-------|
| Kind | Personal introduction page |
| Audience | Classmates, hosts, anyone who cares to meet the author |
| Stack | Plain HTML + CSS (no build step, no framework, no JavaScript) |
| Source | Repository root (`index.html`, `css/`, `pictures/`) |
| Copy source | [about-me.md](about-me.md) |
| GitHub | `https://github.com/CFWork1/my-first-page.git` (branch `main`) |
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

There is no `src/` folder. Do not put the homepage back under `src/` — hosts would then need extra config.

---

## Page structure

One page, four sections, in `index.html`:

| Anchor | Role | Copy from |
|--------|------|-----------|
| `#top` | Hero: name, short hello, portrait | Snapshot + short version in [about-me.md](about-me.md) |
| `#about` | Three traits: optimistic, soft-hearted, social | How I come across |
| `#hello` | Longer note + blockquote | How I am with people + words to live by |
| `#connect` | Email and Instagram placeholders | Contact details you actually use |

Keep this shape. Do not add sections (blog, portfolio, CV) unless asked.

---

## Content rules

- Keep the working first name, age, and story in [about-me.md](about-me.md). The HTML should follow that file, not invent a second biography.
- Working name on the page: **Lena** (placeholder). Replace the name, portrait, and contact links before publishing.
- Portrait in use: `pictures/me_smiling_01.png` (cutout). Original upload: `pictures/me_smiling_01.jpg`.
- Contact placeholders in `#connect`: `hello@example.com` and `https://instagram.com/` / `@lena`.
- Tone: warm, specific, and sincere. No corporate résumé voice, no fake humility, no exaggerated claims.

---

## Design rules

- Semantic HTML (`header`, `main`, `section`, `footer`). Skip-to-content link at the top.
- Warm paper background (`#f4efe6`), olive/sage accents from the portrait shirt, terracotta kickers.
- Editorial serif **Fraunces** for headings; humanist sans **Figtree** for body (Google Fonts).
- Mobile-first. Below 840px the photo stacks above the hero text and traits become a single column.
- No JavaScript unless a real interaction needs it. Smooth scrolling is CSS (`scroll-behavior`); respect `prefers-reduced-motion`.
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

**Cloudflare Pages (Git):** connect `CFWork1/my-first-page`. Production branch `main`. Build command empty. Output directory `/` or empty (repo root).

**GitHub Pages:** Settings → Pages → Deploy from a branch → `main` → `/ (root)`.

`.nojekyll` at the repo root stops GitHub from running Jekyll, so `ai-doc/*.md` is not turned into extra site pages. Direct URLs under `/ai-doc/` can still fetch those files if someone knows the path; they are notes, not the homepage.

### If Cloudflare cannot connect to GitHub

That is a GitHub App install problem, not a missing `index.html`. Uninstall **Cloudflare Workers and Pages** from GitHub, then reconnect from the Cloudflare dashboard (**Connect to Git**), not from GitHub Marketplace. One GitHub account can only be tied to one Cloudflare account.

**Direct Upload** (skips Git): dashboard → Workers & Pages → Create → Pages → Upload assets, or from the repo root:

```sh
npx wrangler pages deploy .
```

That publishes a static Pages site (`*.pages.dev`). It does not convert later into a Git-connected project; create a new Git-backed project once the App works.

Do **not** use `npx wrangler deploy` here. That command publishes a **Worker** (server-side JS) and needs Worker config this repo does not have.

---

## Required context

Before changing the page, read:

1. This file
2. [about-me.md](about-me.md)
3. `index.html` and `css/styles.css`

Link between docs; do not duplicate long biography text into this file.
