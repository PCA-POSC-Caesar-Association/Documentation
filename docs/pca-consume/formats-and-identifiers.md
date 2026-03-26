---
title: Formats and Identifiers
---

This guide explains how PCA content is exposed through identifiers and representations.

## Identifiers

PCA content is intended to be used through stable identifiers and resolvable paths. In practice, you should treat the identifier as the durable reference and the returned representation as a view of that reference.

## Human-readable and machine-readable views

The same content can often be approached in two ways:

- as a human-readable HTML page in the browser
- as a machine-readable representation through API or RDF retrieval

## Representations

Depending on the endpoint and the `Accept` header, the platform can return formats such as:

- HTML
- Turtle
- JSON-LD
- JSON
- other RDF serializations where supported

## Practical advice

1. Use the browser first if you are unsure about the meaning of a resource.
2. Switch to programmatic retrieval once you know the correct identifier or path.
3. Be deliberate about the representation you request.
4. Keep the identifier stable in your own systems even if you consume several different representations.

## See also

- [Get Content Through the UI](get-content-through-the-ui.md)
- [Get Content Through the API](get-content-through-the-api.md)
- [Understand Content Pages](../pca-explore/understand-content-pages.md)
