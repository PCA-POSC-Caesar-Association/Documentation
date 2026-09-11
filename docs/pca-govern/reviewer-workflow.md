---
title: Review a submission
description: Open the Reviewer queue, inspect the proposal and current dependencies, and prepare an approval or rejection decision.
---

Use this journey after the responsible governance process has appointed you as a
Reviewer for the relevant domain. The Reviewer role exposes **Review** in the application;
Creator and Reader alone do not authorize a decision.

## Review the submission

1. Open the review area of the platform.
2. Use the review overview to find Submitted/Pending review items.
3. Open the relevant item, package, or supported aggregate.
4. Inspect identity, definition, target library, creator provenance, change justification,
   relationships, sources, mappings, and replacement impact.
5. Inspect the dependency set presented for the proposed outcome.
6. Complete the responsible working-group or collection-owner decision process.
7. Choose approve or reject, acknowledge impact, and provide the decision justification.
8. Submit the decision and verify the resulting status.

## If the review changed while open

If the item, an aggregate member, or a relevant dependency changes after the decision
view loads, the API returns `409 Conflict`. Do not repeat the same decision blindly.
Reload, review the current set and latest updates, then record a new decision if it still
meets the governance requirements.

## Important scope note

The platform enforces access, lifecycle, required decision data, and consistency checks.
It currently does not replace the governance rules for domain authority,
cross-organization participation, or working-group agreement. These will be added
iteratively over time. Before recording the result, use
[Check dependencies and record an outcome](dependency-review-and-status-updates.md) and
the hub's [content review process](/governance/pca-content-review-process/).
