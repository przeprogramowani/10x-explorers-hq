# Handoff Audit — policy v1

Splot collected “done” reports, but Moreau wants evidence of receipt and independent review. Find the one job with a valid completed handoff. All records are fictional; crew clocks deliberately disagree.

## Normative rules

1. `seq` is a unique acceptance number from one central ledger, shared across `assignments.csv`, `artifacts.csv` and `receipts.csv`. Compare only numeric `seq` values. `actorTime` is the author’s local clock and does not order records against one another. `metadata.csv` confirms this policy. There is no live deadline.
2. For each `jobId`, select the assignment with greatest `seq` in `assignments.csv`. Its `ownerId`, `receiverId` and `reviewerId` are authoritative. All three IDs must differ. An older assignment does not prove current responsibility.
3. For that job, select the artifact with greatest `seq` among `committed: true` rows. It must exist, have `seq` greater than the selected assignment and match its `ownerId`. Its `id` and `revision` define the current artifact. Do not choose an older artifact because it has more receipts. A `committed: false` row is not a release and does not replace the last committed row.
4. Two trusted receipts (`trusted: true`) are required, each with `seq` strictly greater than the selected artifact and matching `jobId`, `artifactId` and `revision`: one `kind: received` whose `witnessId` equals `receiverId`, and one `kind: reviewed` whose `witnessId` equals `reviewerId`. Both roles are necessary. A duplicate receipt, `sent`, self-review or an old revision’s acknowledgement cannot replace a missing role. Unrelated rows may be ignored if a qualifying pair exists.
5. Consider all jobs. Exactly one satisfies every condition. Answer: `handoff-<jobId>-<ownerId>-<artifactId>`, using the current assignment and artifact. The server trims surrounding whitespace and lowercases the answer.

## Evidence review

The agent compares assignment, last committed release and both receipts. An independent reviewer challenges the conclusion, especially ownership changes, revision and witness independence. The Navigator reviews `seq` values and rejected candidates before approving the answer. A “sent” message is not a work result.
