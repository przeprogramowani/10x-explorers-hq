# Change Impact — policy v1

Kern proposes an internal change to batch processing order. Public IDs must remain durable, including after asynchronous receipt. Determine impact in the declared graph and the smallest characterization-test set. This is a fictional investigation; do not modify a real application.

## Normative rules

1. The change starts at `changedNode` in `metadata.csv`. A `dependencies.csv` row means `consumerId` depends on `dependencyId`. Impact travels from dependency to consumer, transitively, for both `transport` values: `sync` and `async`. The changed node is included. This graph is complete for the mission; do not invent edges.
2. A public contract is impacted if and only if its `nodeId` in `contracts.csv` is reached. Use contract and node `id` values, not `displayLabel`. Two “Delivery” labels create neither a dependency nor shared identity.
3. `tests.csv` is the complete candidate set. Only `status: verified` and `kind: characterization` qualify. The `contractIds` list uses `|` separators and names the specific invariants tested. A label snapshot or draft test does not replace a behavior test.
4. Select distinct qualifying tests with summed `cost` no greater than metadata `maxCost`, whose combined `contractIds` cover every impacted contract. Covering an additional contract is allowed. Each test incurs cost once.
5. First minimize the number of tests, then summed cost, then break remaining ties by the lexicographically smallest ID list sorted in ascending ASCII order.
6. Answer: `impact-<test1>-<test2>-...`, with test IDs sorted in ascending ASCII order. The server trims surrounding whitespace and lowercases the answer.

## Evidence review

The agent traces impact paths and proposes coverage. An independent reviewer especially checks the asynchronous edge and the distinction between durable IDs and display names, challenging any missed contract. The Navigator reviews paths, selected tests and rejected alternatives. This is a proposal to protect a change, not authorization to deploy it.
