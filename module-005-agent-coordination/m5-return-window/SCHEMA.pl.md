# Schemat pakietu CSV — Okno powrotu v1

To wierna projekcja bieżącego [dossier platformy](https://platforma.przeprogramowani.pl/game/missions/m5-return-window/v1/dossier.json), a nie osobne zadanie. Kolekcje i kolejność wierszy odpowiadają oryginalnemu JSON. Niczego nie uruchamiaj podczas odczytu.

Pliki CSV używają przecinka, nagłówka, UTF-8 i standardowego cytowania CSV: podwójny cudzysłów wewnątrz cytowanego pola zapisuje się podwójnie. Najpierw sparsuj CSV; nie dziel wiersza po każdym przecinku. Następnie:

- `metadata.csv` zawiera pola nagłówka: `key` to nazwa pola, `jsonValue` to pełna wartość JSON (także cudzysłowy wokół tekstu).
- Cztery pozostałe pliki tworzą tablice pod nazwami równymi nazwom plików bez `.csv`.
- Kolumny wymienione jako Integer są liczbami całkowitymi; Boolean ma dokładnie `true` albo `false`; JSON array jest pełną tablicą JSON.
- Puste pole w kolumnie Optional oznacza **brak właściwości**, nie pusty tekst i nie `null`. Nie dodawaj tej właściwości podczas rekonstrukcji.
- Tylko `interceptOrders.baitId` dopuszcza `null`: dosłowny tekst `null` oznacza wartość JSON null. Pozostałe niepuste pola niewymienione jako liczby, wartości logiczne lub tablice są tekstem.
- Puste tablice to `[]`. Nie zmieniaj wielkości liter ID ani kolejności tablic. Nazwy i wartości porównuj według polityki, nie według wyglądu CSV.

| Collection | Integer | Boolean | JSON array | Nullable | Optional (absent when empty) |
| --- | --- | --- | --- | --- | --- |
| corridors | revision, capacity | cargoCertified, empty | route, privateRelays, flight | — | — |
| relayReceipts | revision, time | trusted | — | — | corridorId, revision, recordId, issuerId |
| releaseLedger | time | — | — | — | — |
| interceptOrders | — | committed | window | baitId | — |

## Pliki

- [corridors.csv](corridors.csv)
- [relayReceipts.csv](relayReceipts.csv)
- [releaseLedger.csv](releaseLedger.csv)
- [interceptOrders.csv](interceptOrders.csv)
- [metadata.csv](metadata.csv)
