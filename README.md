# rsunde.github.io

Ronnie Sunde's personal site — notes and guides, mostly in Swedish. Live at
**[rsunde.github.io](https://rsunde.github.io)**.

<!-- Custom domain retired 2026-08-19 — the domain lapsed, so the site serves from the
     github.io address instead. Previous line, kept for restoration:

     Ronnie Sunde's personal site — notes and guides, mostly in Swedish. Live at
     **[ronniesunde.com](https://ronniesunde.com)**.

     The CNAME file itself was moved, not deleted — see _archive/CNAME. -->


## What's here

| Path | Contents |
|---|---|
| `guides/` | Operating system privacy, browser security, file managers |
| `ai/` | LLM overview, running AI locally, AI-assisted programming |
| `index.md` | Homepage and hand-maintained nav — every new page needs a link added here |
| `_layouts/` | `default.html` (site base), `post.html` |
| `_archive/` | Retired content, kept in git but not published — see `_archive/README.md` |

## Local development

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000
```

Use `bundle exec` and the committed `Gemfile`, not a globally installed Jekyll. The `Gemfile`
pulls in the `github-pages` gem, which pins Jekyll and its plugins to what GitHub Pages actually
runs. That matters here: none of this site's Markdown has YAML front matter, so it renders only
because GitHub Pages force-enables `jekyll-optional-front-matter`, `jekyll-default-layout` and
`jekyll-titles-from-headings`. A plain `jekyll serve` produces different output than production.

## Deployment

Automatic, via GitHub Pages' classic build pipeline, on every push to `master`. There is no
GitHub Actions workflow and no build step in this repo.

The site serves from `rsunde.github.io`. Because that is a GitHub *user* site rather than a
project site, it is served from the domain root — so the absolute internal links used throughout
(`/ai`, `/guides/browsers`) resolve correctly without a `baseurl`. Restoring a custom domain
later means moving `_archive/CNAME` back to the root and pointing DNS at GitHub Pages.

## Notes

The site depends on assets served from a separate repo at
`https://rsunde.github.io/Websites__Static/` (jQuery, plus the bird/caterpillar animations and
the Konami-code easter egg wired up in `_layouts/default.html`).

Agent and contributor instructions live in [`AGENTS.md`](AGENTS.md).
