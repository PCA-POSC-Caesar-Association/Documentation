---
title: Create Reference Library
---

This guide explains how to create and propose reference-library content through PCA.

## What this workflow covers

This workflow is used when you need to create structured ontology or reference-data content such as:

- subclasses or other class-based terms
- properties
- annotation properties
- SHACL shapes
- new ontology contexts

## What you should prepare first

Before you start, prepare:

- a clear name
- a clear description
- a justification for why the content is needed
- the target ontology or collection
- the parent or structural context, such as `subClassOf`, domain, range, or target class where relevant

## Step-by-step for interactive users

1. Confirm through [PCA Explore](../pca-explore/index.md) that the content does not already exist.
2. Decide which kind of content you need to create.
3. Open the relevant creation workflow in the platform.
4. Enter the required fields carefully.
5. Add optional structural information if your content type supports it.
6. Review the proposed values before submission.
7. Submit the content and keep the created IRI or confirmation for later follow-up.

## Step-by-step for technical users

If you use the API, the main reference-library creation endpoints include:

- `POST /rdl/terms/subclass`
- `POST /general/property`
- `POST /rdl/terms/annotationproperty`
- `POST /rdl/shapes`
- `POST /ontologies/domains`

Typical technical workflow:

1. Authenticate with the correct role.
2. Build the payload for the specific content type.
3. Include `changeJustification`, `name`, `description`, and `ontology` where required.
4. Add the type-specific structural fields.
5. Submit the payload and store the returned location or identifier.

## Practical advice

- Treat `changeJustification` as mandatory in practice, even where you are thinking mainly as a modeler rather than a reviewer.
- Be precise about the ontology you are writing into.
- Do not create near-duplicates just because wording differs slightly.

## See also

- [Choose an Evolve Workflow](choose-an-evolve-workflow.md)
- [PCA Govern](../pca-govern/index.md)
