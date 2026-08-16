# AGENTS.md

Single source of truth for **every** AI coding agent on this repository — Claude Code, OpenAI
Codex, Cursor, GitHub Copilot, Gemini CLI, Windsurf, Aider, etc. Edit **this** file; the
tool-specific files (`CLAUDE.md`, `GEMINI.md`, `.cursor/rules/`, `.github/copilot-instructions.md`,
`.windsurfrules`) are thin pointers that import or defer to it. Keep it concise — instructions,
not full docs.

---

## 1. Project Overview

- **rsunde.github.io** — Ronnie Sunde's personal Jekyll site/digital garden, served at the custom
  domain `ronniesunde.com` (via `CNAME`). Content: AI/programming notes, OS/browser/file-manager
  guides, and a short bookmarks page.
- **Stack**: Jekyll static site, served via GitHub's classic Pages build pipeline (no GitHub
  Actions workflow, no `Gemfile`/`Gemfile.lock` — Ruby/Jekyll versions are unpinned). Theme:
  `jekyll-theme-hacker` via `remote_theme: pages-themes/hacker@v0.2.0` (the `jekyll-remote-theme`
  plugin). `_config.yml` has a leftover comment referencing `jekyll-theme-architect` as an
  alternate — not the active theme.
- **Layout**:
  - `_layouts/` — `default.html` (active, hacker theme base), `post.html` (extends default, adds
    date/tags), `default_architect.html` (orphaned — leftover from the architect theme, not
    referenced by current front matter).
  - `ai/` — `index.md`, `aiprogramming.md`, `localai.md`.
  - `guides/` — `browsers.md`, `filemanagers.md`, `operatingsystems.md`.
  - `_archive/` — retired content, kept in git but **not published** (Jekyll skips top-level
    `_`-prefixed directories). Currently holds the whole former `programming/` section (11 pages)
    and `assets/images/` (7 NoSQL/SQL diagrams used only by its `database.md`). See
    `_archive/README.md` for the restore procedure.
  - `assets/css/` (`main.css`, `csharp.css`) — see §7; both are currently unreachable.
  - `index.md` — Swedish-language homepage/nav linking the sections above; `favorites.md` — a
    2-line bookmark list; `debug_glitch.html` — see §7.

---

## 2. Commands

```bash
# No Gemfile is pinned — install Jekyll/bundler globally and serve:
gem install bundler jekyll
bundle exec jekyll serve   # no committed port/flags — defaults to http://localhost:4000
```

Deploy is GitHub's legacy/classic Pages pipeline, auto-triggered on push to `master` — no GitHub
Actions workflow exists (`.github/` has no `workflows/`, only `copilot-instructions.md`), so
there's no in-repo build command to quote.

---

## 3. Architecture

Static Jekyll site rendering Markdown through `_layouts/default.html` (the remote "hacker"
theme) into HTML served at `ronniesunde.com`. New guide content goes in `guides/*.md`, AI notes
in `ai/*.md` — each new page needs a manual link added to `index.md`'s nav list (there's no
auto-generated index/collection). Retiring a page means moving it under `_archive/` (mirroring
its original path) and dropping its nav link, not deleting it. Shared CSS lives in
`assets/css/`. No database, no build-time templating beyond what Jekyll/Liquid does natively.

---

## 4. Conventions

- Write clean, modern, readable code. Prioritise readability and maintainability.
- Explain complex logic or significant architectural decisions.
- Keep markup semantic and assets organised.

---

## 5. Rules (non-negotiable — these override default agent behaviour)

No repo-specific rules today — generic agent-behaviour guidance (delegation, root-clutter,
deletion safety) lives once in `X:\git\rsunde\AGENTS.md` under "Agent-instructions standard →
Working style"; this repo has nothing beyond that estate-wide default.

---

## 6. Testing & Definition of Done

A feature isn't done when it compiles — it's done when it builds, tests pass, and the
docs/README reflect it.

- No test suite exists (static Jekyll site) — "done" means: `bundle exec jekyll build` (or
  `jekyll serve`) completes without errors and the new/changed page renders correctly, no new
  root-level clutter.

---

## 7. Do-not-touch / gotchas

- `debug_glitch.html` is a standalone dev/testing scratch page (a "Glitch the Caterpillar" mouse
  animation) that references `../Websites__Static/bird.css/js` and `caterpillar.css/js` — paths
  **outside this repo**, so it's broken/non-functional as committed. It's leftover local-testing
  content, not real site content; leave as-is unless asked to clean it up.
- `_site` (Jekyll's build output directory) is **not** in `.gitignore` — a local `jekyll
  serve`/`build` can leave generated artifacts untracked-but-unignored. Don't `git add` a `_site/`
  directory if one appears locally.
- The `programming/` section was archived on 2026-08-16 (moved to `_archive/programming/`, nav
  links removed from `index.md`). It was a mix of substantive pages (`testing.md`, `csharp_v6.md`,
  `method_keywords.md`, `database.md`) and stubs (`csharp_v7.md`/`csharp_v8.md` are 3-byte
  placeholders, `async.md` is a bare heading, `orm.md` is 87 bytes, `test.md` is an unexplained
  C# snippet). Don't re-add it to the nav without asking.
- `assets/css/main.css` and `csharp.css` are dead — `csharp.css` is commented out in
  `_layouts/default.html`, and both are only linked from the orphaned `default_architect.html`.
  `main.css` also styles `#main-content`, while the active layout uses `id="main_content"`.
- `_layouts/default_architect.html` is dead/orphaned — the active theme is `hacker`
  (`remote_theme` in `_config.yml`), not `architect`. Don't assume it's wired in.
- `_config.yml`'s `google_analytics: sdfgkj` looks like a placeholder/dummy tracking ID, not a
  real one — don't treat analytics as actually configured.
- No `Gemfile`/`Gemfile.lock` — Jekyll/Ruby versions are unpinned and unverified.
- A prior `AGENTS.md` existed and was explicitly deleted in a recent commit ("chore: Remove
  AGENTS.md file as it is no longer needed") before this file was regenerated — the pointer files
  (`.cursorrules`, `.windsurfrules`, copilot-instructions) had been left dangling in the interim,
  pointing at a file that didn't exist. This file closes that gap.
