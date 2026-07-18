# Sukarix Documentation — Agent Guidelines

## Project

mdBook-based documentation for the Sukarix PHP framework. Source files live
in `src/` and are organised by section (prologue, getting-started, basics,
advanced, security, packages, testing, etc.).

## Tech stack

- **mdBook** with `mdbook-admonish` — `book.toml` at repo root
- **Markdown** — standard mdBook syntax, `<!-- toc -->` for table of contents

## Writing style

- Keep pages concise and practical.
- Code examples must match the actual framework code (verify against `sukarix/src/`).
- Use relative links between docs pages (`../packages/statera.md`).
- Statera is the framework's testing kit — never refer to it as deprecated.

## Commits

- One logical change per commit (unitary commits).
- Author: Ghazi Triki <ghazi.triki@riadvice.com>
- Co-author trailer:
  ```
  Co-Authored-By: Devin <158243242+devin-ai-integration[bot]@users.noreply.github.com>
  ```
- Format:
  ```
  <short description>

  Generated with [Devin](https://devin.ai)

  Co-Authored-By: Devin <158243242+devin-ai-integration[bot]@users.noreply.github.com>
  ```
