# Infinity Stone Works

Marketing website for **Infinity Stone Works**, a natural stone (granite, marble, quartz) company.
*Quality That Never Ends.*

Live site: https://infinitystoneworks.shop

## Overview

A static site made of plain HTML, one shared stylesheet and a small amount of JavaScript. There is no framework and no build step.

| Page | URL |
| --- | --- |
| Welcome | `/` |
| Our Curated Collection | `/collection/` |
| Homeowner Information | `/homeowner-information/` |
| Project Guide | `/homeowner-information/project-guide/` |
| Project Checklist | `/homeowner-information/project-guide/checklist/` |
| Care & Warranty | `/care-warranty/` |
| Photos | `/photos/` |
| Reviews | `/reviews/` |
| FAQ | `/faq/` |
| Contact Us | `/contact/` |
| Privacy Policy | `/privacy/` |
| Terms | `/terms/` |

## Project structure

```
index.html              Welcome page
<page>/index.html       One folder per page (pretty URLs, no .html)
css/style.css           Shared stylesheet (all design tokens live here)
js/                     Shared scripts
assets/                 Site images and data (e.g. assets/reviews/)
brand_assets/           Logo and color guide
SITE-INFO.md            Per-page content requirements
CLAUDE.md               Design and coding rules for the project
serve.mjs               Local dev server
screenshot.mjs          Screenshot helper (Puppeteer)
fetch-google-reviews.mjs  Refreshes the Google reviews JSON
```

## Conventions

- **Pretty URLs:** every page except Welcome lives in its own folder as `index.html`, so it works on any static host with no server config.
- **Root-relative paths:** all internal links and shared assets start with `/` (never `.html`, never page-relative), so they resolve at any folder depth.
- **Shared layout:** every page uses the same header, nav and footer.
- **Design tokens:** colors, spacing and type scale are CSS custom properties in `css/style.css`. The palette comes from `brand_assets/`.
- **Mobile-first** layouts, with no CSS framework.

## Running locally

Requires [Node.js](https://nodejs.org/).

```bash
npm install
npm run serve        # http://localhost:3000
```

Other scripts:

```bash
npm run screenshot     # capture page screenshots with Puppeteer
npm run fetch-reviews  # refresh Google reviews (see below)
```

### Refreshing Google reviews

Reviews are baked into a static JSON file, so visitors never trigger an API call.

1. Copy `.env.example` to `.env` and set `GOOGLE_PLACES_API_KEY` (never commit `.env`).
2. Run `npm run fetch-reviews`.
3. Commit the updated `assets/reviews/google-reviews.json`.

## Third-party services

- **Web3Forms:** contact form submissions
- **hCaptcha:** spam protection on the contact form
- **Cloudflare Web Analytics:** privacy-friendly analytics
- **Google Places API:** used only by the manual review-refresh script

## License

© Infinity Stone Works. All rights reserved.
