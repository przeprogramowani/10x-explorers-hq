# Kontrola implementacji

Druga misja HQ Księżyca 2: Hala Montażowa wykonuje pierwszy kamień milowy
planu „WYDOBYCIE BETA" — partię sprzęgów transportowych dla doku. Foreman F-6
prowadzi linię dosłownie według planu, Controller CP-5 stempluje bramki,
a Astronauta obserwuje linię na miejscu. Nawigator nadzoruje wykonanie
z Earth HQ: ślad fabrykatora dociera przez łącze zapasowe Moreau, więc
werdykt musi być minimalny — jeden punkt, jedno działanie.

1. Uruchom `earthctl status` i potwierdź aktywny `quest_id`.
2. Przeczytaj `PLAN_STEPS.csv`, `FABRICATOR_TRACE.csv` oraz `CONTROL_POLICY.md`.
3. Porównaj ślad wykonania z zatwierdzonym planem krok po kroku, w kolejności
   `seq`. Odnotuj każdą różnicę: parametry, kolejność, kroki brakujące
   i kroki, których plan nie zawiera.
4. Ustal **pierwszy** dryf w kolejności śladu, przypisz go do właściwego
   punktu kontrolnego zgodnie z zasadą przypisania z polityki i dobierz
   działanie korygujące z tabeli klas.
5. Zweryfikuj werdykt: sprawdź tolerancje przy wartościach granicznych
   i upewnij się, że wcześniejsze kroki są czyste. Jeśli Twoje narzędzie na
   to pozwala, oddeleguj kontrolne sprawdzenie osobnemu agentowi.
6. Przygotuj odpowiedź w formacie `CP<numer>:<AKCJA>`, bez spacji.
7. Pokaż Nawigatorowi `quest_id`, wykryty dryf, klasę i werdykt, a po
   potwierdzeniu użyj `earthctl submit`.

Linia stoi z partią w bramce i czeka na decyzję Ziemi. F-6 nie zapyta drugi
raz — wykona dokładnie to, co przyjdzie.
