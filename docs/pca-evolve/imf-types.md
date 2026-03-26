---
title: IMF Types
---

This guide explains how to create reusable IMF types through PCA.

## What this workflow covers

PCA supports creation of IMF:

- attribute types
- block types
- terminal types

This is useful when you want reusable information structures for digital twins, asset information, or related engineering information models.

## Before you start

Prepare:

- the name and description
- the justification for the new type
- any replacement relationship if you are creating a new version
- the RDL or CFIHOS references needed by the type

## Step-by-step for interactive users

1. Confirm through [PCA Explore](../pca-explore/index.md) that the type does not already exist.
2. Choose whether you need an attribute, block, or terminal type.
3. Open the matching platform form.
4. Fill in the required information.
5. Check references, qualifiers, and replacements carefully.
6. Submit the type for review.

## Step-by-step for technical users

Relevant endpoints include:

- `POST /imf/attributetypes`
- `POST /imf/blocktypes`
- `POST /imf/terminaltypes`
- `GET /api/blocks/complete-imf-shacl`
- `GET /api/terminals/complete-imf-shacl`

Typical workflow:

1. Build the creation payload with the required identifiers and qualifiers.
2. Submit it with creator access.
3. Use the SHACL endpoints when you need a complete SHACL representation of a created block or terminal.

## Important note for technical users

CFIHOS references are transformed into PCA-hosted URIs so they can be used in IMF content. This matters particularly when building API payloads for IMF attribute types.

## See also

- [Choose an Evolve Workflow](choose-an-evolve-workflow.md)
- [PCA Consume](../pca-consume/get-content-through-the-api.md)
