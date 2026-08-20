# GADA GROUP — Base44 dev environment

## What this is
A single self-contained `index.html` (Hebrew, RTL) — "GADA GROUP" order/role management app. All CSS and JS are inline; no build step, no backend, no framework.

## External services
- **Firebase Realtime DB** via public REST API (hardcoded URL `https://gada-2027-default-rtdb.europe-west1.firebasedatabase.app/orders`). No API key / no secrets — the URL is public and the app falls back to `localStorage` if Firebase is unreachable.
- Google Fonts (Heebo) and Google Maps search links — both public.

## How it runs here
- `docker-compose.base44.yml` runs a `node:22` container that installs Vite and serves the repo root as a static dev server on port 3000 with live reload.
- `vite.config.js` sets `server.host: true` and `allowedHosts: true` so the preview proxy hostname is accepted.
- No secrets are required to boot.

## Verify it works
```
docker compose -f docker-compose.base44.yml up -d --build
curl -sf -H "Host: external-preview.example.com" http://localhost:3000/   # should return the HTML
```
The login screen should render in the preview.
