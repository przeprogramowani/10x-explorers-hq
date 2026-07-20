# Samodzielna recenzja planu

Ostatnia misja HQ Księżyca 2: plan „WYDOBYCIE BETA" jest kompletny — kontrakt,
kamienie milowe, aneks architektury, wykonanie pod kontrolą — i czeka przy
rdzeniu planowania na zatwierdzenie. Zanim Astronauta dotknie pulpitu
zatwierdzeń, plan musi przejść samodzielną recenzję: autorzy są jedynymi
ludźmi w promieniu dwustu milionów kilometrów, więc Nawigator recenzuje
własną pracę jak pracę obcego, któremu nie ufa. Transmisja idzie łączem
zapasowym Moreau: wraca wyłącznie werdykt.

1. Uruchom `earthctl status` i potwierdź aktywny `quest_id`.
2. Przeczytaj `REVIEW_CHECKLIST.md`, a następnie `REVIEW_PACKET.md` — w tej
   kolejności. Recenzent najpierw uzbraja kryteria, potem czyta tekst.
3. Oceń każdą pozycję normatywną `R-xx` względem wszystkich pięciu kryteriów
   defektu. Sekcje A i B pakietu to kontekst odniesienia dla kryteriów
   3 i 4. Zapisz przy każdej pozycji: defekt (które kryterium) albo czysta
   (dlaczego).
4. Przejrzyj listę defektów po raz drugi w roli adwokata planu: czy któraś
   pozycja tylko wygląda na defekt (wartość graniczna, nota niewiążąca,
   powtórzenie)? Jeśli Twoje narzędzie na to pozwala, oddeleguj tę
   kontrrecenzję osobnemu agentowi.
5. Przygotuj odpowiedź: identyfikatory wszystkich defektów, posortowane
   rosnąco, rozdzielone przecinkami, bez spacji.
6. Pokaż Nawigatorowi `quest_id`, listę defektów z przypisanymi kryteriami
   oraz pozycje uniewinnione, a po potwierdzeniu użyj `earthctl submit`.

Od tego werdyktu zależy pierwsza ludzka decyzja zatwierdzenia w historii
węzła PN-0. Rdzeń czeka na plan bez defektów — i na człowieka, który to
podpisze.
