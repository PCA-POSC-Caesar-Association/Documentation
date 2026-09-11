---
title: Create IMF terminal types
description: Create Draft IMF terminal types with direction, aspect, classification, attribute references, term references, and cardinalities.
---

An IMF terminal type describes a connection interface. It can constrain reusable
attributes and reference terms and can later be used by block types.

## Prepare the terminal

- Target library, name, description, and change justification.
- Direction: input or output.
- Aspect and optional classification.
- IMF attribute-type references with minimum and maximum cardinalities.
- Reference-data term references with minimum and maximum cardinalities.
- Sources, external mappings, package context, and optional `Replaces` IRI.

Create referenced attribute types first so their IRIs can be selected reliably.

## Create in the UI

1. Open **Create > IMF > Terminal type**.
2. Select direction, aspect, and optional classification.
3. Add attribute and reference-term constraints.
4. Verify every cardinality, especially optional versus required and single versus many.
5. Save as Draft and inspect **View draft**.
6. Update the Draft if required and submit it when complete.

## Use the API

- Create: `POST /imf/terminaltypes`
- Update Draft: `PUT /imf/terminaltypes?iri=<encoded-Draft-IRI>`
- Submit: `PUT /status/submit?iri=<encoded-Draft-IRI>`
- Retrieve complete SHACL:
  `GET /api/terminals/complete-imf-shacl?terminalId=<lowercase-guid>`

With Reader or Creator access, the complete-SHACL endpoint supports JSON-LD, plain
text, Turtle, and TriG. The terminal ID must be a lowercase GUID. It assembles the
constraint graph for consumption; it does not submit or approve the type.
