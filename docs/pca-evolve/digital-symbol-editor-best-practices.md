---
title: Engineering-symbol geometry and quality practices
description: Validate SVG path geometry, dimensions, fill behavior, metadata, center of rotation, and connection points before review.
---

Use this checklist before saving and again before submitting.

## Best practices

- Let `<path d="...">` geometry carry the meaning; other SVG element types and styling
  are not the stored geometry.
- Use non-zero dimensions and make both width and height multiples of 12.
- Avoid relying on color, stroke styling, masks, embedded text, or external assets.
- Keep the symbol as simple as possible without losing meaning.
- Verify nonzero fill rules and path direction carefully.
- Make metadata clear enough for reviewers who do not share your local context.
- Add exactly one deliberate center of rotation; it is required to save or submit.
- Add connection points only where applications should connect an edge; verify X/Y and
  direction for each point.
- Choose the target symbol library before the first save; the existing-Draft editor keeps
  that library fixed.
- Use a precise `Replaces` IRI only for a real new version.

## Troubleshooting checklist

If something does not behave as expected, check:

- whether the file is valid SVG XML with an `<svg>` root
- whether at least one path has non-empty `d`
- whether `viewBox` or explicit dimensions can be read and both dimensions are multiples of 12
- whether the paths are closed where needed
- whether path direction produces the intended fill result
- whether a center of rotation exists
- whether name, description, target library, and justification are complete
- whether the resource is still Draft; Submitted/Pending review symbols are locked

## See also

- [Create and edit engineering symbols](digital-symbol-editor.md)
- [Prepare SVGs with Figma](digital-symbol-editor-figma-workflow.md)
- [Submit an engineering symbol](digital-symbol-editor-submission-workflow.md)
