# Test, Lint, Validate: Building Unbreakable Frontends in the Age of AI

A presentation about staying in control when AI writes your code. Covers Test-Driven Development, programmatic guardrails (linting), and integration testing as the foundation for safe AI-assisted frontend development.

Built with [Slidev](https://sli.dev/).

## Demo

[View the slides](https://dipodidae.github.io/test-lint-validate-unbreakable-frontends-ai/)

## Getting Started

```bash
pnpm install
pnpm dev
```

Opens the presentation at [localhost:3030](http://localhost:3030). Edit `slides.md` to modify content.

## Tech Stack

- **Slidev** (v52) — Markdown-based presentation framework on Vite + Vue 3
- **Theme**: [@slidev/theme-seriph](https://github.com/slidevjs/themes/tree/main/packages/theme-seriph)
- **QR codes**: qrcode-generator

## Other Commands

```bash
pnpm build      # Build static site to dist/
pnpm export     # Export slides to PDF
```

## Deployment

Pushes to `main` automatically deploy to GitHub Pages via GitHub Actions.
