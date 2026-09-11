---
title: Plan a hosted collection
description: Choose PCA Host versus interactive authoring and prepare ownership, namespace, RDF, licensing, dependencies, and update operations.
---

Choose PCA Host when you already maintain a collection and want PCA to make it
resolvable, searchable, and reusable. Begin before finalizing namespaces or publication
files, because onboarding must confirm governance, rights, and operations as well as
technical validity.

Typical examples include:

- a standards organization publishing a digital standard through PCA
- an enterprise publishing its own domain ontology or corporate standard
- a content owner providing RDF that should be hosted, validated, and made available through PCA

Use the Creator workspace instead when you need to create individual resources as
Draft, submit them, and receive PCA review outcomes.

## Step-by-step

1. Describe the collection, intended audience, and why PCA should publish it.
2. Name the authoritative owner and technical/operational contacts.
3. Decide whether governance is PCA-managed or externally managed.
4. Confirm rights to publish, license conditions, and public visibility.
5. Agree the canonical ontology and resource namespace before minting final IRIs.
6. Identify the authoritative source, release/version convention, expected update
   frequency, and how corrections are supplied.
7. List external dependencies and verify that imported ontologies are accessible.
8. Prepare Turtle with one ontology and one RDF graph per file.
9. Validate every requirement in [Content host requirements](content-host-requirements.md).
10. Agree initial publication, update validation, failure handling, and support contacts
    with PCA.

Host upload and management are not self-service. Contact PCA for onboarding and validate
the namespace and content structure early, especially when deciding whether the
collection is a standard-aligned ontology, a general PCA ontology, or another RDF
package. After the plan is agreed, use the
[content host requirements](content-host-requirements.md) to prepare the files and
[operate hosted content](hosted-content-lifecycle.md) to plan updates.
