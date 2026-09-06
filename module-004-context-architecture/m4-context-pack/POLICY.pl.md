# Pakiet kontekstu — polityka v1

Echo przygotowuje mały pakiet dla agenta, który ma sprawdzić zapis i odbiór archiwum. Całe archiwum nie mieści się w łączu. Twoim zadaniem jest wybrać najtańszy wystarczający zestaw dokumentów, a potem poddać go niezależnej krytyce. Wszystkie dane są fikcyjne.

## Reguły normatywne

1. `metadata.csv` podaje `targetRevision` i nieprzekraczalny `budget` w umownych jednostkach kontekstu. `documents.csv` jest pełnym zbiorem kandydatów. Identyfikatory łącz dokładnie; etykiety nie są kluczami. Koszt zestawu to suma `units` różnych wybranych dokumentów, liczonych raz.
2. Każdy wybrany dokument musi mieć dokładnie rewizję `targetRevision` i `authority: verified`. Starszy dokument ani `draft` nie kwalifikuje się, nawet gdy jest tani lub deklaruje wszystkie tematy.
3. Wszystkie wymagania z `claims.csv` o `required: true` muszą mieć przynajmniej jeden wpis w `support.csv`, którego `documentId` należy do zestawu, `claimId` pasuje i `verified: true`. Sam tytuł dokumentu lub wiersz `verified: false` nie jest dowodem.
4. Dla każdego wybranego dokumentu dołącz wszystkie jego zależności z `dependencies.csv`: `documentId` wymaga `requiresDocumentId`. Stosuj tę regułę przechodnio, aż zbiór się nie zmienia. Dokumenty wymagane przez zależności również zwiększają koszt i muszą spełniać regułę rewizji oraz statusu weryfikacji. Brak wiersza oznacza brak dodatkowej zależności.
5. Spośród zestawów spełniających reguły i budżet wybierz najmniejszą sumę `units`; przy remisie najmniejszą liczbę dokumentów; przy dalszym remisie leksykograficznie najmniejszą listę ID, wcześniej uporządkowaną rosnąco według ASCII. Są to kolejne kryteria, nie ważona suma.
6. Uporządkuj wybrane ID rosnąco według ASCII. Odpowiedź: `context-<id1>-<id2>-...`. Nie pomijaj wymaganych zależności w odpowiedzi. Serwer usuwa białe znaki z brzegów i zamienia litery na małe.

## Przegląd dowodów

Agent proponuje zestaw, koszt i pokrycie każdego wymagania. Niezależny recenzent dostaje dane i reguły, a nie gotową odpowiedź do potwierdzenia: ma znaleźć pominiętą zależność, nieaktualne źródło albo tańszą poprawną alternatywę. Jeśli nie masz drugiego agenta, wykonaj osobny przegląd z czystym kontekstem. Nawigator sprawdza tabelę dowodów i powody odrzucenia kandydatów przed transmisją.
