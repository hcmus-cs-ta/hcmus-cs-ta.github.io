# WIP — ta-pages (org landing page)

Living tracker for THIS repo only: the org root site at <https://hcmus-cs-ta.github.io/>. Edited in place each turn (never appended), versioned with this repo.

Sibling trackers (each repo manages its own):
- `hcmus-cs-ta/lab-book` → `wip.md` (multi-course Jupyter Book: build/deploy)
- `hcmus-cs-ta/intro-ds` → `wip.md` (arXiv project statement content + IntroDS course page)
- `hcmus-cs-ta/hcmus-programming-exercise` → `wip.md` (programming course page + Regulations content)
- `hcmus-cs-ta/hcmus-ai-arena` → `wip.md` (AI Arena statements)

## Components

| Component | Role | Status |
|---|---|---|
| `index.html` | **landing — course front door**: three cards deep-linking to each course's main page in the Lab Book — *IntroDS* → `/lab-book/intro-ds/`, *Programming* → `/lab-book/programming/problemset/`, *AI Arena* → `/lab-book/arena/statement/`; muted "all materials live in the lab book" note | live |
| `README.md` | org-root role, legacy push=deploy model, single-layer router description, course recipe | shipped (2026-10-09) |
| `AGENTS.md` | publish invariants, rebuilt hierarchy (course pages live in the book; no HTML hubs), link conventions, course-card registry | shipped (2026-10-09) |

## Publishing facts

- Legacy branch deploy: push to `main` publishes in ~1 minute; no CI. `index.html` takes precedence over the README render.
- Navigation chain: landing (here) → book dashboard (`/lab-book/`, card per course) → course main page (in the book, owned by the course repo) → course materials (IntroDS: project overview → three milestone pages).
- The old `/intro-ds/index.html` hub was deleted (decision 2026-10-09, no redirect): course main pages live only inside the book.

## Pending

- (none) Standing watch: if `lab-book` changes its URL scheme (toc/`folders` option), update the landing card links here in lockstep — a stale link is a broken front door.
