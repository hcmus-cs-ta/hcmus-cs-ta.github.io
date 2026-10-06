# hcmus-cs-ta.github.io

Public pages for Teaching Assistant at CS department of FIT@HCMUS.

This is the **org root site**: the repository name matches `hcmus-cs-ta.github.io`, so its Pages deployment serves <https://hcmus-cs-ta.github.io/> directly — the front door that routes visitors to the individual course sites.

## How publishing works (different from the other repos!)

- **Legacy branch deploy**: whatever sits at the root of `main` **is** the site. Push = publish (~1 minute). There is no build workflow, no CI, nothing to wait for.
- `index.html` is the served landing page and takes precedence over the README render. `README.md` stays as repo-facing documentation and is not part of the site.

## Current content

- `index.html` — landing page: one card per course site with deep links into its key pages (currently the Lab Book card: overview + three milestone statements).

## Adding a new course site (extensibility)

1. The course book lives in its own repo (e.g. `hcmus-cs-ta/<course-book>`) with its own Pages deployment — a *project* site served at `https://hcmus-cs-ta.github.io/<repo-name>/`, which means its build must set `BASE_URL=/<repo-name>` (see `lab-book/deploy.yml` as the reference implementation).
2. Add a card to `index.html`: one prominent "open the book" link plus deep links to the pages students actually need.
3. Keep the HTML plain: inline styles, system fonts, zero external scripts. The landing must stay build-free and fast.
4. If the linked book ever changes its URL structure (toc/folders options), update the deep links here in the same commit discipline.
