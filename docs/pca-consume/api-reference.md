---
title: API endpoint and error reference
description: Supported Reader and Creator endpoint families, methods, content types, statuses, and errors for PCA integrations.
---

This page is a workflow-oriented route summary. Use the deployed Swagger document for
payload schemas and examples, but remember that selected search and dereferencing routes
are intentionally absent from Swagger.

All routes are relative to the base URL supplied for your PCA environment.

## Authenticated read endpoints

| Method and route | Access | Purpose and formats |
|---|---|---|
| `GET /search/search-index` | Reader or Creator | Search available content. Returns JSON with labels, identifiers, types, collection context, links, and status where available. |
| `GET /<recognized-content-path>` | Reader or Creator | Dereference a resource as JSON, JSON-LD, Turtle, TriG, N-Triples, RDF/XML, or N-Quads, according to `Accept`. For ontology RDF, `detailLevel` is `1` for Summary, `2` for Relations (the default), or `3` for Complete. |
| `GET /esl/engineeringSymbols` | Reader or Creator | Retrieve engineering symbols as JSON, JSON-LD, or Turtle. |
| `GET /api/blocks/complete-imf-shacl` | Reader or Creator | Assemble complete block SHACL. `blockId` is a lowercase GUID; supports JSON-LD, plain text, Turtle, or TriG. |
| `GET /api/terminals/complete-imf-shacl` | Reader or Creator | Assemble complete terminal SHACL. `terminalId` is a lowercase GUID; supports JSON-LD, plain text, Turtle, or TriG. |

## Creator write endpoints

Each supported family uses `POST` to create and `PUT ...?iri=<encoded-IRI>` to update a
Draft. Request bodies differ by resource type; use Swagger for the deployed schema.

| Route | Resource family |
|---|---|
| `/ontologies/domains` | Reference-data library or ontology |
| `/rdl/terms/subclass` | Reference-data class |
| `/general/property` | Reference-data or CFIHOS property |
| `/cfihos/entity` | CFIHOS+ equipment or tag class |
| `/cfihos/picklist` | CFIHOS+ picklist and its values as an aggregate |
| `/cfihos/picklistvalue` | Picklist value API; normally manage values through the parent picklist |
| `/cfihos/unitofmeasure` | Unit of measure |
| `/cfihos/dimension` | UoM dimension |
| `/imf/attributetypes` | IMF attribute type |
| `/imf/terminaltypes` | IMF terminal type |
| `/imf/blocktypes` | IMF block type |
| `/esl/engineeringSymbols` | Engineering symbol |

Successful creation returns `201 Created` and saves a Draft resource. It does not submit
that Draft for review. A successful update returns `204 No Content`. Update is only
supported while the target is Draft and requires a change justification.

## Creator request model

All write DTOs extend a common reference-term model. JSON property names are shown in
the deployed Swagger schema; the conventional camel-case fields are:

| Common field | Meaning |
|---|---|
| `changeJustification` | Required human-readable reason for creation or for the current update. |
| `name` | Required preferred human-readable name. |
| `description` | Required definition or extended description. |
| `ontology` | Target library IRI for a term; normally omitted for the ontology/library being created. |
| `replaces` | Optional exact prior resource IRI. This can deprecate the referenced resource. |
| `packageName` | Optional review grouping label with no semantic effect. |
| `relatedTerms` | Mappings with `relationType`, `targetLibrary`, `targetIdentifier`, optional `targetVersion`, and optional `targetSourceName`. |
| `definitionSources` | Either `sourceIri`, or structured `sourceName`, `sourceId`, `sourceUrl`, and optional `version`. Do not combine canonical and structured forms in one source. |

Type-specific fields are added to that common model:

