# Reload Bench

A static, single-page tool. No build step and no server code: upload this folder as-is to any static host
(GitHub Pages, Netlify, Cloudflare Pages, itch.io as an HTML project, or your own web server).

## Files
- `index.html` – the whole app (HTML, CSS and JS in one file)
- `favicon.ico`, `favicon-16.png`, `favicon-32.png` – browser tab icons
- `apple-touch-icon.png` – iOS home-screen icon
- `icon-192.png`, `icon-512.png`, `site.webmanifest` – Android / install icons
- `og-image.png` – preview image for links shared on Discord, X, Slack, etc.
- `favicon.svg`, `reload-bench-logo.svg` – vector versions of the logo

Live at **https://joonas98.github.io/reload-bench/** (GitHub Pages, served from the `main` branch root).

## Notes
- Fonts load from Google Fonts. Without a connection the page falls back to system fonts and still works.
- Everything is synthesized locally in the visitor's browser; nothing is uploaded anywhere.
- Single exports download as `.wav`; batches of six download as one `.zip`.
