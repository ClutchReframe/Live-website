# Repository Guidelines

## Project Structure & Module Organization
This repository is a static GitHub Pages site (no framework, no build step). Keep files at the root unless they are supporting docs.

- `index.html`: landing page
- `privacy.html`, `terms.html`: policy/legal pages
- `riot.txt`: Riot verification token file (plain text)
- `og-image.png`: social preview image
- `CNAME`, `.nojekyll`: GitHub Pages/domain config
- `docs/`: operational notes (domain setup, internal guides)

When adding pages, use flat naming like `about.html` and keep shared visual patterns consistent with existing files.

## Build, Test, and Development Commands
There is no compile/build pipeline.

- `python -m http.server 8080`
  Runs a local static server at `http://localhost:8080`.
- `rg --files`
  Quick inventory of tracked files before committing.
- `git diff --check`
  Detects trailing whitespace and patch-format issues.

Deployment is push-based: changes on `main` are published via GitHub Pages.

## Coding Style & Naming Conventions
Follow the current HTML/CSS style:

- Use 4-space indentation in HTML/CSS blocks.
- Keep page-level CSS inside each page’s `<style>` block (current project pattern).
- Prefer kebab-case for CSS classes (example: `.page-container`, `.nav-inner`).
- Keep filenames lowercase and web-safe (`privacy.html`, not `PrivacyPage.html`).
- Preserve canonical URLs, Open Graph, and Riot disclaimer sections on public pages.

## Testing Guidelines
No automated test framework is configured yet. Use manual checks before opening a PR:

1. Serve locally and open `index.html`, `privacy.html`, and `terms.html`.
2. Verify links, mobile layout (<=768px), and basic accessibility (heading order, readable contrast).
3. Confirm `riot.txt` loads as plain text.

Document manual verification steps in the PR description.

## Commit & Pull Request Guidelines
Git history is minimal (`Initial commit: ClutchReframe Live website`), so keep commit messages short, imperative, and specific.

- Good format: `feat: add FAQ section to landing page`
- Keep unrelated edits out of the same commit.

For PRs, include:

1. What changed and why.
2. Files/pages touched.
3. Before/after screenshots for UI edits.
4. Manual test checklist/results.