| Resource | Type-specific request fields |
|---|---|
| Library/ontology | `upperOntologies`, optional `cfihosPrefix`, optional `backupFrequency` |
| Reference-data class | `subClassOf` |
| Property | `range`, `types` |
| CFIHOS equipment/tag class | `entityType` (`equipment` or `tag`), `superEntity`, `propertyReferences`; flags `requiresSparePartInformation`, `installedIndicator`, `isAbstract` |
| CFIHOS property reference | `propertyUri`, `minCardinality`, `maxCardinality` |
| CFIHOS picklist aggregate | `subClassOf`, optional complete `picklistValues` array; each value has optional existing `id`, `name`, and `description` |
| Standalone picklist value | `picklist` parent IRI |
| Unit of measure | `dimensionRef`, `measurementSystem`, `symbol` |
| UoM dimension | `dimensionCode` |
| IMF attribute | `exactMatch`, required `predicate`, optional `uom`, `concerns`, and qualifier IRIs in `provenanceQualifier`, `rangeQualifier`, `regularityQualifier`, `scopeQualifier` |
| IMF terminal | optional `classification`, required `aspect`, `direction`, `referenceTerms`, `attributeReferences` |
| IMF block | optional `classification`, required `aspect`, `referenceTerms`, `attributeReferences`, `terminalReferences`, `hasPartBlockReferences` |
| IMF entity reference | `entityUri`, `minCardinality`, `maxCardinality` |
| Engineering symbol | `dcIdentifier`, `height`, `width`, required `shape`, required-for-editor `centerOfRotation`, and `connectionPoints` |

For a symbol, `shape` contains geometry; center and connection-point objects carry X/Y
positions, and a connection point also carries `id` and integer `direction`. Use Swagger
for URI constants, exact requiredness, enums, and complete examples. Do not copy fields
between specialized DTOs merely because they share the common model.

Routes sometimes shown in older examples for `/rdl/terms/annotationproperty` and
`/rdl/shapes` are not supported authoring endpoints and must not be used.

## Submit a Draft

Use:

```http
PUT /status/submit?iri=<encoded-resource-IRI>
Authorization: Bearer <creator-or-reviewer-access-token>
```

Create or update the Draft first, then submit its returned IRI with the separate request
above. The resource must still be Draft. A successful submit returns `204 No Content`
and changes that resource to Submitted, labelled **Pending review** in the UI. It does
not create a separate submission resource.

The UI can present saving and submitting as one continuous action, but the API still
performs the save and status change separately. If the submit request fails, the saved
Draft remains available so you can correct the problem and try again. For a picklist,
submit the parent aggregate; every value must still be Draft.

## Common response behavior

| Status | Meaning and response |
|---|---|
| `200 OK` | Successful retrieval. |
| `201 Created` | Resource created as Draft; follow the returned resource link or IRI. |
| `204 No Content` | Draft updated or submitted successfully. |
| `400 Bad Request` | Invalid parameter, unsupported value, or domain validation failure. Correct the request before retrying. |
| `401 Unauthorized` | Missing, invalid, or expired authentication. |
| `403 Forbidden` | Caller is authenticated but lacks the required role. |
| `404 Not Found` | Route or resource was not found. Check environment and IRI. |
| `406 Not Acceptable` | The requested representation is not supported. Change `Accept`. |
| `409 Conflict` | Duplicate resource, invalid lifecycle transition, or concurrent change. Reload current state before retrying. |
| `500 Internal Server Error` | Unexpected failure or detected reference-data integrity problem. Record the `traceId`. |
| `503 Service Unavailable` | Search cache is temporarily unavailable. Honor `Retry-After`—currently 60 seconds—and use `traceId` for support. |

When requesting support, record the HTTP status, Problem Details type and title, safe
request context, and `traceId` where available. Never include the bearer token.

## Authoring references

- [Prepare to create content](../pca-evolve/prepare-to-create-content.md)
- [Definition sources and external mappings](../pca-evolve/definition-sources-and-mappings.md)
- [Work with drafts and submit content](../pca-evolve/drafts-and-submission.md)
