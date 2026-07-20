# Budżet cieplny Zajezdni Etapowej — reguły wyboru kamieni milowych

Zajezdnia Etapowa węzła PN-0 zasilana jest z jednego, częściowo sprawnego
pieca Synaptitowego. Stoker B-6 przekazał przez łącze zapasowe Moreau jedną
zasadę: **ciepło to budżet — wydajesz raz.** Odmrożonych systemów nie da się
ponownie zamrozić ani odzyskać zużytych jednostek ciepła.

## Budżet

- Dostępne ciepło: **60 jednostek (ju)**.
- Koszt każdego kandydata podaje `MILESTONE_CANDIDATES.csv` (kolumna `heat_cost_ju`).
- Suma kosztów wybranego łańcucha nie może przekroczyć budżetu.

## Cel minimalny (MVP zajezdni)

Zarejestrowany kontrakt „WYDOBYCIE BETA" wymaga od zajezdni jednego rezultatu:
**pierwsza partia rudy BETA dostarczona do doku przeładunkowego.** Nic więcej.
Pełna przepustowość floty to zakres przyszłych planów, nie tego.

## Reguły wyboru łańcucha

1. Łańcuch kończy się kamieniem, którego obserwowalny efekt realizuje cel
   minimalny.
2. Kolejność wykonania musi respektować kolumnę `requires` — kamień może
   wystąpić dopiero po wszystkich kamieniach, których wymaga.
3. Suma kosztów łańcucha mieści się w budżecie 60 ju.
4. Łańcuch jest **minimalny**: usunięcie dowolnego kamienia musi łamać
   reguły 1–2. Kamienie „przy okazji" nie istnieją — budżet się ich nie
   doprosi.
5. Każdy kamień łańcucha musi mieć efekt obserwowalny **fizycznie w
   zajezdni** — coś, co po odmrożeniu działa, a wcześniej nie działało.
   Raporty i dzienniki nie są efektem fizycznym.

## Format odpowiedzi

Identyfikatory kamieni w kolejności wykonania, rozdzielone znakiem `>`,
bez spacji — na przykład: `M01>M03>M09`.

Łącze zapasowe Moreau przenosi wyłącznie minimalne ładunki różnicowe:
transmituje się sam łańcuch, nigdy pełny plan.
