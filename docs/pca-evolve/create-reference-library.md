---
title: Create a reference-data library
description: Create a Draft ontology/library, class, or property in the PCA Creator workspace or API.
---

Use the reference-data workspace for general vocabulary and ontology content. Choose the
resource that matches the result you need:

| Resource | Use it to |
|---|---|
| Library or ontology | Establish the context and namespace for a maintained body of content. |
| Class | Describe a reusable kind of thing below an existing class. |
| Property | Describe a reusable characteristic or relationship. |

Use a specialized CFIHOS+, IMF, or symbol workspace when those domain rules apply.

Older examples may mention annotation-property or SHACL-shape authoring routes. Those
routes are not supported and must not be used.

## What you should prepare first

Before you start, prepare:

- the target library for a class or property;
- a parent class or other structural context for a class;
- domain/range or equivalent semantics for a property, as required by the form; and
- any upper ontologies for a new library.

A new library can also include a CFIHOS namespace prefix and an automatic backup
frequency of daily, weekly, or monthly. If the library will be used for CFIHOS+, both
the CFIHOS namespace prefix and **CFIHOS RDL v2.0** as an upper ontology must be set.
Choose these settings with the collection owner; they are operational settings, not
content review outcomes.

## Create in the PCA platform

1. Search for the library, class, property, and close alternatives.
2. Open **Create > Reference data** and choose Library, Class, or Property.
3. Select and verify the target library when the resource is not itself a library.
4. Enter the definition, justification, relationships, sources, and mappings.
5. For a library, configure upper ontologies and the agreed backup frequency. For a
   CFIHOS+ library, also set the CFIHOS namespace prefix and select **CFIHOS RDL v2.0**.
6. Choose **Save as Draft**.
7. Follow **View draft**, check the generated IRI and status, and edit if required.
8. Use **Submit for review** only when the Draft is complete.

## Create through the API

If you use the API, the main reference-library creation endpoints include:

- `POST /ontologies/domains` for a library/ontology;
- `POST /rdl/terms/subclass` for a class; and
- `POST /general/property` for a property.

Typical technical workflow:

1. Authenticate with the correct role.
2. Build the payload for the specific content type.
3. Include `changeJustification`, `name`, `description`, and the target library where required.
4. Add the type-specific structural fields.
5. Store the returned Draft location or identifier.
6. To edit, send `PUT` to the same route with the Draft IRI in `iri`.
7. Submit the complete Draft with `PUT /status/submit?iri=<encoded-IRI>`.

`changeJustification` is mandatory. Be precise about the ontology you are writing
into, and search for near-duplicates before creating a differently worded concept. The
[API endpoint and error reference](../pca-consume/api-reference.md) contains the shared
request fields and response behavior; [Work with drafts and submit content](drafts-and-submission.md)
explains what to do with the returned Draft.
