---
title: Create CFIHOS+ units and dimensions
description: Create Draft CFIHOS+ units of measure and UoM dimensions and connect numeric properties to the right quantity model.
---

A UoM dimension describes the physical quantity model; a unit describes a concrete
measurement expression within that model. Create the dimension first when it does not
already exist.

## UoM dimension

Prepare the target library, name, definition, dimension code, justification, sources,
mappings, and any replacement. Create with:

- UI: **Create > CFIHOS+ > UoM dimension**
- API: `POST /cfihos/dimension`
- Draft update: `PUT /cfihos/dimension?iri=<encoded-Draft-IRI>`

## Unit of measure

Prepare the target library, name, definition, referenced dimension, system (SI or
imperial), symbol, justification, sources, mappings, and any replacement. Create with:

- UI: **Create > CFIHOS+ > Unit of measure**
- API: `POST /cfihos/unitofmeasure`
- Draft update: `PUT /cfihos/unitofmeasure?iri=<encoded-Draft-IRI>`

## Interactive sequence

1. Search for the quantity, dimension, unit, symbol, and close alternatives.
2. Create and save a missing dimension as Draft.
3. Create the unit and reference the intended dimension.
4. Inspect the Draft resource pages and correct any relationship or symbol error.
5. Submit each complete Draft for review.
6. Use the dimension when creating a numeric CFIHOS+ property.

## Check external mappings

ETIM unit mappings use the supported ETIM 10.0 entity type and are validated separately
from the PCA dimension relationship. Select a mapping only when the catalogue entry and
version describe the same unit you are creating.
