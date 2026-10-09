# AGENTS.md — hcmus-cs-ta.github.io

Org **root** GitHub Pages site (legacy branch deploy). Static HTML only. Live: <https://hcmus-cs-ta.github.io/>

## Commands

| Task | Command |
|---|---|
| Publish | `git push origin main` (goes live in ~1 min, no CI) |
| Preview | open `index.html` directly in a browser |

## Invariants (do not break)

1. **Any push to `main` publishes immediately** — never commit broken or half-finished HTML. Verify locally in a browser first.
2. `index.html` is the served landing page; `README.md` is repo docs only. GitHub's Jekyll processing is incidental — do not build content that depends on it.
3. Dependency-free pages only: inline CSS, system font stack, no external scripts, no trackers, no framework. This repo must stay trivially auditable.
4. **Never commit secrets** — this repo is fully public.
5. **Hierarchy (decided 2026-10-09)**: `index.html` (landing) exposes **course cards only**, and each card deep-links to that course's **main page inside the Lab Book** — the course home is owned by the book (its `myst.yml` binds each course group to a course page from the course's own repo). This repo holds **no course hubs**: the old `/intro-ds/index.html` hub was deleted in the same decision — never re-create HTML hubs here; course pages belong to the book.
6. Book content links follow the project-site pattern `/<repo-name>/...` (e.g. `/lab-book/intro-ds/`); they must match the book's URL config (`site.options.folders` in `lab-book/myst.yml`). If the book changes its URL scheme, update the landing links here in lockstep — a stale link is a broken front door.
7. Tracked course cards (2026-10-09): **Introduction to Data Science**, **Programming**, **AI Arena** — exactly the three Lab Book course groups. Adding a course = a course main page in the book first, then a landing card here linking to it.

## Cross-repo knowledge

- The Jupyter Book lives in `hcmus-cs-ta/lab-book` (MyST/JB2; repo **private**, its Pages site public by design). It includes three private submodules — `intro-ds`, `programming/problemset` and `arena` — fetched in CI by the unified `STATEMENTS_TOKEN` secret. See its `README.md` and `AGENTS.md` for build/deploy/auth.
- Statement content is owned by `hcmus-cs-ta/intro-ds` (private; canonical tex sources + converter CI; also owns the IntroDS course page `intro-ds/index.md`), `hcmus-cs-ta/hcmus-programming-exercise` (private; Programming course page + Regulations), and `hcmus-cs-ta/hcmus-ai-arena` (private; AI Arena statements, hand-transcribed from versioned statement PDFs). Never copy or fork course/book content into this repo — link to it.
- The navigation chain: landing (here) → book dashboard (`/lab-book/`) → course main page → course materials (IntroDS: project overview → three milestone pages).
