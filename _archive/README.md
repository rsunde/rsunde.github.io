# _archive

Retired site content. Kept in git, **not published**.

Jekyll treats any top-level directory whose name starts with `_` as special and does not copy
it into `_site`, so nothing under here is built or served — no `exclude:` entry in `_config.yml`
is needed (and adding one would override Jekyll's default exclude list, so don't).

The tree here mirrors the site tree it came from, and the files are byte-identical to what was
published. Nothing was edited on the way in — the `/assets/images/...` paths inside
`programming/database.md` are the original absolute site paths, so a restore is a pure move with
no content changes.

## Contents

| Archived | Why |
|---|---|
| `programming/` (11 pages) | The whole Programmering section, retired 2026-08-16. |
| `assets/images/` (7 PNGs) | SQL/NoSQL diagrams used only by `programming/database.md`. |
| `assets/css/` (2 files) | Dead stylesheets, only ever linked from the architect layout. |
| `_layouts/default_architect.html` | Orphaned layout from the abandoned architect theme. |
| `ai/aiprogramming.md` | Retired 2026-08-16 — see below. |
| `CNAME` | Custom domain `ronniesunde.com`, retired 2026-08-19 when the domain lapsed. |

`CNAME` is here rather than commented out in place because a CNAME file has no comment syntax —
GitHub Pages reads the entire file as the hostname. Moving it is the only way to disable the
custom domain without discarding the value. Restore with `git mv _archive/CNAME CNAME`, but only
once the domain resolves to GitHub Pages again; a CNAME pointing at dead DNS takes the site down.

`ai/aiprogramming.md` was not merely stale. Its ranking table's primary column was
self-declared placeholder data (*"Denna kolumn innehåller platshållare"*), one row's Elo was
labelled `GISSAD`, and the "Open Source Modell" column named models that do not exist
(`Gemma-2.5`, `Gemma-2.0-Flash`, `Gemma-1.5`, `DeepSeek-Coder-R1`). Kept for the record only —
**do not restore it to the site.** Its handful of accurate points now live in `ai/index.md`
and `ai/localai.md`.

Only 5 of the 7 diagrams were ever referenced; `nosqlgraph.png` and `nosqlgraph2.png` were
already orphaned before archiving.

## Restoring

Move the directories back and re-add the nav links to `index.md`:

```bash
git mv _archive/programming programming
git mv _archive/assets/images assets/images
```

The removed `index.md` nav block is recoverable from the commit that archived this content.
