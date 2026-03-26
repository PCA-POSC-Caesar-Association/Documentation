---
title: API Authentication
---

This guide explains how to approach authenticated use of PCA APIs.

## Why this guide matters

Swagger can show you endpoints, but it does not by itself explain the access model or the difference between user-based usage and service-to-service usage.

## Default model: user-based authorization

For most external users, the normal starting point is user-based authorization.

This means:

1. A human user signs in through the relevant identity flow.
2. The user receives the permissions needed for the intended workflow.
3. API calls are made on behalf of that user.

This model works well when:

- a person is actively using the platform
- actions should reflect the permissions of an individual user
- traceability of user actions matters

## Role-based access

Access depends on the role and workflow involved.

For external users, the most relevant API usage is mainly tied to:

- consumption of content
- externally relevant evolve workflows

Do not assume that internal governance-related operations are exposed for external integration.

## Application or service authentication

Where there is a valid business and technical need, PCA can also set up application or service authentication on request.

This is useful when:

- an integration runs unattended
- a background service needs access
- a workflow should not depend on an active user session

The exact setup depends on the integration scenario and is handled case by case.

## Recommended onboarding path

1. Read the relevant service guide first.
2. Confirm whether your usage is interactive, programmatic, or unattended.
3. Use user-based authorization by default unless PCA has agreed on a service/application setup with you.
4. Then use Swagger for endpoint-level details.

## See also

- [Get Content Through the API](get-content-through-the-api.md)
- [PCA Evolve](../pca-evolve/index.md)
