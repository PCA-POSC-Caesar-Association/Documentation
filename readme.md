This repository stores and shares PCA documentation, plans, and related working material.

## Local documentation setup

1. Install dependencies:
   - `python3 -m pip install -r requirements.txt`
2. Start the docs site locally:
   - `mkdocs serve`
3. Open the local URL shown by MkDocs (usually `http://127.0.0.1:8000`).

## MkDocs structure

- MkDocs config: `mkdocs.yml`
- Docs source directory: `docs/`
- Theme: Material (`mkdocs-material==9.7.3`)

## PagesCMS authoring

- PagesCMS config: `.pages.yml`
- Content collection path: `docs/`
- New pages are created as Markdown files in `docs/`.
- Media uploads are stored in `docs/images` and exposed as `/images` in MkDocs.
- Existing Markdown files without front matter remain supported.
