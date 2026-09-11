---
title: Find and retrieve data through the API
description: Choose between authorized search, dereferenceable resources, engineering-symbol data, and IMF SHACL.
---

## Before you start

Choose the narrowest retrieval pattern that answers your question. Search finds an IRI;
dereferencing returns a representation of that resource; specialized endpoints assemble
content for a particular domain workflow.

Read [Authentication and authorization](api-authentication.md) and obtain a Reader or
Creator access token before using the API. Opening a human-readable HTML content page in
the browser is a separate journey and does not require an API token.

## Main API consumption patterns

### 1. Search and discovery

Use the search endpoints when you first need to locate relevant resources.

- Search index: `GET /search/search-index`

Typical use:

1. Query the search index to locate likely resources.
2. Inspect the returned identifiers, labels, types, ontology information, and links.
3. In production, follow the returned links rather than constructing a host from the
   identifier. In another environment, use an environment-specific returned `Link` or
   target that environment when forming the request URL, as explained in
   [Identifiers and representations](formats-and-identifiers.md).

### 2. Reference-data retrieval

Use dereferenceable content endpoints when you already know the resource path and need machine-readable output.

Use a Reader or Creator access token and request the required JSON or RDF representation
with `Accept`.

Typical use:

1. Start with a known PCA path or identifier.
2. Request the resource with the representation you need.
3. Use the returned RDF in your downstream workflow.

For ontology resources, `detailLevel` controls how much context PCA returns:

| Value | Meaning |
|---|---|
| `1` | Summary |
| `2` | Relations; this is the default |
| `3` | Complete ontology, including its members and related ontology context |

For example, this request retrieves the complete IDO core ontology as Turtle. The
legacy RDS URL redirects to the current PCA host, so `--location-trusted` is needed to
forward the bearer token across this known PCA-owned redirect:

```bash
curl --location-trusted \
  --header 'Authorization: Bearer <access-token>' \
  --header 'Accept: text/turtle' \
  'https://rds.posccaesar.org/ontology/lis14/ont/core?detailLevel=3'
```

Use `detailLevel=3` with an RDF representation. The current HTML and JSON handlers do
not return the complete ontology view.

### 3. Specialized technical retrieval

Some content families expose dedicated endpoints that are useful in specific workflows.

Supported examples include:

- `GET /api/blocks/complete-imf-shacl?blockId=<lowercase-guid>`;
- `GET /api/terminals/complete-imf-shacl?terminalId=<lowercase-guid>`;
- `GET /esl/engineeringSymbols`.

**Note:** IMF IDs must use a lowercase GUID.

For the supported route families, see the
[API endpoint and error reference](api-reference.md). Contact PCA before depending on
anything undocumented.
