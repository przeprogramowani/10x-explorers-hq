# CSV packet schema — Return Window v1

This faithfully projects the current [platform dossier](https://platforma.przeprogramowani.pl/game/missions/m5-return-window/v1/dossier.json); it is not a separate puzzle. Collections and row ordering correspond to the original JSON. Reading requires no execution.

CSV uses commas, a header, UTF-8 and standard CSV quoting: a double quote inside a quoted field is doubled. Parse CSV first; do not split rows at every comma. Then:

- `metadata.csv` holds the top-level fields: `key` names the field, `jsonValue` is its complete JSON value (including quotation marks around strings).
- The other four files create arrays named after the filenames without `.csv`.
- Integer columns below are integers; Boolean is exactly `true` or `false`; JSON array is a complete JSON array.
- An empty Optional column means **the property is absent**, not an empty string or null. Omit that property when reconstructing.
- Only `interceptOrders.baitId` is nullable: literal `null` means JSON null. Other nonempty fields not listed as numeric, boolean or arrays are strings.
- Empty arrays are `[]`. Preserve ID case and array order. Compare names and values using the policy, not the visual CSV layout.

| Collection | Integer | Boolean | JSON array | Nullable | Optional (absent when empty) |
| --- | --- | --- | --- | --- | --- |
| corridors | revision, capacity | cargoCertified, empty | route, privateRelays, flight | — | — |
| relayReceipts | revision, time | trusted | — | — | corridorId, revision, recordId, issuerId |
| releaseLedger | time | — | — | — | — |
| interceptOrders | — | committed | window | baitId | — |

## Files

- [corridors.csv](corridors.csv)
- [relayReceipts.csv](relayReceipts.csv)
- [releaseLedger.csv](releaseLedger.csv)
- [interceptOrders.csv](interceptOrders.csv)
- [metadata.csv](metadata.csv)
