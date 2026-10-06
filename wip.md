# WIP — ta-pages (org landing page)

Living tracker for THIS repo only: the org root site at <https://hcmus-cs-ta.github.io/>. Edited in place each turn (never appended), versioned with this repo.

Sibling trackers (each repo manages its own):
- `hcmus-cs-ta/lab-book` → `wip.md` (Jupyter Book build/deploy)
- `hcmus-cs-ta/intro-ds` → `wip.md` (statement content)

## Components

| Component | Role | Status |
|---|---|---|
| `index.html` | landing page: "Jupyter Book — Lab Book" card → `/lab-book/`, plus deep links (statement overview + three milestone pages); "FAI — AI Arena" card → `/lab-book/arena/statement/` (overview link only, no deep links by design) | live (`7cb9d61`) |
| `README.md` | org-root role, legacy push=deploy model, `index.html` vs README precedence, recipe for adding course sites | shipped (`bac3945`) |
| `AGENTS.md` | publish invariants, dependency-free rule, no-secrets rule, link conventions | shipped (`bac3945`) |

## Publishing facts

- Legacy branch deploy: push to `main` publishes in ~1 minute; no CI. `index.html` takes precedence over the README render.
- Landing links must mirror the book's URL scheme (`/lab-book/intro-ds/statement/...`, folder URLs). Current links verified by fetch.

## Pending

- (none) Standing watch: if `lab-book` changes its URL scheme (toc/`folders` option), update the deep links here in lockstep — a stale landing link is a broken front door.
