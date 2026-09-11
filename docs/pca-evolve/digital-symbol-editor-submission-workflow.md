---
title: Submit an engineering symbol
description: Upload, describe, save, reopen, edit, and submit an engineering-symbol Draft through the PCA editor or API.
---

This guide starts after you have a geometry-only SVG that passes the import checks.

## What to prepare before you upload

Prepare these before you start the form:

- the final SVG file
- the intended symbol name
- the description or definition
- any additional context that reviewers need to understand the proposal
- the required center of rotation and any optional connection points
- target symbol library, justification, sources, package, or replacement context

## Upload and submit the symbol

1. With Creator access, open **Create > Symbols**.
2. Upload the prepared geometry-only SVG file.
3. Enter the required name and description.
4. Select the target symbol library.
5. Add optional package name and a verified `Replaces` IRI where applicable.
6. Enter the creation justification.
7. Add a center of rotation. This is required even for Save as Draft.
8. Add optional connection points and verify their coordinates and directions.
9. Choose **Save as Draft** and keep the generated resource link.
10. Reopen the Draft to inspect or edit it; each update needs a change justification.
11. Choose **Submit for review**, confirm, and verify Pending review on the resource page.

## What happens after submission

The editor saves unsaved changes before an immediate submit. If submission fails after a
successful save, the symbol remains an addressable Draft; use **View draft** and retry
submission instead of recreating it. Submitted symbols are locked against Creator edits.

## API equivalent

- Create Draft: `POST /esl/engineeringSymbols`
- Update Draft: `PUT /esl/engineeringSymbols?iri=<encoded-Draft-IRI>`
- Submit: `PUT /status/submit?iri=<encoded-Draft-IRI>`
- Reader or Creator retrieval: `GET /esl/engineeringSymbols`

Use Swagger for the geometry, center, and connection-point payload schema. The center
is a single point. Connection points include identity, X/Y position, and direction.

## See also

- [Create and edit engineering symbols](digital-symbol-editor.md)
- [Prepare SVGs with Figma](digital-symbol-editor-figma-workflow.md)
- [Work with drafts and submit content](drafts-and-submission.md)
