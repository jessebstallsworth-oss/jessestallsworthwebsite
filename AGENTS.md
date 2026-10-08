# Base44 Setup Notes

## Project type
Static single-page website. No build step, no backend, no package manager. The entire app is `index.html` (inline CSS + JS).

## Running
`docker compose -f docker-compose.base44.yml up -d` serves `index.html` via nginx on port 3000.

## No external credentials required
The GitHub Device Flow editor sign-in is optional and fully client-side — the user enters their own OAuth App client ID in the browser. No server-side secrets are needed to boot or preview the site.

## Editing
Changes to `index.html` require a browser refresh (no live-reload dev server; nginx serves static files). Use `reload_preview` after edits.
