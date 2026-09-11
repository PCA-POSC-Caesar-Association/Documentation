---
title: Definition sources and external mappings
description: Record definition evidence and validated semantic mappings to PCA, ISO, IEC, ECLASS, ETIM, UNSPSC, and other sources.
---

Definition sources and mappings answer different questions:

- A **definition source** says where the definition's wording or meaning came from.
- An **external mapping** relates the PCA resource to another identifier and states how
  closely their meanings correspond.

Do not assert a mapping merely because a source informed the definition.

## Supported source families

The authoring controls include source or mapping options for PCA content, ISO 15926-4,
IEC CDD, ECLASS, ISO 14224, STEPLIB, legacy `data.posccaesar.org` content, ETIM 10.0,
UNSPSC 26.0801, and an Other option for a source that does not fit a named family.

Selecting `data.posccaesar.org` as evidence or a mapping target does not by itself mean
that every identifier below that host is resolved or hosted by the current PCA platform.
Record the supplied identifier exactly and verify its access separately.

## Record a definition source

1. Select the organization, standard, catalogue, or Other.
2. Record the source URL or identifier where the form requests it.
3. Record a version or release when the source is versioned.
4. Confirm that the cited source supports the proposed wording and scope.
5. Avoid citing a search-results page when a stable source record is available.

PCA validates required URL, version, and external-ID structure for supported source
families. A technically valid source still needs domain review.

## Choose a mapping relationship

- Use **exact match** only when the two concepts can be substituted for the intended
  semantic purpose.
- Use **broader match** when the external concept has wider meaning than the PCA
  resource.

If neither is justified, keep the source evidence without asserting a mapping or ask a
domain reviewer which relationship is appropriate.

## ETIM applicability

The authoring lookup uses ETIM release 10.0 and validates entity type:

| PCA resource | ETIM target |
|---|---|
| CFIHOS+ equipment class | Equipment class (`EC`) |
| Unit of measure | Unit (`EU`) |
| Property | Feature (`EF`) with a compatible feature/value type |

Property compatibility depends on whether the PCA property is quantitative, Boolean,
or another controlled qualitative value. Use the options offered by the form and do not
force an incompatible ETIM feature type.

## UNSPSC applicability

The authoring lookup uses UNSPSC 26.0801. It applies to CFIHOS+ equipment classes and
supports Class or Commodity targets. A mapping to a UNSPSC **Class** must use broader
match rather than exact match.

## Select a mapping in the authoring form

Use the mapping search provided by the authoring form. It limits results to supported
catalogue versions and entity types, which helps avoid identifiers that look plausible
but do not apply to the resource being created. Preserve the selected identifier,
catalogue version, and entity type in the Draft.

## Review checklist

- The version and identifier belong to the selected external source.
- The source supports the definition actually written.
- The mapping target is the right entity type.
- Exact versus broader match is defensible.
- The same external assertion is not duplicated with conflicting relationships.
- A legacy host name is treated as an identifier/source, not as proof of current hosting.
