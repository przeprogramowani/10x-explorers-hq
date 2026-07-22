# Polityka kalibracji tablicy — Grań Przekaźnika

Tablica sensorów CORE AI jest złożona i zasilona na grani Księżyca 1, ale jej
punkt odniesienia jest tak dobry, jak beacony, na których go oprzemy. Ślepe
zaufanie pierwszemu odczytowi to skalibrowanie zmysłów CORE AI wokół fałszywego
sygnału — a po mitygacji nie ma jak tego wychwycić z powierzchni. Ziemia
przechowuje listę beaconów kandydujących (`ARRAY_REFERENCES.csv`). Tylko część z
nich nadaje się na odniesienie.

## Zasada kwalifikacji beacona

Beacon liczy się do klucza kalibracji **wyłącznie**, gdy spełnia jednocześnie
wszystkie trzy warunki:

1. `verified = yes` — odczyt potwierdzony niezależnie przez Ziemię.
2. `source = earth-hq` — pochodzi z sieci odniesienia Ziemi (nie z przekaźnika
   VOID, nie z sondy Odyssey).
3. `drift_ms` **nie większy niż 40** — dryf czasowy w tolerancji kalibracji
   (wartość dokładnie 40 ms jeszcze się kwalifikuje).

Beacon, który nie spełnia choćby jednego warunku, jest odrzucony. Zapisz jawnie,
na którym warunku odpada każdy odrzucony kandydat — kuszące near-missy (dobry
dryf, ale zły `source`; właściwe źródło, ale `verified = no`; poprawne poza
tolerancją dryfu) są w danych celowo.

## Format klucza

`cal-<kod1>-<kod2>-<kod3>` — prefiks `cal-`, następnie `ref_code` trzech
zakwalifikowanych beaconów **uporządkowane rosnąco po `drift_ms`**, rozdzielone
myślnikiem. Bez spacji, małymi literami. Przykład struktury (nie dane):
`cal-<najmniejszy dryf>-<środkowy>-<największy>`.

## Ślad uzgodnień

`RELAY_LOG.csv` to dziennik uzgodnień sesji kalibracji. Zaloguj każdą anomalię,
którą w nim zauważysz, w raporcie dla Nawigatora — ale **nie** próbuj jej
wyjaśniać ani na jej podstawie zmieniać klucza. Klucz zależy wyłącznie od
beaconów zakwalifikowanych regułą powyżej.
