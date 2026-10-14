# WIP — ta-pages (org landing page)

Living tracker for THIS repo only: the org root site at <https://hcmus-cs-ta.github.io/>. Edited in place each turn (never appended), versioned with this repo.

Sibling trackers (each repo manages its own):
- `hcmus-cs-ta/lab-book` → `wip.md` (multi-course Jupyter Book: build/deploy)
- `hcmus-cs-ta/intro-ds` → `wip.md` (arXiv project statement content + IntroDS course page)
- `hcmus-cs-ta/hcmus-programming-exercise` → `wip.md` (programming course page + Regulations content)
- `hcmus-cs-ta/hcmus-ai-arena` → `wip.md` (AI Arena statements)
- `hcmus-cs-ta/hcmus-intro-it` → `wip.md` (IntroIT course page + project-statement transcription)
- `hcmus-cs-ta/hcmus-data-mining` → `wip.md` (Data Mining course page + exercise handouts + project statements)

## Components

| Component | Role | Status |
|---|---|---|
| `index.html` | **landing — course front door**: six cards deep-linking to each course's main page in the Course Lab Book — *Introduction to Data Science* → `/lab-book/intro-ds/`, *Programming Courses* → `/lab-book/programming/problemset/`, *Fundamentals of Artificial Intelligence* → `/lab-book/arena/statement/`, *Introduction to Information Technology* → `/lab-book/introit/`, *Data Mining and Applications* → `/lab-book/data-mining/`, *Introduction to Machine Learning* → `/lab-book/intro-ml/` (card names carry the full course names in the 2026-10-10 rename, fifth card added 2026-10-12, sixth 2026-10-14; the IntroIT copy swept to the 2026-10 verbal style rule — no dashes, parentheses, double quotes or semicolons); muted "all materials live in the Course Lab Book" note | live |
| `README.md` | org-root role, legacy push=deploy model, single-layer router description, course recipe (card list deduped into the AGENTS registry 2026-10-14) | renovated (2026-10-14) |
| `AGENTS.md` | publish invariants, rebuilt hierarchy (course pages live in the book; no HTML hubs), link conventions, course-card registry, cross-repo knowledge pointed at the lab-book canon | renovated (2026-10-14) |

## Docs-architecture round (2026-10-14)

Org principle applied (README = human overview, AGENTS = agent contract, wip =
tracker; duplicated facts owned by the most generic place): the README's
enumerated card list collapsed into a pointer at the `AGENTS.md` card registry
(invariant 7 stays the single card list); the `AGENTS.md` cross-repo section
dropped the restated submodule/auth facts in favor of pointers at the lab-book
`AGENTS.md`/`README.md`, which own all book-side truth since the normative
docs-architecture contract landed there (book commit `34f42fd`). Same round
renovated all five course repos' docs to the principle. Site content itself
unchanged.

## Publishing facts

- Legacy branch deploy: push to `main` publishes in ~1 minute; no CI. `index.html` takes precedence over the README render.
- Navigation chain: landing (here) → book dashboard (`/lab-book/`, card per course) → course main page (in the book, owned by the course repo) → course materials (IntroDS: project overview → three milestone pages; IntroIT: project description + exercises; Data Mining: practice exercises + three project statements; IntroML: term project overview → six checkpoint pages).

## Bind round (2026-10-14)

- Sixth card **Introduction to Machine Learning** added to `index.html` (after
  Data Mining), deep-linking `/lab-book/intro-ml/`; card copy in the 2026-10
  verbal style. The card went live after the lab-book deploy `38521397598`
  turned green with the `intro-ml` submodule, keeping the front door ahead of
  the back end. `AGENTS.md` registry updated to the six tracked courses.
- The old `/intro-ds/index.html` hub was deleted (decision 2026-10-09, no redirect): course main pages live only inside the book.

## Pending

- (none) Standing watch: if `lab-book` changes its URL scheme (toc/`folders` option), update the landing card links here in lockstep — a stale link is a broken front door.
