---
title: Search and filter
description: Use PCA search to find resources, narrow results, check status, and avoid duplicate proposals.
---

Use Search to move from a name, phrase, or identifier to a resource you can assess. It
is useful both when you know exactly what you need and when you are still comparing
possible terms, types, properties, symbols, or libraries. Libraries and Search are
available without a PCA role.

## Search in the PCA platform

1. Open the search area of the platform.
2. Enter a preferred label, synonym, phrase, or known IRI.
3. Compare labels, resource types, collections or ontologies, and status.
4. Apply the available result filters and narrow broad wording when needed.
5. Open several plausible results; a matching label alone is not enough.
6. Inspect hierarchy, definitions, mappings, and version or replacement links.
7. Confirm the resource and its status before reuse.

## Read the results in context

A matching label is only a starting point. Open plausible results and compare:

- the preferred label or other labels
- the type of content you are looking at
- the ontology or collection it belongs to
- status, especially Draft, Pending review, Deprecated, or Externally managed
- replacement links and external mappings.

Search broadly first and narrow the wording as you learn the terminology. If several
results look similar, compare their definitions and relationships rather than choosing
by label alone. Creators should do this before authoring: the platform may perform its
own checks, but it cannot decide that two differently worded concepts mean the same
thing.

## Search from an application

For code, a Reader or Creator can use `GET /search/search-index` to obtain identifiers
and context for the next retrieval step. The route may be omitted from Swagger; the
[API endpoint and error reference](../pca-consume/api-reference.md) describes its access
and response behavior. To interpret a result before retrieving it, continue to
[Read and assess content pages](understand-content-pages.md).
