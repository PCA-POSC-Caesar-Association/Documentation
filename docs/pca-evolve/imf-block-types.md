---
title: Create IMF block types
description: Create Draft IMF block types from classifications, attributes, reference terms, terminals, sub-blocks, and cardinalities.
---

An IMF block type composes a reusable structure. It can constrain attributes, reference
terms, terminal types, and nested block types.

## Prepare the block

- Target library, name, description, and change justification.
- Aspect and optional classification.
- Attribute-type and reference-term constraints with cardinalities.
- Terminal-type constraints with cardinalities.
- Sub-block-type constraints with cardinalities.
- Sources, mappings, package context, and optional `Replaces` IRI.

Create or identify the reusable attributes and terminals first. For recursive-looking
structures, verify that the selected sub-block is intentional and that the cardinality
does not make an impossible required cycle.

## Create in the UI

1. Open **Create > IMF > Block type**.
2. Select aspect and optional classification.
3. Add attribute, reference-term, terminal, and sub-block constraints.
4. Verify each referenced IRI and cardinality.
5. Save as Draft and inspect **View draft**.
6. Edit the Draft if needed, then submit it for review.

## Use the API

- Create: `POST /imf/blocktypes`
- Update Draft: `PUT /imf/blocktypes?iri=<encoded-Draft-IRI>`
- Submit: `PUT /status/submit?iri=<encoded-Draft-IRI>`
- Retrieve complete SHACL:
  `GET /api/blocks/complete-imf-shacl?blockId=<lowercase-guid>`

With Reader or Creator access, the complete-SHACL endpoint supports JSON-LD, plain
text, Turtle, and TriG. The block ID must be a lowercase GUID. Consumers should still
inspect the block's status and provenance before treating the assembled graph as
approved production content.
