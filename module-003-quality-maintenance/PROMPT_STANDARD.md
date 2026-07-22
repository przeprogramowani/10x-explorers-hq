# Wzorzec — walidacja standardu diagnostycznego Odyssey-T

Rdzeń diagnostyczny poligonu Odyssey-T został odbudowany. Zanim astronauta
poręczy za jego wynik, potrzebny jest zaufany wzorzec odniesienia — podpisany
zestaw wektorów, zweryfikowany krzyżowo z archiwami certyfikacji Projektu
Odyssey. Na tym księżycu jeden zielony odczyt nigdy nie wystarcza: każdy
kandydat musi mieć drugiego, niezależnego świadka.

Prowadź tę misję stopniowo. Po każdym kroku pokaż Nawigatorowi ustalenia
i poczekaj na decyzję o przejściu dalej.

1. Uruchom `earthctl status` i potwierdź, że aktywny `quest_id` to
   `q-m3-standard`.
2. Przeczytaj `STANDARD_POLICY.md`. Zanim otworzysz archiwum, wypisz warunki
   kwalifikacji wektora oraz format klucza wzorca.
3. Otwórz `CERT_ARCHIVE.csv`. Sprawdź każdy wektor względem wszystkich
   warunków polityki. Odrzuć wektor, gdy nie spełnia choć jednego warunku,
   i zapisz konkretny powód odrzucenia. Zwróć szczególną uwagę na kolumnę
   drugiego świadka: wektor z zielonym odczytem głównym, ale niezgodnym
   drugim świadkiem, nie wchodzi do wzorca — to jest sedno tego księżyca.
4. Uporządkuj zakwalifikowane kody rosnąco według `seria_index` i zbuduj
   podpisany klucz wzorca w formacie z polityki.
5. Przeczytaj `CANARY_LOG.csv`. Odnotuj anomalię kanarka osobno; nie zmieniaj
   przez nią klucza wyliczonego z archiwum i nie próbuj jej wyjaśniać bez
   dowodów.
6. Pokaż Nawigatorowi `quest_id`, trzy zakwalifikowane wiersze, powody
   odrzucenia pozostałych wektorów, anomalię kanarka oraz przygotowany klucz.
   **Zatrzymaj się i poproś o jawne potwierdzenie transmisji.**
7. Dopiero po potwierdzeniu człowieka użyj:
   `earthctl submit --quest-id q-m3-standard --answer <klucz>`.

Rdzeń diagnostyczny czeka. Certyfikat wystawi maszyna, ale poręczy za niego
człowiek — dopiero wtedy, gdy wzorzec oprze się na wektorach z podwójnym,
zgodnym świadkiem.
