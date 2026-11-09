# AGENTS.md — Portfolio

Single-file LUCIDA OS operator UI: the entire site is `index.html`
(~2,600 lines — markup + CSS + JS, terminal aesthetic with theme switcher).
No build step, no dependencies beyond Google Fonts.

## Conventions

- Edit `index.html` in place; keep it self-contained (no bundler, no framework).
- Verify by opening the file in a browser (or `vesta_station shot <file-url>`
  for a screenshot); there is no test suite.
- No MAINTENANCE.md needed (no known live service). If it ships to a public
  URL, add a DESIGN.md note or fold the design language in here.

## Facts

- This repo carries **no CI**: its only workflow is GitHub's generated Pages
  publisher (`dynamic/pages/pages-build-deployment`), which the API refuses to
  delete (404) and which the fleet's `ci` watch counts as a publisher, not a
  gate.
- Actions stay **enabled** here: with them off, the Pages build never runs —
  push-triggered and `POST /pages/builds` both queue and never complete
  (measured 2026-11-09). Pages build is `legacy`, source `main:/`, so a push
  to `main` publishes <https://0x923041-dotcom.github.io/portfolio/>.
- The boot sequence is ~1.7 s: the reveal runs 8 characters per 10 ms tick
  (`BOOT_CHARS_PER_TICK` / `BOOT_TICK_MS`) and the font stylesheet loads
  non-blocking — a pending stylesheet holds back script execution.
- SomaFM answers 403 to a non-browser User-Agent, and the first `play()`
  needs a user gesture. A blocked play is retried on the first
  pointerdown/keydown, the window says why, and a dead ice host walks the
  mirrors (`ice1` → `ice2` → `ice6`).
- The page sends `<meta name="referrer" content="no-referrer">`: SomaFM
  refuses some referrers (a `*.github.io` referer answers 403, the same
  request without one streams), and Chromium ignores
  `HTMLMediaElement.referrerPolicy` on a detached `new Audio()` — only the
  page policy applies.

*Written by Hermes — 2026-09-06 (stack-doc sweep).*
