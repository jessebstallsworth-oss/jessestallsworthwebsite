# Base44 Dev Environment

## Project Type
Static HTML website (no build step, no package manager). Single-page app using hash-based routing (`#/about`, `#/experience`, etc.) with inline CSS/JS in `index.html` and data in `site-data.js`.

## Setup
- Served by `docker-compose.base44.yml` using `python:3.12-slim` running `http.server` on port 80 (mapped to host 3000).
- The repo directory has restrictive permissions (700), so nginx's non-root worker gets 403 — Python's `http.server` runs as root and works.
- No dependencies to install; source is bind-mounted read-only. Edits to HTML/JS are visible on browser refresh (call `reload_preview` after changes since there's no live-reload dev server).

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` should return 200.
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/site-data.js` should return 200.
- In the preview, check `#app` has children, `#nv` has nav links, and `#proof-carousel` has 5 slides.
- Navigate to `#/experience`, `#/teaching`, `#/projects` via `window.location.hash` to verify each route renders.

## Key Files
- `index.html` — all markup, CSS, and the rendering/router JS (references globals from `site-data.js`).
- `site-data.js` — defines `DEF`, `BIO`, `TEACHING_COURSES`, `TEACHING_ROLES`, `CAPSTONE_URL`, `GL`, `ADD` before the inline script runs.
- `assets/` — portrait and career-highlight images.
