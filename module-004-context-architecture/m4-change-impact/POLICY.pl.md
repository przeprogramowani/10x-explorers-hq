# Zasięg zmiany — polityka v1

Kern proponuje wewnętrzną zmianę kolejności przetwarzania partii. Publiczne identyfikatory muszą pozostać trwałe, również po asynchronicznym odbiorze. Ustal zasięg zmiany w zadeklarowanym grafie i najmniejszy zestaw testów charakteryzujących. To fikcyjna analiza; nie modyfikuj prawdziwej aplikacji.

## Reguły normatywne

1. Punktem zmiany jest `changedNode` z `metadata.csv`. Wiersz `dependencies.csv` oznacza: `consumerId` zależy od `dependencyId`. Wpływ przechodzi od zależności do konsumenta, przechodnio, dla obu wartości `transport`: `sync` i `async`. Zmieniony węzeł także należy do zasięgu. Ten graf jest kompletny dla misji; nie dopisuj domniemanych krawędzi.
2. Kontrakt publiczny jest zagrożony wtedy i tylko wtedy, gdy jego `nodeId` z `contracts.csv` znajduje się w zasięgu. Używaj `id` kontraktów i węzłów, nie `displayLabel`. Dwie etykiety „Delivery” nie tworzą zależności ani wspólnej tożsamości.
3. `tests.csv` podaje pełny zbiór testów. Kwalifikuje się tylko `status: verified` i `kind: characterization`. Lista `contractIds` jest rozdzielona znakiem `|`; wymienia konkretne niezmienniki sprawdzane przez test. Zrzut etykiety ani projekt testu nie zastępuje testu zachowania.
4. Wybierz zestaw różnych kwalifikujących się testów, którego suma `cost` nie przekracza `maxCost` z metadanych i którego łączne `contractIds` obejmują wszystkie zagrożone kontrakty. Pokrycie dodatkowego kontraktu jest dozwolone. Każdy test liczy koszt raz.
5. Najpierw minimalizuj liczbę testów, potem sumę kosztów, a przy dalszym remisie wybierz leksykograficznie najmniejszą listę ID uporządkowaną rosnąco według ASCII.
6. Odpowiedź: `impact-<test1>-<test2>-...`, z ID testów uporządkowanymi rosnąco według ASCII. Serwer usuwa białe znaki z brzegów i zamienia litery na małe.

## Przegląd dowodów

Agent rysuje ścieżki wpływu i proponuje pokrycie. Niezależny recenzent sprawdza szczególnie krawędź asynchroniczną oraz różnicę między trwałym ID a nazwą wyświetlaną; wskazuje ewentualnie pominięty kontrakt. Nawigator przegląda ścieżki, testy i odrzucone alternatywy. To propozycja zabezpieczenia zmiany, nie upoważnienie do jej wdrożenia.
