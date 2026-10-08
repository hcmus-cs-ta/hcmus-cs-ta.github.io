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
5. **Hierarchy is strict and must stay so**: `index.html` (landing) exposes **course cards only**; `/<course>/index.html` (course hub) exposes **section cards**; deep page links live only in the linked books, never on the landing or hubs. Adding a course = landing card + hub page; adding a course section = hub card only.
6. Book content links follow the project-site pattern `/<repo-name>/...` (e.g. `/lab-book/intro-ds/statement/`); they must match the book's URL config (`site.options.folders` in `lab-book/myst.yml`). If the book changes its URL scheme, update the hub links here in lockstep — a stale link is a broken front door.
7. **Path safety for `/intro-ds/`**: this hub path is safe only because the private `intro-ds` repo cannot enable its own Pages site on the org's free plan (private-repo Pages requires a paid plan). If the org plan or repo visibility ever changes, re-check for a project-site collision on that path.
8. Course cards currently on the landing: **Introduction to Data Science only** (decided 2026-10-06). The earlier "FAI — AI Arena" card was removed in the same decision — Programming and AI Arena stay reachable via the Lab Book until they get their own course hubs.

## Cross-repo knowledge

- The Jupyter Book lives in `hcmus-cs-ta/lab-book` (MyST/JB2; repo **private**, its Pages site public by design). It includes three private submodules — `intro-ds`, `programming/problemset` and `arena` — fetched in CI by the unified `STATEMENTS_TOKEN` secret. See its `README.md` and `AGENTS.md` for build/deploy/auth.
- Statement content is owned by `hcmus-cs-ta/intro-ds` (private; canonical tex sources + converter CI) and `hcmus-cs-ta/hcmus-ai-arena` (private; AI Arena statements, hand-transcribed from versioned statement PDFs). Never copy or fork statement pages into this repo — link to them.
- The AI Arena statements (from `hcmus-cs-ta/hcmus-ai-arena`, another submodule of lab-book) are reachable through the Lab Book; when AI Arena gets its own course hub, follow the hierarchy recipe in `README.md`.
