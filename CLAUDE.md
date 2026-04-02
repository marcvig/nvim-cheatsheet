# nvim-cheatsheet

Single-page Neovim command reference cheatsheet.

## Site URL
https://neovimcheatsheet.com

## Stack
- Single `index.html` — no build step, no dependencies
- Deployed on Cloudflare Pages with custom domain
- Preview server: `python3 -m http.server 3001` (port 3001 — 3000 is taken by tmux cheatsheet)

## Design
- Matches the cheatsheet suite aesthetic (tmux, git, atuin, zellij)
- Primary accent: #7ee787 (green)
- Command color: #e3b341 (yellow/amber)
- Font: JetBrains Mono (commands), Segoe UI (UI)
- Dark default; light mode toggle with localStorage key `nvim-theme`
- Flash-prevention inline script in `<head>` applies saved theme before first paint

## File Structure
- `index.html` — all HTML, CSS, and JS in one file (no separate stylesheets or scripts)
- `og-image.png` — 1200×630 social preview image
- `og-image.html` — source file to regenerate og-image.png (see below)
- `favicon.svg` — site favicon
- `robots.txt` — allows all crawlers, references sitemap
- `sitemap.xml` — single-page sitemap
- `wrangler.jsonc` — Cloudflare Pages config

## Regenerating og-image.png
```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless=new --screenshot="og-image.png" \
  --window-size=1200,630 --hide-scrollbars --disable-gpu \
  "file:///Users/marcvigod/Documents/GitHub/nvim-cheatsheet/og-image.html"
```

## Key Features
- Live search filtering across all cards (textContent only, not data attributes)
- Tooltip system: hover (2s delay on rows, 400ms on headers) or click any command/header/legend badge
- Tooltip toggle switch — persisted in localStorage key `nvim-tooltips`
- Card header tooltips — colored to match their accent color via getComputedStyle
- Mode legend badge tooltips (N Normal, I Insert, V Visual, C Command)
- Light/dark mode toggle
- Back-to-top button (appears after 300px scroll)
- Penguin 🐧 easter egg with canvas-confetti explosion
- Search clear (✕) button

## Footer Cross-Links
Uses the centralized cheatsheet registry — never hardcode "Also check out" links.
Registry: `https://cdn.jsdelivr.net/gh/marcvig/cheatsheet-registry@main/cheatsheets.json`
CURRENT_DOMAIN for this site: `neovimcheatsheet.com`

## Tooltip System Notes
- `data-tip` = description shown in tooltip body
- `data-cmd` = title shown in tooltip header (overrides auto-detection)
- `data-example` = code shown in example block (hides example section if absent)
- `data-danger` = triggers red warning banner at top of tooltip
- Placeholder syntax `<x>` in data-tip/cmd is auto-styled amber italic via JS post-processing
- `openTooltip(el)` works on any element — `<tr>`, `.card-header`, `.legend span`
- Title color is set via `getComputedStyle(el).color` so it auto-matches card accent in both themes

## LSP Keymaps (Neovim 0.10+ built-in defaults)
The Neovim-Specific card shows built-in defaults only — no custom config needed:
- `gd` go to definition, `grr` references, `gri` implementation, `grn` rename
- `gra` code action (NOT `<leader>ca` — that's a custom mapping)
- `gO` document symbols, `Ctrl+S` (Insert) signature help
- `K` hover docs, `]d`/`[d` next/prev diagnostic

## Google Analytics
Tag ID: G-KVMK7GTY9C
