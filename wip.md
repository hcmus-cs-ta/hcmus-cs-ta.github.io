# WIP — ta-pages (org landing page)

Living tracker for THIS repo only: the org root site at <https://hcmus-cs-ta.github.io/>. Edited in place each turn (never appended), versioned with this repo.

Sibling trackers (each repo manages its own):
- `hcmus-cs-ta/lab-book` → `wip.md` (multi-course Jupyter Book: build/deploy)
- `hcmus-cs-ta/intro-ds` → `wip.md` (arXiv project statement content)
- `hcmus-cs-ta/hcmus-programming-exercise` → `wip.md` (programming problems + Regulations content)
- `hcmus-cs-ta/hcmus-ai-arena` → `wip.md` (AI Arena statements)

## Components

| Component | Role | Status |
|---|---|---|
| `index.html` | **landing — course cards only**. One card: *Introduction to Data Science* → `/intro-ds/`. (The flat Lab Book card and the FAI — AI Arena card were removed in the hierarchy restructure, by decision 2026-10-06.) | live |
| `intro-ds/index.html` | **course hub** — section cards. One card: *Project* → `/lab-book/intro-ds/statement/` (statements overview). Future sections (Labs, Slides, ...) become sibling cards. | live |
| `README.md` | org-root role, legacy push=deploy model, two-layer router description, course-site recipe | shipped |
| `AGENTS.md` | publish invariants, hierarchy invariants, path-safety note, link conventions | shipped |

## Publishing facts

- Legacy branch deploy: push to `main` publishes in ~1 minute; no CI. `index.html` takes precedence over the README render.
- Hierarchy: landing (courses) → hub (sections) → book pages (deep links only inside the book).
- `/intro-ds/` hub path is safe: the private intro-ds repo cannot enable its own Pages on the org's free plan.

## Pending

- (none) Standing watch: if `lab-book` changes its URL scheme (toc/`folders` option), update the hub links here in lockstep — a stale link is a broken front door.
