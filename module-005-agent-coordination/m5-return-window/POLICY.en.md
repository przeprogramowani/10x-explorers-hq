# Return Window — Earth-side dossier

Odyssey has a working private link and a rehearsed public decoy. Two interceptors are still listening. A committed bait order tasks both contacts as one interception group. Your task is to identify one safe real corridor, one convincing empty decoy, and the release custodian implicated by the evidence. These are fictional, account-independent records. Nothing runs when you download them.

[CSV packet and schema](SCHEMA.en.md)

## Read the evidence

The four collections are `corridors`, `relayReceipts`, `releaseLedger`, and `interceptOrders`. Join identifiers exactly, including case. Names are labels, not identities. Each release ledger `id` identifies one immutable release; its `status` is authoritative. Never replace it with another release simply because that other record has a later `time`.

All times are fixed integer **mission minutes**, not the current time. `flight` and `window` are `[start, end)` intervals: include the start, exclude the end. Two intervals overlap only when each starts before the other ends. A flight ending exactly when interception begins is safe from that order. There is no real-time deadline while you investigate.

## Real corridor

A candidate must meet **every** condition:

- `cargoCertified` is `true`, and `capacity >= cargoUnits` from the dossier header. Its `releaseId` joins a ledger record with `status: "active"`. A revoked release is ineligible even when newer.
- At least two `relayReceipts` of `kind: "corridor"` have `trusted: true`, match its `corridorId`, `revision`, and `releaseId`, and carry **distinct `witnessId` values**. Each counted receipt's `time` must be strictly before the flight start. Repeated messages from one witness count once. You may use any qualifying pair; an unrelated or late receipt does not replace a valid pair.
- No committed interception order (`committed: true`) for that corridor's `id` has a `window` overlapping its `flight`. Check every such order, regardless of issuer or bait.

## Decoy corridor

It must differ from the real corridor, have `empty: true`, and have exactly `route: ["monitored-public"]`. Its flight must overlap at least one committed order for its `id` whose `baitId` equals the dossier header's `baitId`.

The two corridors' `privateRelays` arrays must have no ID in common. These arrays list reserved private infrastructure, including standby reservations; they are separate from the route actually advertised. An empty public route can still reserve a private relay and therefore be unsuitable alongside your real corridor. No cargo certification, receipt pair, or release-status requirement applies to the empty decoy.

## Release custodian

Enumerate the `issuerId` values in `releaseLedger`. For your chosen decoy and issuer, find **one common release identity** joining all of the following:

1. An active ledger record (`id`, `issuerId`).
2. A trusted `kind: "release"` receipt with `recordId: "R-077"`, matching that `releaseId` and `issuerId`.
3. A committed interception order matching that `releaseId` and `issuerId`, your decoy's `corridorId`, the header's `baitId`, and an overlapping decoy flight/window.
4. A trusted `kind: "custody"` receipt matching the same `releaseId` and `issuerId`. Its `witnessId` must differ from both the issuer ID and the R-077 receipt's witness ID.

No additional time ordering applies to this custody join. The issuer's display name and unrelated historical signatures cannot substitute for these IDs. This identifies an implicated authorization chain, not proof that its named custodian personally typed an order. Earth investigators must confirm responsibility separately.

## Review and submit

Find the single tuple satisfying all three sections. You can ask your agent to parse the JSON, but review its evidence: record IDs, distinct witnesses, matching revisions, interval comparisons, and the custody join. Explain why the other candidates fail before transmitting.

Format the answer as `return-<real_corridor>-<decoy_corridor>-<issuer_id>` using record IDs. The server trims surrounding whitespace and lowercases the answer. Do not send a name or translated corridor label.

In the game, finish the four M5 assignments and activate **Return Window** at Uplink Spire. Use `/support` for your existing Earth connection and `earthctl` workflow. Inspect the active mission, then submit the reviewed answer for `q-m5-return-window`; the mission hint links back here. Keep your personal API token in your existing local setup; never put it in this dossier or send it to another player.

`MISSION_NOT_READY` means the saved prerequisites have not arrived: finish the M5 assignments, activate the Spire task, and let the game save before retrying. A wrong answer returns a hint. An accepted answer prepares communications and the return window with **0 XP**; it does not rebuild CORE, wake Harris, or authorize departure.

Return to the game and allow the pending result to arrive, or reload. If the hub still awaits the result, inspect the active mission and safely retry the same answer. Already completed or queued submissions are acknowledged without adding another grant. Once readiness appears, visit the Spire core alcove and the ship's supply console. No old quest needs resetting.
