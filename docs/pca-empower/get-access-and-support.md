---
title: Get access and support
description: Request the right PCA role or integration setup and send safe, actionable diagnostic information when you need help.
---

Libraries, Search, and HTML content pages do not require a PCA role. Use the table to
identify what your next task requires, then send the request details below to
[PCA support](mailto:support@posccaesar.org).

| Need | Request |
|---|---|
| Search, browse, and read HTML content pages | No role |
| Use search or retrieval APIs, including JSON, RDF, symbols, or IMF SHACL | Reader |
| Create, edit, and submit Draft content | Creator |
| Record review outcomes | Reviewer appointment through the governance process |

## Request user access

Include:

- your organization and PCA account identity;
- the environment you need;
- the task and requested role;
- the target library or content family;
- whether you intend to use the interactive interface, API, or both; and
- an owner and expected duration if access is temporary.

## Request an integration

PCA supports approved registered applications and services. State the endpoint families,
expected volume, calling organization, data handling, credential owner, and operational
contact. PCA will confirm the intended access, register the
application, and supply the environment-specific authentication details. Do not build
an integration service around a copied user token; follow
[Authentication and authorization](../pca-consume/api-authentication.md).

## Request content hosting

Include the content owner, governance model, namespace, source format, license, release
cadence, dependencies, and public audience. Begin with [Plan a hosted collection](../pca-host/get-started-with-hosting.md).

## Report a problem safely

Include:

- environment and UTC timestamp;
- page or endpoint path, method, and safe parameters;
- expected and actual result;
- HTTP status, Problem Details title/type, `traceId`, and `Retry-After` if present;
- resource IRI and content status where relevant; and
- minimal reproduction steps.

Never send an access token, password, client secret, or private content in a screenshot.
For `503`, wait for the indicated `Retry-After` before retrying. For `409`, reload current
resource or review state before deciding whether a retry is safe.
