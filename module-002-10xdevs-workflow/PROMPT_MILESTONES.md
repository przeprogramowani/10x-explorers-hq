# Kamienie milowe MVP

Pierwsza misja HQ Księżyca 2: kontrakt planu „WYDOBYCIE BETA" jest zarejestrowany
w węźle PN-0, ale zajezdnia etapowa stoi zamrożona, a Stoker B-6 pilnuje resztek
budżetu cieplnego. Astronauta czeka na miejscu — to Nawigator tnie plan na
kamienie milowe. Transmisja idzie łączem zapasowym Moreau przez Odyssey:
ładunek musi być minimalny i różnicowy, a odpowiedź Ziemi zweryfikuje bloczek
jednorazowy.

1. Uruchom `earthctl status` i potwierdź aktywny `quest_id`.
2. Przeczytaj `THAW_BUDGET.md` oraz `MILESTONE_CANDIDATES.csv`.
3. Wyznacz łańcuch odmrożeń: najmniejszą uporządkowaną sekwencję kamieni,
   która realizuje cel minimalny zajezdni i spełnia wszystkie reguły budżetu.
   Zapisz jawnie, dlaczego każdy odrzucony kandydat odpada (budżet, brak
   fizycznego efektu, zakres poza MVP, zależności).
4. Zweryfikuj własny wybór: policz sumę kosztów, sprawdź kolejność zależności
   i upewnij się, że usunięcie dowolnego kamienia łamie reguły. Jeśli Twoje
   narzędzie na to pozwala, oddeleguj kontrolną recenzję osobnemu agentowi.
5. Przygotuj odpowiedź w formacie `Mxx>Myy>Mzz` — identyfikatory kamieni
   w kolejności wykonania, rozdzielone `>`, bez spacji.
6. Pokaż Nawigatorowi `quest_id`, wybrany łańcuch, sumę kosztów i powody
   odrzuceń, a po potwierdzeniu użyj `earthctl submit`.

Zajezdnia odmrozi dokładnie to, co wyśle Ziemia — ani jednostki ciepła więcej.
