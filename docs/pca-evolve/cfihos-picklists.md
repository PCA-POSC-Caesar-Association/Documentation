---
title: Create CFIHOS+ picklists
description: Create and maintain a Draft CFIHOS+ picklist and its values as one review aggregate.
---

A picklist and its values form one governed aggregate. The parent supplies identity and
review context; the values supply the allowed choices.

## Prepare the aggregate

- Picklist name, definition, target library, and justification.
- At least one value, each with a name and description.
- Definition sources, mappings, and version relationships where applicable.
- The full value set that reviewers need to assess together.

## Create or edit in the UI

1. Open **Create > CFIHOS+ > Picklist**.
2. Enter parent metadata and add at least one complete value.
3. Save as Draft.
4. Open the Draft and edit values through the parent picklist.
5. Verify that no value is missing a name or description and that every aggregate part
   remains Draft.
6. Submit the **parent picklist** for review.

Individual values are not separate submissions. The review queue presents the aggregate
rather than duplicating each value as an independent proposal.

## Use the API

- Create aggregate: `POST /cfihos/picklist`
- Update aggregate: `PUT /cfihos/picklist?iri=<encoded-Draft-IRI>`
- Low-level value route: `/cfihos/picklistvalue`
- Submit parent: `PUT /status/submit?iri=<encoded-picklist-IRI>`

Prefer the parent aggregate route for normal authoring. If a technical integration uses
the value route, it must still preserve aggregate lifecycle invariants. A submit fails if
the parent or a value is not Draft.

## Review-safety behavior

If the picklist or its values change while a reviewer has the decision view open, the
platform rejects the stale decision with `409 Conflict`. The reviewer must reload and
assess the current aggregate.
