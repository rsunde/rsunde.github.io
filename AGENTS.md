# AGENTS.md

Single source of truth for **every** AI coding agent on this repository — Claude Code, OpenAI
Codex, Cursor, GitHub Copilot, Gemini CLI, Windsurf, Aider, etc. Edit **this** file; the
tool-specific files (`CLAUDE.md`, `GEMINI.md`, `.cursor/rules/`, `.github/copilot-instructions.md`,
`.windsurfrules`) are thin pointers that import or defer to it. Keep it concise — instructions,
not full docs.

---

## 1. Project Overview

- **rsunde.github.io** — Ronnie Sunde's personal Jekyll site/digital garden, served at the custom
  GitHub Pages address `rsunde.github.io`. Content: three opinionated guides (OS privacy, browser
  privacy, file managers), two AI notes (concepts, running models locally), and a short bookmarks
  page. All prose is Swedish. As of 2026-08-16 every page has been rewritten to the rot-proof
  standard in §4 — read that before adding content.
- **Stack**: Jekyll static site, served via GitHub's classic Pages build pipeline (no GitHub
  Actions workflow). A `Gemfile` pins the `github-pages` gem so local builds match production —
  see §2 and §7. Theme: `jekyll-theme-hacker` via `remote_theme: pages-themes/hacker@v0.2.0`
  (the `jekyll-remote-theme` plugin).
- **Layout**:
  - `_layouts/` — `default.html` (active, hacker theme base), `post.html` (extends default, adds
    date/tags).
  - `ai/` — `index.md` (durable concepts: parameters, quantisation, memory arithmetic, how to
    choose a model) and `localai.md` (practice: tools, hardware, local endpoints). Deliberately
    contain no prices, leaderboard scores or model version numbers — those rot; see §7.
  - `guides/` — `browsers.md`, `filemanagers.md`, `operatingsystems.md`.
  - `_archive/` — retired content, kept in git but **not published** (Jekyll skips top-level
    `_`-prefixed directories). Holds the former `programming/` section (11 pages), its
    `assets/images/` diagrams, the dead `assets/css/`, the orphaned
    `_layouts/default_architect.html`, and `ai/aiprogramming.md`. See `_archive/README.md` for
    the restore procedure — and note that `ai/aiprogramming.md` is flagged do-not-restore.
  - `index.md` — Swedish-language homepage/nav linking the sections above; `favorites.md` — a
    2-line bookmark list; `debug_glitch.html` — see §7.
  - The repo ships **no CSS of its own** — all styling comes from the remote hacker theme.

---

## 2. Commands

```bash
bundle install
bundle exec jekyll serve   # no committed port/flags — defaults to http://localhost:4000
```

**Always use `bundle exec` with the committed `Gemfile`** — never a globally installed Jekyll.
The `Gemfile` pulls in the `github-pages` gem, which pins Jekyll and its plugin set to what the
Pages build actually runs. Plain Jekyll silently renders this site *differently* — see §7.

Deploy is GitHub's legacy/classic Pages pipeline, auto-triggered on push to `master` — no GitHub
Actions workflow exists (`.github/` has no `workflows/`, only `copilot-instructions.md`), so
there's no in-repo build command to quote.

---

## 3. Architecture

Static Jekyll site rendering Markdown through `_layouts/default.html` (the remote "hacker"
theme) into HTML served at `rsunde.github.io`. New guide content goes in `guides/*.md`, AI notes
in `ai/*.md` — each new page needs a manual link added to `index.md`'s nav list (there's no
auto-generated index/collection). Retiring a page means moving it under `_archive/` (mirroring
its original path) and dropping its nav link, not deleting it. All styling comes from the remote
theme — the repo ships no CSS. No database, no build-time templating beyond Jekyll/Liquid.

---

## 4. Conventions

- Keep markup semantic and assets organised.

**Content is written to be rot-proof.** This site is not maintained on a schedule, so pages must
stay true without edits. Every defect found in the 2026-08-16 audit lived in the same construct: a
table of perishable facts. Therefore:

