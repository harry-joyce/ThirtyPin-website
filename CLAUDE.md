# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static marketing website for ThirtyPin — a native macOS app for syncing music libraries to classic iPods. The site is hosted on GitHub Pages with no build step or framework. All pages are plain HTML/CSS/JS.

## Structure

```
index.html       — Landing page (hero, features, how it works, compatibility, notify CTA)
changelog.html   — Release timeline
docs.html        — Documentation and FAQ (details/summary accordion)
contact.html     — Contact form + bug report section
css/style.css    — Single stylesheet for all pages
js/main.js       — Shared JS (mobile menu, scroll animations, form submissions)
.nojekyll        — Prevents GitHub Pages from running Jekyll
```

## Hosting

Served from the root of the `main` branch via GitHub Pages. Custom domain `thirtypin.app` is configured via the `CNAME` file. All paths are relative.

## Design system (defined in css/style.css `:root`)

- **Background:** `#FAF7F2` (warm cream) with `#FFFFFF` cards
- **Dark sections:** `#1A1A1A`
- **Brand blue:** `#0A7AFF` — primary CTAs
- **Amber accent:** `#C97C10` — eyebrows, step numbers, logo "Pin"
- **Heading font:** `EB Garamond` (loaded from Google Fonts) — all `h1`–`h4`
- **Body font:** Helvetica Neue / `-apple-system`

## Conventions

- All section animations use the `.fade-up` class + IntersectionObserver in `main.js`.
- Inner pages (changelog, docs, contact) use `.page-header` for their hero, not `.hero`.
- The nav is shared across all pages; update all four HTML files if nav links change.
- The footer block is duplicated in each HTML file — keep them in sync.

## Things to fill in before launch

1. **Formspree form ID** — replace `REPLACE_WITH_YOUR_FORM_ID` in `index.html` (notify form) and `contact.html` (contact form).
2. **GitHub repo URL** — replace `REPLACE_WITH_YOUR_GITHUB_REPO` in `contact.html` bug report link and footer GitHub links.
3. **Download link** — when the app is ready, replace `href="#download"` on the nav CTA and hero button with the actual download URL or Mac App Store link.
4. **Copyright year** — update the year in all four footer blocks.
5. **OG image** — add a `<meta property="og:image">` tag and a social preview image.

## ThirtyPin app reference

The app source lives at `/Users/harry/development/ThirtyPin`. Key facts relevant to website copy:

- macOS SwiftUI app, macOS 13+ required
- Uses `libgpod` to read/write the iPod database
- Supports: iPod Classic (1G–7G), Nano (1G–7G), Shuffle (1G–4G), mini, Photo, Video
- Two sync modes: Safe (only removes what ThirtyPin added) and Full Replace
- FFmpeg for transcoding; SQLite for settings and track records
- "ThirtyPin" refers to the 30-pin dock connector used on classic iPods
