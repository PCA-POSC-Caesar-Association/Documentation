---
title: Work with drafts and submit content
description: Save, reopen, update, and submit Creator Drafts safely, including IMF batches, CFIHOS picklists, and engineering symbols.
---

Creation and submission are separate operations. **Save as Draft** persists an
addressable resource that can be searched and edited. **Submit for review** moves the
resource to Submitted/Pending review and locks Creator editing.

## Standard interactive flow

1. Complete the form and choose **Save as Draft**.
2. Keep the generated IRI and use **View draft** to open its content page.
3. Confirm status, target library, definition, relationships, sources, and mappings.
4. Choose **Edit this resource** for a supported Draft type.
5. Enter a new change justification and choose **Update resource** or save the updated
   Draft.
6. When no unsaved changes remain, choose **Submit for review** and confirm.
7. Verify that the content page now shows Submitted or **Pending review**.

If you choose Submit while a supported editor still has unsaved changes, the application
saves the Draft first and then requests the transition. If saving succeeds but submission
fails, the Draft remains addressable; open it and retry only the submit step.

## API flow

1. Create with `POST` on the resource-family route and Creator authorization.
2. Store the returned Draft IRI or location.
3. Update only while Draft using `PUT <same-route>?iri=<encoded-Draft-IRI>`.
4. Supply a change justification for each update.
5. Submit with:

```http
PUT /status/submit?iri=<encoded-Draft-IRI>
Authorization: Bearer <creator-access-token>
```

A successful create returns `201 Created`; update and submit return `204 No Content`.
Treat `409 Conflict` as a lifecycle, duplicate, aggregate, or concurrency conflict. Read
current state before deciding whether to retry.

## Rules by resource type

### IMF attribute batches

One qualifier selection can create several candidate attributes. Successful Drafts are
not rolled back when another candidate fails. Record successes and retry only the missing
candidate after searching for duplicates.

### CFIHOS+ picklists

Manage values through the parent picklist and submit the parent aggregate. Every value
must be Draft; values are not submitted as independent review items.

### Engineering symbols

The symbol needs valid geometry, required metadata, a target symbol library, and a centre
of rotation before Save as Draft or Submit. Connection points are optional. An existing
Draft can be edited; a submitted symbol is locked.

## What cannot be edited through this flow

- Submitted/Pending review content;
- Approved, Rejected, or Deprecated content in place;
- Externally Managed content without PCA Draft provenance; and
- resource types for which the page does not expose a supported editor.

To supersede an existing resource, create a new proposal with a verified `Replaces` IRI.
Be aware that the referenced resource is marked Deprecated by the replacement operation.

## There is no withdraw promise

The documented platform transition does not include a Creator action that withdraws a
Submitted resource back to Draft. Contact PCA if a submitted proposal must be stopped;
do not build automation around an assumed reverse transition.

## Continue to governance

After submission, a Reviewer assesses the current resource and its dependencies. A stale
review action is rejected if the reviewed items changed while the decision view was open.
See [Review and approve changes](../pca-govern/index.md).
