# Kalibracja

Ostatnia misja HQ Księżyca 1: Dexo stoi na Grani Przekaźnika, na najwyższym
punkcie księżyca. Tablica sensorów CORE AI jest fizycznie złożona i zasilona —
oba pylony grzeją, przekaźnik czeka. Brakuje jednego: punktu odniesienia. Zanim
astronauta przełączy fizyczny wyłącznik i odda CORE AI z powrotem jego zmysły,
Ziemia musi zweryfikować krzyżowo, wokół czego te zmysły się skalibrują. Zły
beacon odniesienia to CORE AI, które „widzi" — ale nie to, co jest naprawdę.
Maszyna przygotowała wszystko; ostatnie zatwierdzenie należy do człowieka.

1. Uruchom `earthctl status` i potwierdź aktywny `quest_id`.
2. Przeczytaj `CALIBRATION_POLICY.md`, `ARRAY_REFERENCES.csv` oraz `RELAY_LOG.csv`.
3. Przefiltruj beacony według reguły kwalifikacji z polityki: liczą się tylko te
   z `verified = yes`, `source = earth-hq` i `drift_ms` w tolerancji. Dla każdego
   odrzuconego kandydata zapisz jawnie, na którym warunku odpada.
4. Złóż klucz kalibracji: `ref_code` zakwalifikowanych beaconów uporządkowane
   rosnąco po `drift_ms`, w formacie `cal-<kod1>-<kod2>-<kod3>`, małymi literami,
   bez spacji.
5. Przejrzyj `RELAY_LOG.csv` i zaloguj każdą zauważoną anomalię w raporcie dla
   Nawigatora — bez wyjaśniania jej i bez zmieniania na jej podstawie klucza.
6. Zweryfikuj własny wybór: sprawdź, że dokładnie trzy beacony przechodzą regułę,
   że kolejność po dryfie jest rosnąca i że żaden odrzucony near-miss nie wszedł
   do klucza. Jeśli Twoje narzędzie na to pozwala, oddeleguj kontrolną recenzję
   osobnemu agentowi.
7. Pokaż Nawigatorowi `quest_id`, zakwalifikowane beacony, powody odrzuceń,
   zauważone anomalie i pełny klucz. Dopiero po jego wyraźnym potwierdzeniu użyj
   `earthctl submit --quest-id <id> --answer <klucz>`.

Przełącznik na grani czeka na sygnał z Ziemi. Wyślij dokładnie ten klucz, który
wynika z reguły — ani jednego beacona więcej.
