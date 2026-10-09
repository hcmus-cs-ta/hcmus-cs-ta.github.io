# hcmus-cs-ta.github.io

Public pages for Teaching Assistant at CS department of FIT@HCMUS.

This is the **org root site**: the repository name matches `hcmus-cs-ta.github.io`, so its Pages deployment serves <https://hcmus-cs-ta.github.io/> directly — the front door that routes visitors to the individual course sites.

## How publishing works (different from the other repos!)

- **Legacy branch deploy**: whatever sits at the root of `main` **is** the site. Push = publish (~1 minute). There is no build workflow, no CI, nothing to wait for.
- `index.html` is the served landing page and takes precedence over the README render. `README.md` stays as repo-facing documentation and is not part of the site.

## Current content

The site is the **front door of the Lab Book** — one card per course; the card deep-links to the course's main *page inside the book* (`/lab-book/...`):

- *Introduction to Data Science* → `/lab-book/intro-ds/` (course home; from there: the arXiv project overview → three milestone pages)
- *Programming* → `/lab-book/programming/problemset/` (course home)
- *AI Arena* → `/lab-book/arena/statement/` (statements overview)
- *Introduction to Information Technology* → `/lab-book/introit/` (course home; from there: the course project description)

Course main pages live **only inside the book** (owned by the course repos, bound in `lab-book/myst.yml`); the old `/intro-ds/` HTML hub was deleted on 2026-10-09. This repo stays a single-layer router.

## Adding a new course (extensibility)

1. The course content lives in its own repo (e.g. `hcmus-cs-ta/<course-repo>`) and is bound into `hcmus-cs-ta/lab-book` as a private submodule; the build sets `BASE_URL=/<repo-name>` (see `lab-book/deploy.yml` as the reference implementation).
2. Give the course a **main page** inside the book (first child of its `myst.yml` toc group; `intro-ds/index.md` is the reference pattern).
3. Add a **course card** to `index.html` here linking to that course page — never deeper.
4. Keep the HTML plain: inline styles, system fonts, zero external scripts. Pages must stay build-free and fast.
5. If the book changes its URL structure (toc/`folders` options), update the affected links here in the same commit discipline.
