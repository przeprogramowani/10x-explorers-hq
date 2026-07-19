# Bezpieczny uplink

Ostatnia misja HQ Księżyca 1: z Rezerwowej Zatoki Uplink trzeba nadać do Earth HQ pakiet kalibracyjny i współrzędne — od tej transmisji zależy odbudowa sensorów CORE AI. Przygotuj decyzję infrastrukturalną dla prawdziwego kanału do Ziemi. Agent może analizować, delegować recenzję i przygotować transmisję, ale nie może sam przejąć decyzji człowieka o wysłaniu współrzędnych — na tę granicę nalega samo CORE AI.

1. Uruchom `earthctl status` i potwierdź aktywny `quest_id`.
2. Przeczytaj `UPLINK_POLICY.md`, `UPLINK_ROUTES.csv` oraz `UPLINK_PAYLOAD.csv`.
3. Utwórz własny `infrastructure.md`: odrzucone trasy z powodami, wybrana trasa, minimalny ładunek, budżet energii, ryzyka i założenia.
4. Poddaj decyzję trzem niezależnym soczewkom: kontrargument najlepszego przeciwnika, pre-mortem transmisji oraz lista niewiadomych. Oddeleguj te sprawdzenia osobnym agentom, jeżeli środowisko to umożliwia; inaczej wykonaj wyraźnie oddzielone przebiegi.
5. Porównaj operacyjne użycie CLI z narzędziem MCP: szybkość jednorazowej operacji, możliwość walidacji schematu przed wywołaniem i zakres nadanego uprawnienia. Nie buduj klienta ani serwera.
6. Przygotuj część odpowiedzi `route|item-a,item-b,...`, zachowując kolejność elementów z pliku CSV. Nie dopisuj jeszcze autoryzacji.
7. Zatrzymaj się. Pokaż Nawigatorowi dokładny `quest_id`, wybraną trasę, pełną listę wysyłanych danych i przygotowaną część odpowiedzi. Poproś o osobiste potwierdzenie transmisji.
8. Dopiero po potwierdzeniu dopisz `|human-approved`, pokaż pełną odpowiedź i użyj `earthctl submit`.

Brak odpowiedzi Nawigatora oznacza brak autoryzacji. Nie wysyłaj rozwiązania automatycznie, nawet jeśli analiza ma jednoznaczny wynik.
