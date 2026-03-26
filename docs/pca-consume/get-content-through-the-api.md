---
title: Get Content Through the API
---

This guide explains how technical users can consume PCA content through the API.

## Before you start

Read [API Authentication](api-authentication.md) first if your usage requires authenticated access.

## Main API consumption patterns

### 1. Search and discovery

Use the search endpoints when you first need to locate relevant resources.

- Search index endpoint: `search/search-index`
- UoM lookup endpoint: `search/uom`

Typical use:

1. Query the search index to locate likely resources.
2. Inspect the returned identifiers, labels, types, ontology information, and links.
3. Follow the returned links or identifiers into the next retrieval step.

### 2. Reference-data retrieval

Use dereferenceable content endpoints when you already know the resource path and need machine-readable output.

The platform supports HTML for human-readable pages and RDF representations for machine use. The RDF representations depend on the `Accept` header.

Typical use:

1. Start with a known PCA path or identifier.
2. Request the resource with the representation you need.
3. Use the returned RDF in your downstream workflow.

### 3. Specialized technical retrieval

Some content families expose dedicated endpoints that are useful in specific workflows.

Examples include:

- complete IMF SHACL for a block
- complete IMF SHACL for a terminal
- engineering symbols as RDF or JSON
- inherited properties for CFIHOS equipment or tags

## Step-by-step API workflow

1. Identify the content family you need.
2. Decide whether you need discovery, direct retrieval, or a specialized endpoint.
3. Authenticate if required.
4. Call the endpoint with the correct parameters.
5. Use the returned identifier, link, RDF, or JSON in your workflow.

## Recommended endpoint families

- `search/search-index` for discovery
- `search/uom` for applicable units of measure
- dereferenceable PCA content paths for reference-data retrieval
- `api/blocks/complete-imf-shacl` and `api/terminals/complete-imf-shacl` for IMF SHACL output
- `esl/engineeringSymbols` for engineering symbols
- `cfihos/ancestors/properties` for CFIHOS property inheritance

## Important note

Use Swagger as the detailed endpoint reference after you understand the workflow. This documentation is meant to help you choose the right path and avoid starting at the wrong technical layer.

## See also

- [API Authentication](api-authentication.md)
- [Formats and Identifiers](formats-and-identifiers.md)
- [PCA Explore](../pca-explore/index.md)
