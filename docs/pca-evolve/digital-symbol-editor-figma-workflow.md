---
title: Prepare SVGs with Figma
description: Convert engineering-symbol artwork to valid geometry-only SVG with path data, nonzero fill behavior, and a 12-unit grid.
---

Prepare the visual geometry in Figma and use the
[PCA Engineering Symbols Tool](https://www.figma.com/community/plugin/1564995746782047272/pca-engineering-symbols-tool)
when you need help converting strokes and shapes to the geometry the platform stores.
Figma is optional: any tool or text editor can produce the SVG if it meets the same
requirements.

## Goal

Your goal is to produce a geometry-only SVG that PCA can ingest reliably.

## Step-by-step

1. Design on dimensions that can be exported as width and height multiples of 12.
2. Convert meaningful strokes and shapes into path geometry.
3. Use the Engineering Symbols Tool plugin to expand strokes where needed.
4. Flatten or convert relevant visual objects so the export contains `<path>` elements
   with non-empty `d` attributes.
5. Check closed paths, path direction, and the nonzero fill rule.
6. Export a valid SVG with a `viewBox`, or explicit non-zero width and height.
7. Reopen the exported file or import it into PCA and verify the geometry without styling.

## Create a compatible SVG without Figma

The uploaded file must be valid, non-empty SVG XML with `<svg>` as its root. It must
contain at least one `<path>` with a non-empty `d` attribute, and its non-zero width and
height must both be multiples of 12. You can provide the dimensions through a `viewBox`
or explicit `width` and `height` values.

This minimal 24-by-24 example meets the upload requirements:

```xml
<svg xmlns="http://www.w3.org/2000/svg"
     width="24" height="24" viewBox="0 0 24 24">
  <path d="M 3 3 H 21 V 21 H 3 Z" />
</svg>
```

PCA imports path geometry. Convert circles, rectangles, strokes, and other visual
objects to paths before upload, and check that the resulting shape still looks correct
with the nonzero fill rule.

## What PCA keeps from the SVG

PCA joins the non-empty `d` values from SVG `<path>` elements. Other elements such as
circles and rectangles, and styling such as color and stroke width, are not retained as
the symbol geometry. Applications can then control presentation independently.

## What to verify before export

- the file still meets the structural upload requirements above
- closed paths behave correctly
- nonzero fill behavior is correct for outlined and filled symbols
- the exported result still expresses the intended shape

## See also

- [Create and edit engineering symbols](digital-symbol-editor.md)
- [Submit an engineering symbol](digital-symbol-editor-submission-workflow.md)
- [Geometry and quality practices](digital-symbol-editor-best-practices.md)
