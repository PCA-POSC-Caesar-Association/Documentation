---
title: Check dependencies and record an outcome
description: Assess approval or rejection impact, handle picklist aggregates and stale review data, and record a justified status change.
---

A review outcome can affect referenced or dependent content, not only the proposal shown
at the top of the page. The platform therefore binds the decision to the exact review
item set and version that the Reviewer assessed.

## Check impact and record the decision

1. Open the submitted review item.
2. Start the approval or rejection action.
3. Inspect approval or rejection dependencies and any aggregate members.
4. Confirm that every review item is present once and that the set matches the current
   proposal.
5. Confirm that the dependency impact is understood under the applicable governance
   rules.
6. Provide a specific decision justification.
7. Record the Approved or Rejected status and verify the result.

## What the platform checks

The review implementation includes support for:

- viewing submitted items
- seeing approval dependencies
- seeing rejection dependencies
- requiring decision justification and dependency-impact acknowledgement.

## Picklist aggregate behavior

Review the picklist parent and all values together. The values are not separately
submitted decisions. If an aggregate member changes, reload the complete aggregate before
deciding.

## Replacement and deprecation

When a proposal declares `Replaces`, assess both the proposed resource and the effect on
the referenced version. The old identifier remains resolvable for traceability but can be
marked Deprecated. Confirm that the relationship is exact before approval.

These consistency checks prevent a valid decision from being applied to a different
item set than the one assessed. They do not replace domain judgement or the applicable
governance process. Return to [Review a submission](reviewer-workflow.md) for the full
Reviewer journey.
