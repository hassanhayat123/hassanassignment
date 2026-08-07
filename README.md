# University Student Clubs Portal

A small, responsive informational website that introduces the student clubs of the
university and helps new students find and join the community that fits them.

Built as **DevOps Assignment 01 (Summer 2026)** to practise a real collaborative
Git + GitHub workflow: feature branches, pull requests, code review, `git rebase`,
conflict resolution, branch protection and release management.

---

## Team

| Sr # | Student Name | University Email | GitHub Username | Role | Branch Worked On |
|-----|--------------|------------------|-----------------|------|------------------|
| 1 | Hassan Hayat (L1F22BSCS0976) | l1f22bscs0976@ucp.edu.pk | hassanhayat123 | Team Lead | `main`, `develop`, `release/v1.0`, all `feature/*` |

> Submitted as a solo repository. The Team Lead performed every role in the
> workflow (initialisation, all five feature branches, reviews, release and
> production merge).

---

## Project Structure

```
student-portfolio/
│
├── .gitignore
├── README.md
├── src/
│   ├── index.html          # Home — landing page
│   ├── clubs.html          # Club categories
│   ├── events.html         # Upcoming events
│   ├── join.html           # How to join
│   └── highlights.html     # Club achievements
└── styles/
    └── style.css           # Single shared stylesheet
```

Every page links to the one shared stylesheet with `../styles/style.css`.

---

## Pages

| Page | Description | Responsibility |
|------|-------------|----------------|
| `index.html` | Landing page — introduces the portal, explains why clubs matter, links to every other page. | Team Lead |
| `clubs.html` | Club categories — Technology, Sports, Cultural and Debate societies. | Member 1 |
| `events.html` | Upcoming workshops, competitions, meetups and seminars. | Member 2 |
| `join.html` | Step-by-step guide to registering and joining a club. | Member 3 |
| `highlights.html` | Major achievements and notable accomplishments. | Member 4 |

---

## Branching Strategy

| Branch | Purpose | Protected |
|--------|---------|-----------|
| `main` | Production-ready code only. Receives merges from `release/*`. | Yes — PR required, **3** approvals |
| `develop` | Integration branch. All active development lands here. | Yes — PR required, **2** approvals |
| `release/v1.0` | QA / testing branch cut from `develop` before production. | No |
| `feature/<page-name>` | One short-lived branch per page, cut from `develop`. | No |

Flow:

```
feature/<page>  ──PR──▶  develop  ──cut──▶  release/v1.0  ──PR──▶  main
                            ▲                                        │
                            └──────────── sync PR ───────────────────┘
```

Before every merge a feature branch is brought up to date with:

```bash
git fetch origin
git rebase origin/develop
```

so the history stays linear and free of noise merge commits.

---

## Running Locally

No build step and no dependencies — it is plain HTML and CSS.

```bash
git clone https://github.com/hassanhayat123/hassanassignment.git student-portfolio
cd student-portfolio
open src/index.html
```

Or serve it:

```bash
python3 -m http.server 8000
```

then visit <http://localhost:8000/src/index.html>.

---

## Responsiveness

`styles/style.css` is mobile-friendly. Each page contributed at least one
media query; the shared breakpoints are:

| Breakpoint | Target |
|------------|--------|
| `max-width: 900px` | Tablets — navigation wraps, grids collapse to two columns |
| `max-width: 600px` | Phones — single column, larger tap targets, stacked navigation |

---

## Licence

Coursework submission for the University of Central Punjab. Not for redistribution.
