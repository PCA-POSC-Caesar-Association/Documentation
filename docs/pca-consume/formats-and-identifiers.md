---
title: Identifiers and representations
description: Resolve PCA and supported legacy RDS identifiers and request the correct HTML, JSON, or RDF representation.
---

You may encounter a PCA resource in a browser, a search result, an API response, or an
RDF graph. Two related values help you refer to and retrieve it correctly:

- the **identifier** is the durable IRI that identifies a resource; and
- the **access URL** is the environment-specific address used to retrieve a representation.

## Identifiers

Store and exchange the identifier returned in the resource data. It identifies the
resource independently of the server that currently delivers it. The access URL can be
different: it tells your browser or API client where to request a representation.

For recognized PCA resources, the platform resolves the requested path to the canonical
IRI and returns a representation of that resource. This means a browser can show the
current HTTPS host while the page or RDF still presents an older IRI as the resource's
identifier.

Always use HTTPS when making a request to PCA. Some historical identifiers begin with
`http://`, but that is part of the identifier and does not mean that you should make an
insecure HTTP request. An HTTP request may return only a redirect; it should not be
relied on to retrieve the representation.

## Production and development environments

In production, follow the access link returned by PCA. When you work against another
environment, send requests to that environment instead:

```text
https://<environment>.posccaesar.org/<resource-path>
```

The representation can still contain the resource's canonical production or legacy
identifier. Preserve that identifier in your data. When you use a returned PCA resource
as the target of a subsequent request, use the environment-specific `Link` where one is
provided, or change the hostname of the request URL to the environment you are testing.
Do not replace identifiers throughout stored RDF or change external identifiers.

Swagger UI is already connected to the environment where it is hosted. It sends the
request to that environment, so you can keep canonical identifiers in request fields
unless an endpoint says otherwise.

## Resolving legacy `rds.posccaesar.org` identifiers

PCA has moved the service that answers selected legacy RDS identifiers to the current
PCA host. DNS and web routing keep the old addresses usable: a request to the legacy
HTTPS host is redirected automatically to the corresponding path on the current host.

This change does not create a new identifier and does not require existing data,
mappings, or citations to be rewritten. For example, the IDO core ontology can be
requested through its familiar RDS address:

```text
https://rds.posccaesar.org/ontology/lis14/ont/core
```

The request is redirected to the current access URL:

```text
https://posccaesar.org/ontology/lis14/ont/core
```

The current host serves the representation, but the ontology keeps its canonical
identifier:

```text
http://rds.posccaesar.org/ontology/lis14/ont/core
```

You can therefore continue to use the existing identifier without changing data,
mappings, or citations. A browser follows the host redirect and shows the current URL;
the content page still shows the canonical RDS identifier. API clients must be
configured to follow the redirect.

### Legacy identifier families covered by the routing

Legacy resources that have moved from `rds.posccaesar.org` to `posccaesar.org`, while
keeping their original identifiers, include:

- any resource below `http://rds.posccaesar.org/ontology/lis14/rdl/`;
- any resource below `http://rds.posccaesar.org/ontology/plm/rdl/`;
- the unversioned LIS14 core ontology IRI; and
- the recognized unversioned PLM ontology IRIs for core, CHEBI adaptation, document,
  process, equipment, UoM, datasheet, NORSOK Z-001, and core collect.

Versioned ontologies have not moved. For example,
`https://rds.posccaesar.org/ontology/lis14/ont/core/4.0` is still served from the legacy
host. These ontologies are planned to move later, and machine-readable access through
the current PCA service will then require authorization. Unknown PLM ontology paths are
also not covered by the current routing.

Do not mechanically rewrite an arbitrary `rds.posccaesar.org` IRI. Preserve the
canonical identifier in RDF, citations, and mappings, and use PCA's resolution service
to determine whether an older identifier is supported.

## Human-readable and machine-readable views

The same resource path can negotiate different views:

- as a human-readable HTML page in the browser
- as JSON or an RDF representation for software

## Representations

For dereferenceable reference data, use an explicit `Accept` header:

| `Accept` | Typical access |
|---|---|
| `text/html` | Human-readable page; no PCA role required |
| `application/json` | Reader or Creator |
| `text/turtle` | Reader or Creator |
| `application/ld+json` | Reader or Creator |
| `application/trig` | Reader or Creator |
| `application/n-triples` | Reader or Creator |
| `application/rdf+xml` | Reader or Creator |
| `application/n-quads` | Reader or Creator |

Specialized endpoints have their own format set. Engineering symbols support Turtle,
JSON-LD, and JSON. Complete IMF SHACL supports JSON-LD, plain text, Turtle, and TriG.
Unsupported negotiation returns `406 Not Acceptable`.

The following example shows the variables needed to request a supported representation
for a resource:

```bash
curl \
  --header 'Accept: <representation-media-type>' \
  --header 'Authorization: Bearer <access-token>' \
  '<resource-identifier>'
```

Replace `<representation-media-type>` with a supported value from the table, and use an
HTTPS address for `<resource-identifier>`.

For content that has moved between PCA-owned hosts, such as IDO, `--location-trusted`
is useful because curl otherwise does not forward the bearer token when a redirect
changes the hostname. Use it only for this known PCA redirect, because the option allows
credentials to be forwarded to the redirect target:

```bash
curl --location-trusted \
  --header 'Accept: <representation-media-type>' \
  --header 'Authorization: Bearer <access-token>' \
  'https://rds.posccaesar.org/ontology/lis14/rdl/Activity'
```

Replace `<representation-media-type>` with a supported value from the table.

## Practical advice

1. Use HTML first if you are unsure about meaning or status.
2. Preserve the IRI supplied by the content.
3. Request an explicit representation and handle `406`.
4. Allow the known PCA legacy-host redirect, and otherwise follow returned links instead
   of guessing environment hosts.
5. Cache with care: Draft and Submitted content can still change or receive an outcome,
   and new versions of resources can be published.

## See also

- [Use content in the browser](get-content-through-the-ui.md)
- [Find and retrieve data through the API](get-content-through-the-api.md)
- [Read and assess content pages](../pca-explore/understand-content-pages.md)
