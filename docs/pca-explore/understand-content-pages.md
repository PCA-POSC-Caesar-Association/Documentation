---
title: Read and assess content pages
description: Interpret PCA resource pages, provenance, status, hierarchy, mappings, and version relationships before reuse.
---

A content page turns a PCA resource into a human-readable view. Use it to understand the
resource itself and the context around it—its identifier, owning collection, hierarchy,
provenance, lifecycle status, mappings, and historical or replacement information.

## Read a content page

1. Open the content page from search or from a known link.
2. Confirm the IRI, label, type, and owning collection. Similar labels can identify
   different concepts.
3. Read the definition and any stated source. A definition source is evidence for the
   wording; it is not the same as a semantic mapping.
4. Inspect parent, child, property, dependency, and related-term links.
5. Check status and version information. Prefer a replacement over a Deprecated item.
6. Assess external mappings and their relationship type before treating identifiers as
   equivalent.
7. Choose the next action: follow links, retrieve a representation, edit a Draft if you
   are its Creator, or submit it for review.

## Interpret the actions on a page

- **Edit this resource** is available for supported Draft types to a Creator.
- **Submit for review** is available for a Draft to an authorized Creator or Reviewer.
- Submitted/Pending review content is locked against Creator editing.
- Externally Managed content is not managed through PCA's content lifecycle and cannot
  enter the built-in authoring workflow.

The absence of an action is meaningful: check your role, the resource type, and its
status before reporting a platform error.

## Continue from the page

- Follow hierarchy and relationship links to understand the surrounding model.
- Preserve the displayed resource identifier when referring to the concept elsewhere.
- Continue to [Use data in applications](../pca-consume/index.md) for machine-readable
  retrieval.
- Continue to [Create and extend content](../pca-evolve/index.md) if the needed content
  does not exist or a new governed version is required.

## Technical note

The page URL and the RDF identifier can differ in host or scheme for supported legacy
identifiers. Preserve the identifier supplied in the resource data and follow the
platform link for access. [Identifiers and representations](../pca-consume/formats-and-identifiers.md)
explains how these two addresses relate.
