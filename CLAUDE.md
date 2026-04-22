# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project is

A static personal website for Sean McGinty — CMO and growth strategist based in Charleston, SC. The site is a single-page HTML file deployed to Vercel, served at **seanmcginty.me** (DNS via Cloudflare).

The project lives at `Claude/Projects/Sean Personal Website/` inside iCloud Drive. There is no build step, no framework, no npm. All HTML, CSS, and JS live inline in `index.html`.

## Deployment

```bash
vercel deploy --prod   # deploy to production
vercel dev             # local dev server
```

`vercel.json` configures the output directory as `.` (project root), enables clean URLs, and disables trailing slashes.

## File structure

- `index.html` — the entire site: HTML structure, all CSS (in a `<style>` block), and all JS (inline `<script>` at bottom)
- `brand-guidelines.html` — design token reference document (not a live page; for human reference only)
- `content-plan.md` — canonical source of truth for all copy, photo placement, and design decisions
- `Personal-details.md`, `personal-lifestory.md`, `Resume - Sean McGinty - March 2026.md` — source material; not deployed
- `photos/` — images referenced by `index.html`

## Design system

All design tokens are defined as CSS custom properties in `:root` inside `index.html`. **Do not hardcode color or font values** — use the variables:

| Token | Value | Use |
|---|---|---|
| `--bg` | `#F8F5F0` | Page background (warm parchment) |
| `--dark` | `#0A1628` | Darkest navy (hero bg, dark sections) |
| `--text` | `#141E30` | Primary body text |
| `--text-mid` | `#5C6878` | Secondary / subdued text |
| `--text-light` | `#9AA3AF` | Tertiary / placeholder text |
| `--accent` | `#1A7A78` | Teal accent (links, highlights) |
| `--accent-light` | `#E5F4F4` | Teal tint (backgrounds, chips) |
| `--accent-warm` | `#C87941` | Warm amber accent |
| `--border` | `#E2DDD6` | Dividers and borders |
| `--font-serif` | DM Serif Display | All headings |
| `--font-sans` | DM Sans | All body copy |

The max content width is `--max-w: 1100px` with fluid gutters via `clamp()`.

`brand-guidelines.html` is the full visual specification — spacing scale, border radii, component patterns, and motion principles. Consult it before introducing new UI patterns.

## Key interactions

- **Cycling hero headline** — the animated word cycling on a timer ("smarter / faster / more human / harder to ignore") is the signature interaction; handle with care
- **Scroll reveal** — elements with `.reveal` class animate in via IntersectionObserver; stagger delays use `.delay-1` through `.delay-4`
- **Sticky nav** — gains `.scrolled` class on scroll, triggering frosted-glass effect

## Email obfuscation

The email address (`smmcginty@gmail.com`) must **never appear in plain HTML source**. It is constructed at runtime via JavaScript. Cloudflare Email Obfuscation is also enabled as a second layer. Do not change this pattern.

## Content authority

`content-plan.md` is the single source of truth for all copy, photo selection decisions, and tone guidance. Check it before making any content changes. The tone is warm, direct, and personal — not corporate.

## Photos

Four approved photos live in `/photos/`:
- `IMG_7269.jpeg` — dogs (About section, personal)
- `family_snee.jpeg` — family on porch (About section, personal)
- `tsgb_clemson.jpeg` — Gator Bowl with mascot (Career, TaxSlayer entry)
- `tsgb_uva.jpeg` — field with Hannah after UVA win (About or Career)
