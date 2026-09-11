---
title: Roles, access, and content states
description: Understand access without a role, Reader and Creator permissions, authentication, and the lifecycle states shown by the PCA platform.
---

PCA separates **access roles** from **content states**. Your role determines which
actions and representations you can access. A resource's state records where that
resource is in its lifecycle.

## Access at a glance

| Access | Interactive capabilities | API capabilities |
|---|---|---|
| No PCA role | Open Libraries and Search, search and filter content, open HTML content pages, and inspect status and relationships | No API access |
| Reader | Continue to use the interactive reading journey | Search and retrieve supported machine-readable representations |
| Creator | Use the Reader retrieval workflows, plus the Create workspace, Draft authoring, Draft editing, and submission for review | Search and retrieve data, create and update supported content, then submit Draft resources |
| Reviewer | Review submitted content, inspect effects on dependencies, and approve or reject with justification | Governance operations intended for the review application |

## What is public

You can use these capabilities without a PCA role:

- browse Libraries and Search;
- open reference-data resources as HTML;
- inspect their status, provenance, and relationships before deciding whether to use
  them.

## What Reader adds

Reader is for programmatic consumption of protected data representations. Across PCA's
supported endpoints, these include JSON, JSON-LD, Turtle, TriG, N-Triples, RDF/XML,
and N-Quads. Not every endpoint supports every format; consult the
[API endpoint and error reference](pca-consume/api-reference.md) for the formats that
apply to each endpoint family.

Reader does not add the Create workspace and does not authorize content changes.

## What Creator adds

Creator enables the supported authoring workspaces and write APIs. A Creator can:

- create a reference-data library or ontology;
- create reference-data classes and properties;
- create CFIHOS+ equipment classes, tag classes, properties, picklists, units of
  measure, and dimensions;
- create IMF attribute, terminal, and block types;
- create or edit engineering symbols;
- save new content as Draft;
- reopen and update supported Draft resources;
- submit Draft resources for review.

Creator does not authorize approval or rejection. Submission hands the resource to a
Reviewer workflow.

## How authorization is applied

The PCA web application signs people in through Microsoft identity. API clients use an
OAuth 2.0 bearer access token, whether the caller is a person or a PCA-registered
application. The API checks the role in that identity.
[Authentication and authorization](pca-consume/api-authentication.md) explains the user,
Swagger, and registered-application flows.

## Content states

| State | Meaning | Available actions by role |
|---|---|---|
| `Draft` | The resource exists and can be discovered, but has not entered formal review. | It can be inspected in the browser. A Creator can edit, save, or submit supported content. |
| `Submitted` | The resource is in the review queue. The UI may label this **Pending review**. | Read only, editing not available. A Reviewer can assess it and record an outcome. |
| `Approved` | An authorized review has accepted the resource and recorded its decision. | It can be inspected and used. A Creator can prepare a later replacement but cannot edit the approved resource in place. |
| `Rejected` | Review did not accept the proposal in its current form. | The outcome remains visible. A Creator can prepare a new proposal when appropriate. |
| `Deprecated` | The resource remains resolvable for traceability but is no longer preferred. | It remains visible so users can follow replacement links to the preferred version. |
| `ExternallyManaged` | PCA exposes content governed outside PCA's own lifecycle. The UI can display **Externally managed** when PCA provenance is absent. | Read only. It cannot be edited or submitted through the PCA Draft workflow. |

Draft content being searchable is not a quality approval. Always inspect status before
reuse. If you create a replacement, verify the `Replaces` relationship carefully: the
referenced resource is marked Deprecated as part of the replacement operation.

## Next steps

- [Find and understand data](pca-explore/index.md)
- [Use data in applications](pca-consume/index.md)
- [Prepare to create content](pca-evolve/prepare-to-create-content.md)
- [Work with drafts and submit content](pca-evolve/drafts-and-submission.md)
