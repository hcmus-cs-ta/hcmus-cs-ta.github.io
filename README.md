# hcmus-cs-ta.github.io

Public pages for Teaching Assistant at CS department of FIT@HCMUS.

This is the **org root site**: the repository name matches `hcmus-cs-ta.github.io`, so its Pages deployment serves <https://hcmus-cs-ta.github.io/> directly — the front door that routes visitors to the individual course sites.

## How publishing works (different from the other repos!)

- **Legacy branch deploy**: whatever sits at the root of `main` **is** the site. Push = publish (~1 minute). There is no build workflow, no CI, nothing to wait for.
- `index.html` is the served landing page and takes precedence over the README render. `README.md` stays as repo-facing documentation and is not part of the site.

## Current content

The site is a strict two-layer router:

- `index.html` — **landing**: one card per **course**, nothing deeper. Currently one card: *Introduction to Data Science* → `/intro-ds/`.
- `intro-ds/index.html` — **course hub**: one card per course **section**. Currently: *Project* → `/lab-book/intro-ds/statement/` (the statements overview in the Lab Book). Future sections (Labs, Slides, ...) become sibling cards here.

Deep page links (milestones, statements) live **only at the third layer** — inside the book itself; the landing and hubs never link below section level.

## Adding a new course site (extensibility)

1. The course content lives in its own repo (e.g. `hcmus-cs-ta/<course-book>`) with its own Pages deployment — a *project* site served at `https://hcmus-cs-ta.github.io/<repo-name>/`, which means its build must set `BASE_URL=/<repo-name>` (see `lab-book/deploy.yml` as the reference implementation).
2. Add a **course card** to `index.html` linking to `/<course>/` — never to the book directly and never with deep links.
3. Create `/<course>/index.html` — the course hub — with one card per section; section cards may link into the book's content.
4. Keep the HTML plain: inline styles, system fonts, zero external scripts. Pages must stay build-free and fast.
5. If a linked book changes its URL structure (toc/folders options), update the affected hub links here in the same commit discipline.
