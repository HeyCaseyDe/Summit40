# AGENTS.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview
This is a static single-page landing page for Laura's 40th birthday trip to Zion National Park. The site invites 5 couples to join the celebration, showcases the property and potential activities, and tracks RSVPs.

## Architecture
The project is a pure HTML/CSS static website with no build process:
- `index.html`: Single-page application with hero, details, property, adventures, and RSVP sections
- `styles.css`: Complete styling with CSS variables, responsive design, and topographic pattern overlays
- `Logo-Summit-40.png`: Main logo used in hero and footer
- `Topographic-Map-Pattern-7.png`: Background texture pattern referenced in CSS via `--topo-pattern` variable

The design uses a nature-inspired color palette (teal `#2C5F5D`, sage `#8B9E7D`, orange `#D85A3A`, cream `#F4EDE4`) with typography from Google Fonts (Playfair Display for headings, Libre Franklin for body text).

## Development Commands
Since this is a static site with no dependencies, there are no build, test, or lint commands. To preview locally:

```zsh
# Option 1: Python simple server
python3 -m http.server 8000

# Option 2: Node's http-server (if installed)
npx http-server -p 8000
```

Then open http://localhost:8000 in a browser.

## Deployment to Railway
This site is intended for Railway deployment. To deploy:

1. Ensure git repository is initialized and committed
2. Create a `package.json` with a start script for Railway:
```json
{
  "name": "summit-40-landing",
  "version": "1.0.0",
  "scripts": {
    "start": "npx serve -s . -p ${PORT:-3000}"
  }
}
```
3. Deploy via Railway CLI (`railway up`) or connect GitHub repo in Railway dashboard

Railway will automatically detect the static site and serve it using the start script.

## Content Updates
RSVP statuses are hardcoded in `index.html` (lines 204-225). To update guest status, edit the `<span>` class from `pending` to `confirmed` and update the text accordingly.
