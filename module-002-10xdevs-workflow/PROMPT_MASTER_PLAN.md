# Plan Główny — walidacja harmonogramu Odyssey-F

Dyspozytornia lodowej wykuwni jest oczyszczona ze skażonego harmonogramu.
Astronauta stoi przy głównym przełączniku, ale nie uruchomi linii, dopóki
szkielet nowego planu nie zostanie porównany z archiwami budowy Odyssey-F
i podpisany przez Earth HQ.

Prowadź tę misję stopniowo. Po każdym kroku pokaż Nawigatorowi ustalenia
i poczekaj na decyzję o przejściu dalej.

1. Uruchom `earthctl status` i potwierdź, że aktywny `quest_id` to
   `q-m2-master-plan`.
2. Przeczytaj `MASTER_PLAN_POLICY.md`. Zanim otworzysz archiwum, wypisz
   warunki kwalifikacji bloku oraz format klucza.
3. Otwórz `FORGE_ARCHIVE.csv`. Sprawdź każdy blok względem wszystkich
   warunków polityki. Odrzuć blok, gdy nie spełnia choć jednego warunku,
   i zapisz konkretny powód odrzucenia.
4. Uporządkuj zakwalifikowane kody według `takt_index` i zbuduj podpisany
   klucz planu w formacie z polityki.
5. Przeczytaj `RECON_LOG.csv`. Odnotuj każdą anomalię uzgodnienia osobno;
   nie zmieniaj przez nią klucza wyliczonego z archiwum i nie próbuj jej
   wyjaśniać bez dowodów.
6. Pokaż Nawigatorowi `quest_id`, trzy zakwalifikowane wiersze, powody
   odrzucenia pozostałych bloków, anomalie z dziennika oraz przygotowany
   klucz. **Zatrzymaj się i poproś o jawne potwierdzenie transmisji.**
7. Dopiero po potwierdzeniu człowieka użyj:
   `earthctl submit --quest-id q-m2-master-plan --answer <klucz>`.

Rdzeń Harmonogramu czeka. Pierwszy takt ruszy dopiero wtedy, gdy człowiek
zatwierdzi plan oparty na właściwej rewizji fabryki.
