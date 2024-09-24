# Versioning workshop 11.09.2024

## Draft

There is a consensus that multiple parties will likely have an interest in updating or creating new types. The key question is whether PCA should offer functionality for collaboration on types, allowing contributors to share and work together on drafts. A significant issue is determining who should have the authority to edit and own these drafts. Should ownership belong to an individual or the organization? One argument is that organizational ownership would offer better resilience (e.g., if the individual responsible for the draft leaves the organization).

**Conclusion:** it would be beneficial for PCA to provide a draft environment where users can view their drafts in the context of the library, complete with IDs and other relevant details. However, this is a more long-term goal. Additionally, there is agreement that data with Draft status should remain inaccessible to others within PCA until it is submitted.

## Submitted

Should it be possible to withdraw submissions and continue working on them as drafts?
Should it be possible to mark submissions as invalid, allowing them to be resubmitted? This approach would simplify the process, especially if the type hasn’t been used by others in the system but its meaning has changed. It would also generate a new ID.

**Conclusion:** there will likely be instances where data in the submitted state needs to be modified before approval. Therefore, there must be a way to submit replacements while the data is still in the submitted state. If a submission is replaced at this stage, the original will be marked as Deprecated, indicating that it is no longer valid and should not be considered.

This reflects the current situation: Draga’s data in the PCA library is marked as Submitted, and they will continue updating it until it is ready for approval.

## Rejected

Is it necessary to retain a history of rejected resources? One reason to keep all rejected resources in the library is the possibility that a user may have based their work on the resource while it had Submitted status, prior to its rejection. Additionally, if the assumptions for a resource change, previously rejected resource may become relevant again, prompting the need to resubmit the same resource that was once rejected.

**Conclusion:** the recommendation is that a Rejected resource cannot be replaced, and any replacement relationships will be linked only to Approved resources. Rejected resouces will function as leaf nodes in the hierarchy. If an attribute is rejected, it will trigger the rejection of the terminal and blocks that use it. Similarly, if a terminal is rejected, all associated blocks will be rejected. If a block is rejected, all dependent blocks will also be rejected.

## Splitting:

A brief discussion on how to split compound concepts when separate parts of a combined expression are needed. To simplify this process, users should submit new terms for each component independently, without referencing the original combined expression. For example, if the expression **Pressure-hand grenade** is required, the user should submit **Pressure** and **Hand grenade** as independent terms, which can later be combined as needed.

# Conclusion:

The conclusion of this workshop is PCA's approach on resource versioning. The documentation of the approach can be found as `versioning.md`, located in this repository.
