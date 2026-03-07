# Claude Code for Non-Coders — Slide Deck

A [Marp](https://marp.app/)-based slide deck for a 45-minute sharing session on using Claude Code for non-coders.

## Prerequisites

- [Node.js](https://nodejs.org/) (v18+)

## Setup

```bash
npm install
```

## Usage

### Live preview (opens in browser with hot reload)

```bash
npm run dev
```

### Build static HTML

```bash
npm run build
```

Output: `dist/index.html`

### Export to PDF

```bash
npm run pdf
```

Output: `dist/slides.pdf`

## Presenting

1. Run `npm run dev` for live preview, or
2. Open `dist/index.html` in a browser after building
3. Press **F** for fullscreen, **P** for presenter notes

## Deployment

Slides auto-deploy to GitHub Pages on push to `main` via GitHub Actions.

## Structure

```
slides.md              # All slides (single Marp markdown file)
theme/custom.css       # Custom Marp theme
images/                # Diagrams and screenshots
marp.config.js         # Marp CLI configuration
.github/workflows/     # GitHub Actions deployment
```
