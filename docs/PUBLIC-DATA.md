# ql-public-data — public documentation

This file is safe to commit in the **public** repository. Internal ops, tokens, and architecture rules live in the private monolith workspace (`docs/MONOREPO-*.md`, `ql-hub/docs/`), not here.

## Purpose

CDN-friendly JSON and static assets for tournament overlays and public pages. Served via jsDelivr after git push.

## Directory layout

- `index.json` — catalog root
- `schema/` — JSON schemas
- `tournaments/{slug}/` — per-event data
  - `meta.json`, `bracket.json`, `players.json`, …
  - `overlay-live.json` — live match fields for overlays
- `assets/overlay-logos/` — logo images
- `assets/overlay-logos.json` — logo catalog

## Privacy

- Do **not** publish `steam_id64` or other PII in committed JSON.
- No secrets, VPS addresses, or ingest tokens in this repo.

## Consumers

- **ql-stream-tools** `stream-overlay/` reads tournament JSON from CDN (transitioning to WebSocket for live fields — see private stream-tools docs).
- **ql-hub** publishes via `public_publish` (private hub code).

## Schema changes

Update files under `schema/` when JSON shape changes. Keep backward compatibility when possible for CDN caches.

## Editing

Local edit + push, or ql-hub «Publish public data» from operator environment.
