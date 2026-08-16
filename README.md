# rsunde.github.io

Ronnie Sunde's personal site — notes and guides, mostly in Swedish. Live at
**[ronniesunde.com](https://ronniesunde.com)**.

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
GitHub Actions workflow and no build step in this repo. The custom domain is set by `CNAME`.

## Notes

The site depends on assets served from a separate repo at
`https://rsunde.github.io/Websites__Static/` (jQuery, plus the bird/caterpillar animations and
the Konami-code easter egg wired up in `_layouts/default.html`).

Agent and contributor instructions live in [`AGENTS.md`](AGENTS.md).
