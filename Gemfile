source "https://rubygems.org"

# The `github-pages` gem pins Jekyll and every plugin to exactly the versions
# GitHub Pages' classic build runs server-side. That matters here more than
# usual: none of this site's Markdown has YAML front matter, so it only renders
# because GH Pages force-enables jekyll-optional-front-matter,
# jekyll-default-layout and jekyll-titles-from-headings — and _layouts/default.html
# calls {% seo %}, which needs jekyll-seo-tag.
#
# Install plain Jekyll instead of this and a local build silently produces
# different output than production: front-matter-less pages get copied verbatim
# rather than rendered, and {% seo %} raises an unknown-tag error.
gem "github-pages", group: :jekyll_plugins

# Windows and JRuby ship no zoneinfo files.
gem "tzinfo-data", platforms: [:mingw, :x64_mingw, :mswin, :jruby]

# Faster directory watching for `jekyll serve` on Windows.
gem "wdm", "~> 0.1", platforms: [:mingw, :x64_mingw, :mswin]
