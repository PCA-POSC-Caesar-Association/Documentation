---
title: IMF type authoring
description: Plan and author reusable IMF attribute, terminal, and block types with Draft editing, API creation, and SHACL retrieval.
---

IMF authoring lets you describe reusable information requirements for digital twins,
asset information, and related engineering models. The types build on one another, so
start with the smallest reusable parts and compose them in dependency order.

| Order | Resource | What it describes |
|---|---|---|
| 1 | [Attribute type](imf-attribute-types.md) | A reusable qualified property or value requirement. |
| 2 | [Terminal type](imf-terminal-types.md) | A reusable connection interface with attribute and reference constraints. |
| 3 | [Block type](imf-block-types.md) | A reusable structure composed from attributes, terminals, references, and other blocks. |

## Before you start

For every type, prepare:

- the name and description
- the justification for the new type
- any replacement relationship if you are creating a new version
- the target library and the RDL, CFIHOS, or IMF references needed by the type;
- cardinalities for every composed reference; and
- definition sources and external mappings where applicable.

## Create and use the types

Search for reusable parts before creating them, then follow the guide for the first type
you need. Each guide covers the interactive form, Creator API route, required
relationships, and domain-specific checks. Keep the returned IRI: later IMF types use
those IRIs as references.

When the type is ready, follow the shared
[Draft and submission workflow](drafts-and-submission.md). Reader and Creator clients
can also retrieve complete SHACL for a block or terminal when they need the assembled
constraint graph; [Find and retrieve data through the API](../pca-consume/get-content-through-the-api.md)
and the endpoint reference describe that consumption path.
