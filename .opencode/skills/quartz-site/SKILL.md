---
name: Quartz Site
description: Edit this repository's Quartz 5 and GitHub Pages website, including posts-only publishing, Adwaita Flexoki styling, RIDIBatang, and hidden frontmatter.
---

# Chillbok Quartz website

## Repository boundaries

- This repository publishes the root site at `https://chillbok.github.io/`.
- The FPS documentation site is a separate project site. Do not edit its vault or deployment config when working here.
- `posts/` is the only publishing source. The workflow syncs its files and subfolders into Quartz's `content/`; Markdown elsewhere in this repository is not published.
- `posts/index.md` becomes the homepage. Keep private or unfinished notes outside `posts/` unless the user explicitly asks to publish them.

## Frontmatter

- Keep `@quartz-community/note-properties` enabled in `.publish/quartz.config.yaml` so YAML frontmatter is parsed as metadata.
- Keep `hidePropertiesView: true`: frontmatter drives page titles and metadata but must not render as a visible properties panel or raw text.
- Do not remove YAML frontmatter from posts just to hide it.

## Theme and layout

- Palette and Quartz plugins are configured in `.publish/quartz.config.yaml`; custom styles are in `.publish/custom.scss`.
- The site uses the Adwaita Flexoki light/dark palette and the locally bundled RIDIBatang font. Keep the font asset and SIL OFL notice together under `.publish/`.
- Keep the Quartz dark-mode component enabled; it sets `saved-theme`, which activates the configured light/dark palette.
- Keep the explorer, search, graph, backlinks, table of contents, reader mode, and navigation components enabled to retain the FPS-site-style Quartz layout.
- Keep the generated tag archive disabled unless requested; only real source files under `posts/` should be published.
- Quartz wraps rendered Markdown headings inside a preview container and renders `article-title` in `.page-header`. Font overrides must cover both `.page > #quartz-body .center article` descendants and `.page > #quartz-body .page-header h1.article-title`.

## Build and deploy

- `.github/workflows/publish.yml` is the source of truth for the pinned Quartz revision and GitHub Pages build/deploy steps.
- For local verification, use the workflow's pinned `QUARTZ_REF`, copy `.publish/quartz.config.yaml` and `.publish/custom.scss` into Quartz, copy the font/license into `quartz/static/`, sync only `posts/` into Quartz `content/`, then run `npx quartz build`.
- Check that frontmatter is absent from rendered page bodies, the page title is correct, the local font loads, and the sitemap is generated.
- Preserve unrelated edits, especially `.obsidian/workspace.json` and untracked personal notes. Stage only task-specific paths; do not use `git add -A` blindly.
- Do not commit or push unless the user asks for it.
