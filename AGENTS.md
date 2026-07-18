# Sukarix Documentation

mdBook-based documentation for the Sukarix PHP framework.
MIT licensed. Contributions welcome.

## Quick start

```bash
mdbook serve --open    # live preview at http://localhost:3000
```

## Tech stack

- mdBook with mdbook-admonish
- Markdown — standard mdBook syntax
- `<!-- toc -->` for table of contents

## Structure

- `src/SUMMARY.md` — table of contents (navigation)
- `src/prologue/` — overview, features, F3 introduction
- `src/getting-started/` — installation, configuration, directory structure
- `src/architecture-concepts/` — terminology, lifecycle, DI
- `src/basics/` — routing, database, validation, session, upload
- `src/advanced/` — advanced framework features
- `src/packages/` — Sukarix packages (Statera, etc.)
- `src/testing/` — testing guide
- `src/security/` — security practices
- `src/release-notes.md` — changelog

## Writing guidelines

- Keep pages concise and practical
- Code examples must match the actual framework code (verify against `sukarix/src/`)
- Use relative links between pages (`../packages/statera.md`)
- Add new pages to `src/SUMMARY.md`
- Statera is the framework's testing kit — never refer to it as deprecated

## AI usage

This project is developed with AI assistance (Devin, GitHub Copilot, and others).
AI-generated contributions are welcome and should follow the same conventions as human contributions.

## Commits

One logical change per commit.

```
<description>

Co-Authored-By: Devin
```
