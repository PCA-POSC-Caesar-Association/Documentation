---
title: Create IMF attribute types
description: Create one or more Draft IMF attribute types from predicates, units, and qualifier combinations, then recover safely from partial success.
---

An IMF attribute type qualifies a predicate so that it can be reused consistently in
terminal and block constraints. Its displayed name can be generated from the selected
predicate and qualifier combinations.

## Prepare the attribute

- Target library and change justification.
- Predicate or reference-data term that expresses the property.
- Optional unit of measure.
- Any applicable qualifier values:

| Qualifier dimension | Supported choices in the authoring flow |
|---|---|
| Range | Average, minimum, maximum, nominal, normal |
| Regularity | Absolute, continuous |
| Provenance | Calculated, measured, specified, calibration |
| Scope | Design, operating |

Selecting several values can generate several candidate attribute types. Review every
generated combination before saving.

## Create in the UI

1. Open **Create > IMF > Attribute type**.
2. Select the target library, predicate, optional UoM, and qualifier combinations.
3. Review the generated candidates and add shared justification and source context.
4. Select **Save as Draft**.
5. Follow the result links to inspect each created Draft.
6. Update an individual Draft if needed, then submit it for review.

## Handle partial batch success

Candidate creation is not all-or-nothing. If some combinations succeed and another
fails, the successful Drafts remain created. Record their IRIs, correct the failing
candidate, and retry only what is missing. Search before retrying so you do not create
duplicates.

## Use the API

- Create: `POST /imf/attributetypes`
- Update Draft: `PUT /imf/attributetypes?iri=<encoded-Draft-IRI>`
- Submit: `PUT /status/submit?iri=<encoded-Draft-IRI>`

Use the deployed Swagger schema for qualifier and reference objects. A batch client must
handle partial results explicitly and reconcile successful Drafts before retrying.

## Before submission

- The predicate has the intended semantics.
- The UoM is compatible with the predicate where one is supplied.
- Every qualifier combination is meaningful rather than merely possible.
- Generated candidates do not duplicate existing content or each other.
