# AGENTS.md

This repository is the Rumchester Jekyll site. Debbie is an experienced software engineer who may be using coding agents for the first time. Treat her as technical, but make agent behavior explicit: state assumptions, name files changed, and verify the build before claiming work is done.

## Site Goals

- Keep the site simple, static, and easy to edit directly in GitHub.
- Prefer Jekyll data files and Markdown over adding JavaScript.
- Preserve the existing `CNAME` file unless Debbie explicitly asks to change the domain.
- Keep content changes understandable to a non-agent reviewer reading the diff.

## Editable Content Map

- `_config.yml`: site title, tagline, description, Instagram URL, and default logo path.
- `index.md`: homepage copy, hero summary, story text, button labels, and principle chips.
- `_data/events.yml`: event cards. Each event has `title`, `description`, `start_time`, `image`, and `location`.
- `_data/gallery.yml`: gallery cards. Each item has `title`, `image`, and `alt`.
- `_data/navigation.yml`: header navigation labels and anchors.
- `assets/images/`: logos, gallery images, and section artwork.
- `assets/css/variables.css`: colors, font stacks, sizing tokens, radius, and shadows.
- `assets/css/site.css`: layout and component CSS.

## Build And Verification

Use Ruby/Bundler for local validation:

```bash
bundle install
bundle exec jekyll build
```

If dependencies are already installed, `bundle exec jekyll build` is enough.

Before finishing a change:

- Run `bundle exec jekyll build`.
- Inspect `git diff --stat` and the relevant diff hunks.
- Confirm no generated `_site/`, `.jekyll-cache/`, or temporary files are staged.
- For image changes, confirm paths referenced in YAML or Markdown exist under `assets/images/`.

## Working With Agents

Good agent prompts for this repo are specific and bounded. Examples:

- "Add one event to `_data/events.yml` and run the Jekyll build."
- "Update the homepage story copy in `index.md` without changing layout CSS."
- "Replace the gallery image references in `_data/gallery.yml`; do not change the design."
- "Adjust only colors in `assets/css/variables.css` and summarize the visual impact."

For larger work, ask the agent for a short plan first, then let it implement after the plan looks right. For example:

```text
Please propose a small plan to add a sponsors section to the Rumchester Jekyll site. Keep it editable through `_data/sponsors.yml`; do not implement yet.
```

When reviewing agent output, check:

- Did it change only the files it said it changed?
- Did it keep editable data in `_data/` or Markdown?
- Did it run `bundle exec jekyll build`?
- Did it avoid committing generated files?
- Did it explain any assumptions or tradeoffs?

## Code Style

- Use plain HTML/Liquid templates and CSS. Avoid framework dependencies unless Debbie explicitly asks for them.
- Use semantic HTML and useful `alt` text for content images.
- Keep CSS variables in `assets/css/variables.css`; use them from `assets/css/site.css`.
- Keep cards and buttons at `8px` border radius through `--radius`.
- Prefer short comments only when they help future editors.

## Pull Request Expectations

PR summaries should include:

- What changed.
- Which files Debbie should edit later.
- How the change was verified.
- Any follow-up decisions needed from Debbie.

Do not merge or deploy destructive changes automatically. If a change affects the domain, GitHub Pages settings, repository visibility, or secrets, stop and ask Debbie/Kyle for explicit approval.
