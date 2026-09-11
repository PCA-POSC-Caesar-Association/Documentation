---
title: Create CFIHOS+ properties
description: Create Draft CFIHOS+ properties with the correct value type, picklist or dimension constraint, sources, and mappings.
---

A CFIHOS+ property states what value an equipment or tag class can carry. Select the
value model before adding it to classes.

## Choose the property model

| Value kind | Constraint to prepare |
|---|---|
| Number | A UoM dimension so applicable units can be resolved |
| Text with controlled values | A CFIHOS+ picklist |
| Free text | No picklist; document the intended value clearly |
| Boolean | Yes/No semantics |

Do not use free text when a maintained picklist expresses the domain, and do not bind a
numeric property directly to an arbitrary unit when the model expects a dimension.

## Create in the UI

1. Search for an existing property, synonym, dimension, or picklist.
2. Open **Create > CFIHOS+ > Property**.
3. Select the target library and value kind.
4. Select the required UoM dimension or picklist.
5. Enter the name, definition, justification, sources, mappings, and version context.
6. Save as Draft, inspect its resource page, and update as needed.
7. Submit the complete Draft for review.

## Use the API

- Create: `POST /general/property`
- Update Draft: `PUT /general/property?iri=<encoded-Draft-IRI>`
- Submit: `PUT /status/submit?iri=<encoded-Draft-IRI>`

The general property route serves more than one authoring context. Use the deployed
Swagger schema and include the CFIHOS-specific value constraint selected above.

## ETIM mapping applicability

ETIM feature mappings depend on the property's value model. Quantitative properties map
to supported numeric feature types; Boolean qualitative properties map to the supported
logical type; other controlled qualitative properties map only where the catalogue and
form allow it. The mapping selector validates catalogue version, entity type, and
relationship—do not bypass those checks with an unverified identifier.
