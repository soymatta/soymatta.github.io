# AGENTS.md

## Project

Single-page portfolio site for Yassed Matta. Astro 5 + Tailwind CSS v4, deployed to GitHub Pages.

## Commands

- `pnpm install` — install deps
- `pnpm dev` — local dev server at localhost:4321
- `pnpm build` — production build to `dist/` (only verification command available)

No linter, formatter, test suite, or typecheck script exists.

## Stack

- **Astro 5** — pages in `src/pages/`, components in `src/components/` (all `.astro`)
- **Tailwind CSS v4** — configured as Vite plugin in `astro.config.mjs`. Theme tokens defined via `@theme` in `src/styles/global.css`. Scoped `<style>` blocks in components require `@reference "../styles/global.css"` to use `@apply` with theme utilities.
- **TypeScript** — strict mode via `astro/tsconfigs/strict` (no `tsconfig` customization)

## Design Tokens (global.css)

Colors use CSS custom properties for dark/light switching (`.light` class on `:root`), mapped to Tailwind utilities via `@theme`:

| Token | Usage | Dark | Light |
|-------|-------|------|-------|
| `bg-page` | page background | #111113 | #f5f5f5 |
| `text-fg` | primary text | #ffffff | #111113 |
| `bg-card` | card/surface bg | #272729 | #ffffff |
| `bg-card-hover` | hover surface | #3a3a3d | #e5e5e5 |
| `text-muted` | secondary text | #8a8a8a | #6a6a6a |
| `border-line` | borders/dividers | #3a3a3d | #d1d1d1 |
| `bg-footer-bg` | footer background | #1f1f23 | #e5e5e5 |
| `text-accent` | brand blue | #2f53d7 | #2f53d7 |

Use these tokens as standard Tailwind classes (`bg-card`, `text-muted`, `border-line`, etc.). Avoid hardcoded hex in templates.

## Fonts

- **Varela** (body, default) — applied to `<body>` via base style
- **Istok Web** (headings, labels, nav) — applied to `h1-h6, strong, b` via base style
- Both defined as `@theme` tokens: `font-varela`, `font-istok`
- Font files in `public/fonts/`

## Layout

- Footer is full-width (outside `<main>` wrapper in `index.astro`)
- Content constrained by `px-[140px]` on `<main>` and `<body>` removed padding
- Navbar is fixed, centered with `backdrop-blur-md`

## JS

All JavaScript is centralized in a single `<script>` block at the bottom of `src/pages/index.astro`. Do not add `<script>` blocks to components.

Functions: `initTheme()`, `initLang()`, `initCopyEmail()`, `initContactForm()` — all re-init on `astro:after-swap`.

Email tooltip hover is CSS-only (Tailwind `group-hover:*` utilities). Only the copy-to-clipboard click uses JS.

## SEO

Meta tags (description, Open Graph, canonical) are in `index.astro` `<head>`. Site URL: `https://soymatta.github.io/`.

## Gotchas

- Tailwind v4 `@apply` in scoped `<style>` blocks requires `@reference "../styles/global.css"` or it will fail with "unknown utility class"
- Dark/light theme uses manual `.light` class toggle, not `prefers-color-scheme`
- "Download CV" links to `/cv.pdf` which does not exist in `public/` — the actual PDFs are at the repo root (`EN_Yassed Matta.pdf`, `ES_Yassed Matta.pdf`)
