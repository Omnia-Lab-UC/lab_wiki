# Omnia Lab Wiki — Ground Rules

Quarto website serving as the Omnia Lab (UC) knowledge base. Public repo at
`Omnia-Lab-UC/lab_wiki`, published from `main`.

## Commands

```bash
quarto preview        # live-reload dev server
quarto render         # full build into _site/ — must pass before any commit
```

There are no tests; a clean `quarto render` is the acceptance check.

## Structure

- `_quarto.yml` — site config and the source of truth for which sections exist.
  Sidebar sections use globs (`onboarding/*.qmd`), so new pages appear
  automatically; only edit this file to add a whole new section.
- `index.qmd` — home page. `contributing.qmd` — human-facing editing guide;
  its Sections table says what belongs in each folder.
- Content lives in one folder per section. Each has an `index.qmd` with a
  `listing` block that auto-lists the section's pages — don't hand-maintain
  page lists.
- Exception: `tutorials/` is a single sidebar link, not a glob, and its
  `index.qmd` is hand-written. A new page there won't show up in the sidebar
  or a listing; link it from `tutorials/index.qmd`.
- `_site/` and `.quarto/` are build outputs: never edit, never commit.

## Writing pages

- Write in English, even when the request or source material is in Spanish.
- New content = one `.qmd` file in the right section folder. Don't create new
  top-level sections without being asked.
- Filenames: lowercase kebab-case (`rna-extraction.qmd`).
- Every page needs frontmatter with `title` and a one-line `description`
  (the description is what shows in section listing tables).
- One `title` in frontmatter, no `#` H1 in the body; start body headings at `##`.
- One topic per page; prefer a new page over a very long one.
- Internal links point to `.qmd` source files (`../computing/index.qmd`),
  not `.html` — Quarto resolves them and validates at render time.
- Images go in an `images/` subfolder inside the page's section.
- Plain Markdown by default. Executable code cells only when the output
  genuinely needs to be computed; `freeze: auto` is enabled, so rendered
  results are cached under `_freeze/` (commit that folder if it appears).

## Hard constraints

- **This repo is public.** Never add credentials, API keys, internal
  hostnames/IPs paired with access details, participant/patient data, or
  unpublished results. If asked to document something sensitive, flag it
  instead of writing it.
- Don't delete or rewrite existing pages wholesale without being asked;
  wiki pages accumulate institutional knowledge that may not be obvious.
- Run `quarto render` before committing content changes; fix any warnings
  about broken links.

## Git

- Small content edits: commit directly to `main`.
- Structural changes (new sections, `_quarto.yml`, theme): branch + PR.
- Commit messages: short imperative summary, e.g. `Add HPC access page`.
