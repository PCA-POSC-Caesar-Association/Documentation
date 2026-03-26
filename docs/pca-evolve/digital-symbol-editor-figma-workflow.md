---
title: Digital Symbol Editor Figma Workflow
---

This guide explains how to prepare a symbol in Figma before uploading it to PCA.

## Goal

Your goal is to produce a geometry-only SVG that PCA can ingest reliably.

## Step-by-step

1. Design the symbol geometry in Figma.
2. Focus on the actual geometry of the symbol, not on colors or stroke styling.
3. Use path-based drawing where possible.
4. Use the Engineering Symbols Tool plugin to help convert visual shapes into a PCA-friendly geometry representation.
5. Check how closed paths and path direction affect the resulting fill behavior.
6. Export the SVG only after you have verified that the geometry, not the styling, carries the meaning.

## What PCA keeps from the SVG

PCA is interested primarily in the geometry encoded in the path data. Styling such as color and stroke width should not be relied on to carry the meaning of the symbol.

## What to verify before export

- the symbol is represented by path geometry
- closed paths behave correctly
- fill behavior is correct for outlined and filled symbols
- the exported result still expresses the intended shape

## See also

- [Digital Symbol Editor](digital-symbol-editor.md)
- [Digital Symbol Editor Submission Workflow](digital-symbol-editor-submission-workflow.md)
- [Digital Symbol Editor Best Practices](digital-symbol-editor-best-practices.md)
