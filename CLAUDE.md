# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A Slidev presentation: **"Test, Lint, Validate: Building Unbreakable Frontends in the Age of AI"** — a technical talk about TDD, programmatic guardrails (linting), and integration testing as foundations for safe AI-assisted frontend development.

## Commands

```bash
pnpm install              # Install dependencies (uses pnpm@10.33.0)
pnpm dev                  # Start dev server at localhost:3030 (opens browser)
pnpm build                # Build static site to dist/
pnpm export               # Export slides to PDF
```

For GitHub Pages deployment, the build uses a base path:
```bash
pnpm exec slidev build --base /test-lint-validate-unbreakable-frontends-ai/
```

There are no tests or linting configured in this project.

## Architecture

- **slides.md** — The entire presentation content (single-file Slidev format). Contains all slides, speaker notes (in HTML comments), transitions, and embedded Vue component usage.
- **components/** — Vue 3 components automatically available in slides: `Counter.vue` (interactive demo), `QRCode.vue` (generates QR codes via `qrcode-generator`).
- **snippets/** — Code snippets referenced from slides (`external.ts`).
- **pages/** — Additional slide pages that can be imported (`imported-slides.md`).

## Tech Stack

- **Slidev** (v52) — Markdown-based presentation framework built on Vite + Vue 3
- **Theme**: `@slidev/theme-seriph` with dark color scheme, Inter/Fira Code fonts
- **Styling**: UnoCSS (bundled with Slidev)
- **Package manager**: pnpm (version specified in `packageManager` field)

## Deployment

- **GitHub Pages**: Primary deployment via `.github/workflows/deploy.yml` (triggers on push to `main`)
- **Vercel**: Configured in `vercel.json` (SPA rewrite to index.html, output from `dist/`)
- **Netlify**: Configured in `netlify.toml`

## Slidev Conventions

- Slides are separated by `---` in `slides.md`
- Frontmatter between `---` markers configures per-slide options (transition, background, class, layout)
- `<v-clicks>` / `<v-click>` wraps content for progressive reveal
- Speaker notes go in `<!-- ... -->` HTML comments after slide content
- Vue components from `components/` are auto-registered and usable directly in markdown
