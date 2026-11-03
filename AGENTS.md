# Project conventions

## Tech stack

- Plain HTML, CSS, and browser JavaScript; no framework, package manager, build step, or runtime dependencies.
- `index.html` contains the page structure and links `style.css` plus `app.js` with `defer`.
- `style.css` contains all visual styling. Keep styles out of inline `style` attributes and HTML `<style>` blocks.
- `app.js` contains game state, calculations, and interactions. Keep scripts out of HTML `<script>` blocks.
- Google Fonts are loaded from Google Fonts; the system sans-serif and serif fallbacks keep the page usable if the fonts cannot load.

## Run locally

The game is static and needs no installation or build command. Open `index.html` in a modern browser. Keep `index.html`, `style.css`, and `app.js` together in the project root so their relative links resolve.

An optional local server can be started from the project root with Python:

```sh
python -m http.server 8000
```

Then visit `http://localhost:8000`. On Windows, `py -m http.server 8000` can be used if the `python` command is unavailable.

## Current setup

- The game runs a 30-day cookie shop season, starting with $100.
- Players choose among four cookie varieties, set batch size and price, and choose an advertising budget.
- Daily weather affects demand. The game tracks cash, reputation, total sales, profit, and a daily ledger.
- Customers are animated during the daily sales scene. Sales are capped by baked inventory, and the planned batch plus advertising cannot exceed available cash.
- The layout adapts for smaller screens and respects reduced-motion preferences.
- Game state exists in browser memory only; reloading starts a new season. There is no backend or save system.
- No automated test suite or lint setup is currently configured. `node --check app.js` checks JavaScript syntax when Node.js is installed; `git diff --check` checks patch whitespace.

## Change conventions

- Preserve the dependency-free, static-browser setup unless a change explicitly calls for a framework or build tool.
- Keep markup, styles, and game logic in their respective files. Use semantic HTML, accessible labels and status messages, visible keyboard focus, responsive layouts, and reduced-motion support.
- Preserve core economy rules: cash cannot be spent below zero, sales cannot exceed the day's baked inventory, and the 30-day progression and ledger must remain consistent.
- Do not commit changes unless the user explicitly asks for a commit.
