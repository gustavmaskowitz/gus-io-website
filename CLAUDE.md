# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static personal portfolio/contact page for gus.io (Gustav Maskowitz). Single-page site with terminal-style UI.

Pure static HTML/CSS - no JavaScript, no build process, no dependencies.

## Structure

```
/
├── index.html                      # Main entry point (~3KB)
├── 404.html                        # Error page (~1KB)
├── CLAUDE.md                       # Documentation for Claude Code
└── gus-io-web/
    ├── vapor-complete.css          # Full CSS source (~13KB)
    ├── vapor-complete.min.css      # Minified production CSS (~11KB)
    ├── fonts/                      # Self-hosted Roboto fonts (~38KB total)
    │   ├── roboto-regular-latin.woff2
    │   ├── roboto-regular-latin-ext.woff2
    │   ├── roboto-mono-regular-latin.woff2
    │   └── roboto-mono-regular-latin-ext.woff2
    └── [images]                    # Favicon + social icons (~13KB total)
```

**Total site weight: ~60KB** (down from 360KB with Vue.js bundle)

## Architecture

100% static HTML/CSS with self-hosted fonts - no external dependencies, no JavaScript.

The site displays:
- Terminal window with macOS-style stoplight decoration
- Personal info formatted as JSON
- Social media link cards (GitHub, Twitter, LinkedIn, Medium, YouTube)

**Key files:**
- `vapor-complete.css` - Complete CSS with all component styles and @font-face declarations
- `vapor-complete.min.css` - Production-ready minified CSS (used by HTML)
- `fonts/` - Self-hosted Roboto and Roboto Mono with font-display: swap

**CSS Architecture:**
Uses Vapor CSS framework naming conventions:
- `.vapor-app` - Base layout and responsive containers
- `.vapor-terminal` - Terminal window with macOS stoplights
- `.vapor-card` - Social media card component
- `.vapor-contribute` - Card grid layout
- Responsive breakpoints: 420px, 600px, 768px, 1050px

## Development

**Preview the site:**
```bash
python3 -m http.server 8000
# Visit http://localhost:8000
```

**Edit content:** Modify `index.html` directly (lines 24-29 contain the personal info JSON)

**Update styles:**
1. Edit `gus-io-web/vapor-complete.css`
2. Regenerate minified version:
   ```bash
   cat vapor-complete.css | tr -d '\n' | sed 's/  */ /g' | sed 's/ *{ */{/g' | sed 's/ *} */}/g' > vapor-complete.min.css
   ```

No build process required - all assets are ready to deploy.
