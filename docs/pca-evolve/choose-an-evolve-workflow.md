---
title: Choose a content workflow
description: Select the correct PCA Creator workspace for reference data, CFIHOS+, IMF types, or engineering symbols.
---

The table below gives a general mapping from common needs to corresponding resource
types that can be created.

| Need | Workspace | Main resources |
|---|---|---|
| Establish a shared vocabulary or describe a reusable concept | [Reference data and taxonomies](create-reference-library.md) | Library/ontology, class, property |
| Extend/build on the CFIHOS library | [CFIHOS+ extensions](cfihos-extensions.md) | Equipment class, tag class, property, picklist, unit, dimension |
| Describe reusable information-model structures and their constraints | [IMF type authoring](imf-types.md) | Attribute type, terminal type, block type |
| Publish a diagram symbol with reusable geometry and connection information | [Engineering symbols](digital-symbol-editor.md) | Symbol, geometry, centre of rotation, connection points |

In practical terms, start with what is missing. A new business concept or vocabulary
usually belongs in reference data. A missing CFIHOS class, property, allowed-value list,
or measurement concept belongs in CFIHOS+. Reusable requirements belong in
an IMF type, while visual diagram elements belong in the Engineering Symbol Editor.

## After you choose

We advise you to complete [Prepare to create content](prepare-to-create-content.md)
before opening a form or building an API payload. The selected domain guide then
explains the information and relationships unique to that resource. The shared steps
for reopening, updating, and submitting the result are kept in
[Work with drafts and submit content](drafts-and-submission.md).
