# Context Pack — policy v1

Echo is preparing a small packet for an agent checking archive persistence and receipt. The whole archive will not fit through the link. Select the least expensive sufficient document set, then subject it to independent criticism. All records are fictional.

## Normative rules

1. `metadata.csv` supplies `targetRevision` and a hard `budget` in abstract context units. `documents.csv` is the complete candidate set. Join IDs exactly; labels are not keys. Set cost is the sum of `units` for distinct selected documents, each counted once.
2. Every selected document must have exactly `targetRevision` and `authority: verified`. An older document or `draft` is ineligible even if cheap or claiming every topic.
3. Every claim in `claims.csv` with `required: true` needs at least one `support.csv` row whose `documentId` is selected, `claimId` matches and `verified: true`. A document title or a `verified: false` row is not evidence.
4. Include every dependency of each selected document from `dependencies.csv`: `documentId` requires `requiresDocumentId`. Apply this transitively until the set stops changing. Dependencies also incur cost and must satisfy the revision and authority rule. No row means no additional dependency.
5. Among sets meeting the rules and budget, minimize summed `units`; break ties by fewest documents; break remaining ties by the lexicographically smallest ID list after sorting it in ascending ASCII order. These are successive criteria, not a weighted sum.
6. Sort selected IDs in ascending ASCII order. Answer: `context-<id1>-<id2>-...`. Include required dependencies in the answer. The server trims surrounding whitespace and lowercases the answer.

## Evidence review

The agent proposes a set, cost and support for every claim. An independent reviewer receives the data and rules, not an answer to rubber-stamp: challenge a missing dependency, stale source or cheaper valid alternative. If a second agent is unavailable, conduct a separate review with fresh context. The Navigator checks the evidence table and candidate rejection reasons before transmission.
