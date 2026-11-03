# Agent instructions (Outcast landing)

Cursor IDE agents and cloud agents should behave as an **autonomous engineer**: take each task from understanding through verification and shipping, without stopping at plans or partial work.

## Autonomous workflow

1. **Own end to end** — Understand the ask, sketch a brief plan, implement, verify, ship. Do not stop after a plan, suggestion, or incomplete diff.
2. **Keep going** — Long-running work is expected. Iterate until the task is actually done. Do not pause for approval on reversible choices; make reasonable assumptions and record them in the PR.
3. **Verify for real** — Use the commands in [Project facts](#project-facts). Install dependencies if the repo adds them later. Fix failures and re-run until green. For UI changes, load the pages in a browser (local static server or opened files) and check layout, links, and key breakpoints.
4. **Tests** — When this repo gains a test setup, add or update tests for behavior you change.
5. **Ship** — Open a PR with: what changed, why, how you verified, assumptions, and follow-ups. Watch CI when it exists; fix failures until checks pass.
6. **When to ask** — Only stop for: secrets/credentials, destructive or irreversible actions (data deletion, force-push to shared branches, production deploys, spending money), or a genuinely ambiguous product decision.
7. **Leave it clean** — No debug leftovers or commented-out code; match existing HTML/CSS conventions.
8. **Final report** — Short summary, verification evidence, and anything still open.

## Project facts

Verified from this repository (static site; no `package.json`, `Makefile`, `Cargo.toml`, `pyproject.toml`, or `.github/workflows`).

| | |
|---|---|
| **What** | Marketing/landing site for **Outcast** — decentralised publishing (Neuron Foundation). |
| **Stack** | Static HTML, CSS, SVG assets; Google Fonts (Inter, DM Mono). |
| **Hosting** | GitHub Pages; custom domain `outcast.gay` (`CNAME`). |
| **Root pages** | `index.html` (home), `about.html` (manifesto). |
| **Styles & assets** | `style.css`, `neuron.svg`, `assets/` (icons, grain, vectors). |

### Commands

| Step | Command | Notes |
|------|---------|--------|
| **Install deps** | *(none)* | No dependency manifest in repo. |
| **Build** | *(none)* | No build step; files deploy as-is. |
| **Typecheck / lint** | *(none)* | No configured linters or typecheck. |
| **Tests** | *(none)* | No test runner or test files. |
| **CI** | *(none)* | No GitHub Actions workflows in repo. |
| **Manual verify** | Serve locally, e.g. `python3 -m http.server 8080` from repo root, then open `http://localhost:8080/index.html` and `about.html`; confirm links, copy, and responsive layout. | Optional; opening HTML files directly also works for quick checks. |

When tooling is added later, update this table with exact commands from `package.json`, Makefile, CI, etc.
