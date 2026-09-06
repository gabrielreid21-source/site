# authorericabiddings.com — client review build

Static one-page site for Erica Jones Biddings. Built from `Landing Page v3.dc.html`
in the design handoff bundle (the approved design).

**This is a temporary preview for client approval, not the launch build.**

## Files

| File | Notes |
|---|---|
| `index.html` | The whole site. No build step, no dependencies. |
| `assets/` | Headshot, three book covers, books-on-table photo. |
| `robots.txt` | Blocks all crawlers while this is a preview. |
| `.nojekyll` | Tells GitHub Pages to serve files as-is. |

## Publishing to GitHub Pages

1. Create a new **private** repo on GitHub (e.g. `erica-biddings-preview`).
   Private repos can still serve Pages on paid plans; on a free plan the repo
   must be public — see the note below.
2. Push this folder to it (see the commands in the handoff chat).
3. Repo → **Settings** → **Pages** → Source: **Deploy from a branch**,
   Branch: `main`, Folder: `/ (root)` → Save.
4. Wait ~1 minute. URL will be `https://<username>.github.io/<repo>/`.

**If the repo has to be public:** the site is already `noindex, nofollow` and
`robots.txt` disallows everything, so it will not turn up in search results.
It is still technically reachable by anyone with the URL — fine for a client
review link, worth knowing before sharing it widely.

## Before launch — remove the preview scaffolding

- [ ] Delete the `<meta name="robots" content="noindex, nofollow">` line in `index.html`
- [ ] Delete `robots.txt` (or replace with an allow-all + sitemap)
- [ ] Replace the Google Form placeholder block (marked with a comment in `index.html`)
- [ ] Swap in real cover art for books 01 and 02 (current ones are cropped from a photo)
- [ ] Compress and resize the images — currently ~24 MB total, far too heavy for a page
      that is mostly opened on phones from an email or WhatsApp link
- [ ] Confirm the favicon and Open Graph image with the client (both are stand-ins)
- [ ] Point `og:image` at an absolute URL on the final domain

## Changes made against the design file

The design file is a Design Component prototype, not runnable HTML. To make it a
real page:

- Removed the `<x-dc>` / `<helmet>` wrappers and the `support.js` runtime
- Replaced the four `{{ amazonUrl }}` template holes with the real Amazon URL
- Converted `style-hover` attributes (a prototype-only feature) into real CSS
  `:hover` rules; the affected elements now carry their styles in classes rather
  than inline, because inline styles cannot be overridden by `:hover`
- Added focus-visible outlines (open item 3 in the handoff)
- Added `lang`, `<title>`, meta description, Open Graph and Twitter card tags,
  a placeholder favicon, `theme-color` and `color-scheme` (open item 4)
- Added `prefers-reduced-motion` guard on `scroll-behavior: smooth`
- Added intrinsic `width`/`height` on the headshot to reserve layout space

Everything else — colors, type, spacing, copy, markup structure — is verbatim
from the approved design.
