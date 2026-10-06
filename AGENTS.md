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
5. Book links follow the project-site pattern `/<repo-name>/` (e.g. `/lab-book/`); deep links use the book's folder URLs (e.g. `/lab-book/intro-ds/statement/crawling`).
6. Deep links must match the linked book's URL config (`site.options.folders` in `lab-book/myst.yml`). If the book changes its URL scheme, update `index.html` in lockstep — a stale landing link is a broken front door.

## Cross-repo knowledge

- The Jupyter Book lives in `hcmus-cs-ta/lab-book` (MyST/JB2, includes the private `intro-ds` submodule) — see its `README.md` and `AGENTS.md` for build/deploy/auth.
- Statement content is owned by `hcmus-cs-ta/intro-ds` (private; canonical tex sources + converter CI). Never copy or fork statement pages into this repo — link to them.
