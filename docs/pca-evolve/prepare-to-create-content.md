---
title: Prepare to create content
description: Check Creator access, duplicates, ownership, identifiers, evidence, mappings, and lifecycle consequences before authoring.
---

Complete these checks before opening a form or building an API payload. They apply to
reference data, CFIHOS+, IMF, and engineering symbols.

## 1. Confirm access and scope

- Your PCA account must have Creator.
- Confirm which library or collection you may extend.
- Confirm whether the content should use an interactive Creator workflow or be onboarded
  as a separately managed [content host](../pca-host/index.md).

## 2. Search before creating

Search for the intended name, synonyms, identifier, parents, and close alternatives.
Reuse content where possible. If the need is a new version, identify the exact
resource it replaces rather than creating an unrelated near-duplicate.

## 3. Prepare common information

Most authoring forms require or support:

| Information | Guidance |
|---|---|
| Name | Use the domain's naming convention and make it distinguishable in search. |
| Description or definition | State clearly what the resource means. |
| Target library | Select the governed collection that will own the new resource. An ontology/library itself does not have this field. |
| Change justification | Explain the need, due diligence, intended use, and material changes. Required for creation and update. |
| Package name | Optional grouping for related review work. Do not use it as a substitute for relationships. |
| `Replaces` | Optional IRI of the exact prior resource. Verify it carefully because the prior resource will be marked as Deprecated. |
| Related terms | Add relationships that help users and reviewers understand context. |
| Definition sources | Record evidence for the wording and scope of the definition. |
| External mappings | State the target identifier and whether the semantic match is exact or broader. |

The selected target library can be retained for the current Creator workspace session.
Check it whenever you change workspaces or author for more than one collection.

## 4. Prepare type-specific relationships

- A reference-data class normally needs its structural parent context.
- A property needs the relevant domain, range, or specialized CFIHOS value constraint.
- A CFIHOS equipment or tag class needs its super-entity and property/cardinality choices.
- IMF terminals and blocks compose references with cardinalities; attributes use a
  predicate, optional UoM, and qualifier combinations.
- An engineering symbol needs valid SVG path geometry and a centre of rotation before it
  can be submitted.

Use the domain guide to collect these values before an API call.

## 5. Understand visibility and states

Creating content persists it as Draft and assigns a resource IRI. Draft content is
searchable. It is not approved, and it remains editable only while Draft. Submission is
a separate action that locks Creator editing and changes the status to Submitted/Pending
review.

For more details on this, read
[Roles, access, and content states](../roles-access-and-content-states.md) and the
governance process.

## 6. Choose evidence and mappings deliberately

A definition source explains where wording or meaning came from. A mapping asserts a
relationship to another identifier. See
[Definition sources and external mappings](definition-sources-and-mappings.md) for more
details.

## Ready checklist

- [ ] Creator access and target ownership are confirmed.
- [ ] Existing and similar resources have been searched.
- [ ] The correct specialized workflow is selected.
- [ ] Required labels, definitions, relationships, and justification are ready.
- [ ] Sources, external versions, and mapping relation types are verified.
- [ ] Any `Replaces` consequence has been reviewed.
- [ ] The team understands that the first persisted state is Draft, not Submitted.
