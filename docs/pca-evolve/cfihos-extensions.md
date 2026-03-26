---
title: CFIHOS Extensions
---

This guide explains how to use PCA to extend CFIHOS in a controlled way.

## What this workflow is for

Use this workflow when existing CFIHOS content does not fully cover your needs and you want to create extensions that remain technically aligned with the broader CFIHOS structure.

## Typical content types

Examples include:

- entities such as equipment or tags
- properties
- picklists and picklist values
- dimensions
- units of measure

## Step-by-step for interactive users

1. Start in [PCA Explore](../pca-explore/index.md) and confirm that the needed content does not already exist.
2. Decide which CFIHOS extension type you need.
3. Open the matching creator workflow in the platform.
4. Fill in the required descriptive and structural information.
5. Check carefully that the content really belongs in the intended CFIHOS context.
6. Submit the proposal for review.

## Step-by-step for technical users

Relevant API endpoints include:

- `POST /cfihos/entity`
- `POST /cfihos/picklist`
- `POST /cfihos/picklistvalue`
- `POST /cfihos/unitofmeasure`
- `POST /cfihos/dimension`
- `GET /cfihos/ancestors/properties`

A practical workflow is:

1. Use the read endpoint to inspect inherited properties if needed.
2. Prepare the new extension payload.
3. Submit the proposed content with the appropriate creator permissions.
4. Track the resulting item through review.

## See also

- [Choose an Evolve Workflow](choose-an-evolve-workflow.md)
- [IMF Types](imf-types.md)
