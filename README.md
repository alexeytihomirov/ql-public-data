# ql-public-data

Public tournament assets, JSON schemas, and CDN-friendly static files for Quake Live events.

Published to GitHub and served via jsDelivr (`HUB_PUBLIC_CDN_BASE` in ql-hub).

## Layout

- `index.json` — catalog root
- `schema/` — JSON schemas
- `tournaments/{slug}/` — per-event data
  - `meta.json`, `bracket.json`, `players.json`, …
  - `overlay-live.json` — live match popups for OBS stream overlay (updated on ingest)
- `assets/overlay-logos/` — tournament logo images
- `assets/overlay-logos.json` — logo catalog for stream overlay picker

## Stream overlay

[ql-stream-tools](https://github.com/alexeytihomirov/ql-stream-tools) polls:

- `tournaments/{slug}/overlay-live.json`
- `assets/overlay-logos.json`

No HTTP access to QL Hub from streamers.

## Editing

Edit locally or via ql-hub «Publish public data» (git push with deploy key).

Logos: add PNG/SVG to `ql-hub/hub/app/static/overlay-logos/` — hub syncs them here on publish.
