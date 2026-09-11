---
title: Operate hosted content
description: Agree ownership, external governance, versions, identifier stability, source updates, validation, and support for a PCA-hosted collection.
---

Hosting is an ongoing agreement between the authoritative content owner and PCA. The
technical platform can expose and index content, but the agreement must say who decides
meaning, releases, corrections, and retirement.

## Choose the governance model

| Model | Lifecycle shown by PCA | Decision authority |
|---|---|---|
| PCA-governed interactive content | Draft → Submitted/Pending review → Approved or Rejected; replacement can deprecate an older resource | PCA's applicable review process |
| Externally managed hosted content | Externally Managed; it does not enter the PCA Draft/review transition | The named external standard or collection owner |

Externally Managed does not mean ungoverned, approved by PCA, or technically inferior.
It means that users must consult the external owner's release and decision process.

## Preserve identifiers

- Treat resource IRIs as durable identifiers.
- Agree the `https://posccaesar.org/` namespace before publication.
- Do not reuse an IRI for a different meaning.
- Keep prior version identifiers resolvable where the agreement requires traceability.
- Use explicit version and replacement links rather than silently changing identity.

## Supply an update

1. The owner publishes or delivers the agreed source and release identification.
2. Re-validate PCA's [content host requirements](content-host-requirements.md).
3. Compare the update with the currently hosted release and explain intentional removals,
   replacements, or semantic changes.
4. PCA and the owner resolve validation or dependency failures before publication.
5. Publish through the agreed operational channel and verify search, HTML, authorized
   machine-readable retrieval, identifiers, and key dependencies.
6. Record release evidence and communicate material changes through the agreed channel.

Content updates follow the operational channel agreed by PCA and the content owner; they
are not performed through a self-service API.

## Failure and rollback planning

Before the first release, you and PCA will agree on:

- who can stop or approve publication;
- what happens when parsing, validation, or dependency checks fail;
- which previous release can be restored;
- how an affected identifier or consumer is communicated; and
- which information a support request must include.

If an update fails a check, PCA will keep the currently agreed release available while
you and PCA resolve the issue. A partially validated update will not be published simply
to preserve a schedule.

## Consumer communication

Before publication, you and PCA will agree how users are informed about the collection
owner, governance model, version, authoritative source, license, status meaning,
deprecation policy, and contact route. This information helps users decide whether a
resolvable resource is suitable for operational use.
