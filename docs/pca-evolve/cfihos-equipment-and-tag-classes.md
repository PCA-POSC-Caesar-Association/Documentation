---
title: Create CFIHOS+ equipment and tag classes
description: Create Draft CFIHOS+ equipment or tag classes with parents, properties, cardinalities, flags, sources, and mappings.
---

Equipment and tag classes extend their corresponding CFIHOS hierarchy. Choose the
correct kind first; their available flags and expected context differ.

## Prepare the model

Collect:

- the target library;
- class name, definition, and change justification;
- the direct super-entity;
- directly assigned property references and their cardinalities;
- applicable classification flags, such as abstract, installed, or spare-part behavior
  shown by the selected form;
- definition sources and external mappings; and
- an optional exact resource IRI in `Replaces` for a new version.

Use inherited properties to understand what the parent already supplies. Do not repeat a
property as direct merely to make it visible.

## Create in the UI

1. Open **Create > CFIHOS+**.
2. Choose **Equipment class** or **Tag class**.
3. Select the target library and the correct super-entity.
4. Add direct properties and verify minimum and maximum cardinalities.
5. Complete applicable flags, sources, mappings, and justification.
6. Select **Save as Draft**.
7. Open **View draft**, inspect inherited and direct context, and update if needed.
8. Submit the Draft when the class and its relationships are complete.

## Use the API

- Create: `POST /cfihos/entity`
- Update Draft: `PUT /cfihos/entity?iri=<encoded-Draft-IRI>`
- Read inherited properties:
  `GET /cfihos/ancestors/properties?cfihosUri=<encoded-absolute-IRI>`
- Submit: `PUT /status/submit?iri=<encoded-Draft-IRI>`

Use Swagger for the deployed request schema. Do not infer an entity discriminator,
cardinality shape, or flag name from this guide. Validate all referenced IRIs and model
the same direct relationships as the interactive form.

## External mapping rules

CFIHOS equipment classes can map to ETIM equipment classes and to appropriate UNSPSC
class or commodity identifiers. A mapping to an UNSPSC Class must be broader rather
than exact. See [Definition sources and external mappings](definition-sources-and-mappings.md).

## Verify before submission

- The class kind and super-entity are correct.
- Direct properties are not inherited duplicates.
- Each cardinality expresses the real constraint.
- The definition and mapping relation do not overstate equivalence.
- `Replaces`, if present, points to the exact resource that may become Deprecated.
