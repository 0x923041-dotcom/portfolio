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

*Written by Hermes — 2026-09-06 (stack-doc sweep).*
