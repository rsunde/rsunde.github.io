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

Only 5 of the 7 diagrams were ever referenced; `nosqlgraph.png` and `nosqlgraph2.png` were
already orphaned before archiving.

## Restoring

Move the directories back and re-add the nav links to `index.md`:

```bash
git mv _archive/programming programming
git mv _archive/assets/images assets/images
```

The removed `index.md` nav block is recoverable from the commit that archived this content.
