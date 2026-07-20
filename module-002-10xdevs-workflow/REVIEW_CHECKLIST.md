# Lista kontrolna samodzielnej recenzji — węzeł PN-0

Recenzja samodzielna rządzi się jedną zasadą: autor czyta własny plan jak
plan obcy, któremu nie ufa. Defekt to pozycja normatywna, która spełnia
dowolne z poniższych kryteriów. Wszystko inne — w tym rzeczy brzydkie,
powtórzone lub niedoskonałe stylistycznie — defektem nie jest.

## Kryteria defektu

1. **Kryterium niemierzalne.** Kryterium sukcesu, którego spełnienia nie da
   się jednoznacznie zweryfikować (brak liczby, progu lub testu).
2. **Krok bez bramki.** Krok wykonania bez przypisanego punktu kontrolnego,
   na którym dryf byłby widoczny.
3. **Przekroczenie mandatu.** Zakres pracy jednostki wykracza poza jej
   mandat z aneksu architektury (sekcja B pakietu).
4. **Sprzeczność zależności.** Deklarowana zależność między kamieniami
   przeczy zatwierdzonej kolejności wykonania (sekcja A pakietu).
5. **Operacja nieodwracalna bez decyzji człowieka.** Krok nieodwracalny,
   który uruchamia się bez jawnego zatwierdzenia przez człowieka.

## Co defektem NIE jest

- Powtórzenia treści i noty redakcyjne lub stylistyczne.
- Wartości graniczne mieszczące się w tolerancji (kraniec przedziału
  jest w przedziale).
- Załączniki oznaczone jako niewiążące (w tym TODO na przyszłość).
- Kroki poprawnie wskazujące bramki i decyzje człowieka.

## Format odpowiedzi

Identyfikatory wszystkich defektów, posortowane rosnąco, rozdzielone
przecinkami, bez spacji — na przykład: `R-01,R-04,R-12`.
Łączem Moreau wraca wyłącznie ten werdykt.