- **Don't** add prices, model version numbers, leaderboard scores, "current version" tables, or
  hardware/OS compatibility matrices. Link to the live source instead and let the reader look.
- **Do** write concepts, trade-offs, criteria and opinions — the parts that were still accurate
  after two years untouched.
- Prefer arithmetic a reader can apply (`params × bytes-per-weight`) over a snapshot of results.
- Name product or model *families*, not versions — families last years, versions last months.
- **Never publish a placeholder.** If a figure isn't known, omit the claim. Do not ship a table
  with invented values and a note telling the reader to go fetch the real ones.
- Content is Swedish; keep the existing direct, opinionated voice. Match the page you're editing.

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
- **No page in this repo has YAML front matter** — not `index.md`, not any content page. Only
  `_layouts/post.html` does. This is load-bearing, not an oversight to "fix": the site renders
  because GitHub Pages force-enables `jekyll-optional-front-matter` (renders front-matter-less
  Markdown at all), `jekyll-default-layout` (assigns `default`) and `jekyll-titles-from-headings`
  (title from the first `#`), and `_layouts/default.html` calls `{% seo %}` from `jekyll-seo-tag`.
  A plain `jekyll serve` without the `github-pages` gem copies those pages verbatim instead of
  rendering them, and errors on `{% seo %}`. Hence the `Gemfile` — always `bundle exec`.
  Adding front matter to pages is fine, but don't do it *believing the site is broken without it*.
- **The custom domain `ronniesunde.com` was retired on 2026-08-19** — it lapsed. The site now
  serves from `rsunde.github.io`. The `CNAME` file was moved to `_archive/CNAME`, not deleted,
  because a CNAME file has **no comment syntax**: GitHub Pages reads the whole file as the domain,
  so a `#`-prefixed line would be parsed as a hostname. Moving it is the only way to disable it
  while keeping the value. Do not recreate a root `CNAME` unless the domain is live again and its
  DNS points at GitHub Pages — a `CNAME` for a domain that doesn't resolve breaks the site.
- Because `rsunde.github.io` is a GitHub **user** site, it is served from the domain root, so the
  absolute internal links (`/ai`, `/guides/browsers`) work with no `baseurl`. Don't add one.
- Don't add an `exclude:` key to `_config.yml` to hide `_archive/` — Jekyll's `exclude` **replaces**
  its default list (`Gemfile`, `vendor/`, `node_modules`, …) rather than extending it. The
  leading underscore already keeps `_archive/` out of the build.
- The `programming/` section was archived on 2026-08-16 (moved to `_archive/programming/`, nav
  links removed from `index.md`). It was a mix of substantive pages (`testing.md`, `csharp_v6.md`,
  `method_keywords.md`, `database.md`) and stubs (`csharp_v7.md`/`csharp_v8.md` are 3-byte
  placeholders, `async.md` is a bare heading, `orm.md` is 87 bytes, `test.md` is an unexplained
  C# snippet). Don't re-add it to the nav without asking.
- Cleaned up 2026-08-16, all archived rather than deleted: `assets/css/{main,csharp}.css` (dead —
  only ever linked from the orphaned architect layout), `_layouts/default_architect.html`
  (leftover from the architect theme, never wired into the active `hacker` one), and the
  commented-out dead markup in `_layouts/default.html`. The dummy `google_analytics: sdfgkj`
  was removed from `_config.yml` — there is **no analytics on this site**, by choice.
- `_config.yml` carries both `theme: jekyll-theme-hacker` and `remote_theme:
  pages-themes/hacker@v0.2.0`. Redundant but harmless — `remote_theme` wins. Left alone
  deliberately; changing it alters rendering and there's no local build here to verify against.
- A prior `AGENTS.md` existed and was explicitly deleted in a recent commit ("chore: Remove
  AGENTS.md file as it is no longer needed") before this file was regenerated — the pointer files
  (`.cursorrules`, `.windsurfrules`, copilot-instructions) had been left dangling in the interim,
  pointing at a file that didn't exist. This file closes that gap.
