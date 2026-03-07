# Claude Code Sharing — Marp Slide Deck

## Overview
A Marp-based slide deck for a 45-minute session on Claude Code for non-coders.

## Build & Run
- Install: `npm install`
- Dev preview: `npm run dev`
- Build HTML: `npm run build` (outputs to `dist/index.html`)
- Build PDF: `npm run pdf` (outputs to `dist/slides.pdf`)

## Structure
- `slides.md` — single Marp markdown file (all slides)
- `theme/custom.css` — custom Marp theme
- `images/` — diagrams, screenshots
- `marp.config.js` — Marp CLI configuration
- `.github/workflows/deploy.yml` — GitHub Pages deployment

## Feature Checklist
- [x] Project initialisation (git, .gitignore, CLAUDE.md)
- [x] Marp tooling setup (package.json, marp.config.js)
- [x] Custom CSS theme
- [x] Slide deck (13 sections from hackathon outline)
- [x] GitHub Actions for Pages deployment
- [x] README.md
- [ ] GitHub repo created and pushed

## Decisions
- Single slides.md file (no splitting)
- Marp CLI via npm (not Docker)
- GitHub Pages deploy via Actions (not gh-pages branch)
- Custom theme for branding
