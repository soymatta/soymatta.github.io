# Yassed Matta — Portfolio

Personal portfolio site for Yassed Matta, fullstack web & mobile developer.

**Live:** [soymatta.github.io](https://soymatta.github.io/)

## Stack

- **Astro 5** — static site generator
- **Tailwind CSS v4** — utility-first styling via Vite plugin
- **TypeScript** — strict mode

## Features

- Dark / light theme toggle
- Spanish / English language toggle
- Responsive design (mobile hamburger menu)
- Contact form with math captcha
- SEO meta tags, Open Graph, and structured data
- GitHub Pages deployment via Actions

## Project Structure

```text
/
├── public/
│   └── fonts/          # Istok Web + Varela font files
├── src/
│   ├── components/     # Navbar, Buttons, Studies, Projects, etc.
│   ├── images/         # SVG icons and profile image
│   ├── pages/
│   │   └── index.astro # Single-page app (all sections + JS)
│   └── styles/
│       └── global.css  # Tailwind config, theme tokens, animations
└── package.json
```

## Commands

| Command | Action |
| :------ | :----- |
| `pnpm install` | Install dependencies |
| `pnpm dev` | Local dev server at `localhost:4321` |
| `pnpm build` | Production build to `dist/` |
| `pnpm preview` | Preview build locally |
