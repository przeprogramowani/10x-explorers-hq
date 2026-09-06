# Okno powrotu — ziemskie dossier

Odyssey ma sprawne łącze prywatne i przećwiczony publiczny wabik. Dwa statki przechwytujące nadal nasłuchują. Zatwierdzony rozkaz dotyczący wabika kieruje oboma kontaktami jako jedną grupą przechwytującą. Wyznacz bezpieczny korytarz rzeczywistego lotu, wiarygodny pusty wabik i dysponenta wydania, którego wskazują dowody. To fikcyjne dane, niezależne od konta gracza. Pobranie pliku niczego nie uruchamia.

[Pakiet CSV i schemat](SCHEMA.pl.md)

## Odczytaj dowody

Cztery kolekcje to `corridors`, `relayReceipts`, `releaseLedger` i `interceptOrders`. Łącz identyfikatory dokładnie, z zachowaniem wielkości liter. Nazwy są etykietami, nie dowodem tożsamości. Każde `id` w rejestrze wydań oznacza jedno niezmienne wydanie; jego `status` jest rozstrzygający. Nie zastępuj go innym wydaniem tylko dlatego, że ma późniejszy `time`.

Wszystkie czasy to stałe, całkowite **minuty misji**, nie bieżący zegar. `flight` i `window` są przedziałami `[start, end)`: początek należy do przedziału, koniec nie. Przedziały nakładają się tylko wtedy, gdy początek każdego przypada przed końcem drugiego. Lot kończący się dokładnie z początkiem przechwycenia jest bezpieczny wobec tego rozkazu. Podczas analizy nie upływa żaden rzeczywisty termin.

## Prawdziwy korytarz

Kandydat musi spełnić **wszystkie** warunki:

- `cargoCertified` wynosi `true`, a `capacity >= cargoUnits` z nagłówka dossier. Jego `releaseId` wskazuje wpis rejestru o `status: "active"`. Wydanie wycofane jest niedopuszczalne, nawet jeśli jest nowsze.
- Co najmniej dwa wpisy `relayReceipts` o `kind: "corridor"` mają `trusted: true`, zgodne `corridorId`, `revision` i `releaseId` oraz **różne wartości `witnessId`**. `time` każdego liczonego potwierdzenia musi być ściśle wcześniejszy niż początek lotu. Powtórzone wiadomości jednego świadka liczą się raz. Możesz użyć dowolnej poprawnej pary; obcy lub spóźniony wpis nie zastępuje poprawnej pary.
- Żaden zatwierdzony rozkaz przechwycenia (`committed: true`) dla `id` tego korytarza nie ma `window` nakładającego się na jego `flight`. Sprawdź wszystkie takie rozkazy, niezależnie od wystawcy i wabika.

## Korytarz wabika

Musi być inny niż prawdziwy korytarz, mieć `empty: true` i dokładnie `route: ["monitored-public"]`. Jego lot musi nakładać się na przynajmniej jeden zatwierdzony rozkaz dla jego `id`, którego `baitId` jest równy `baitId` z nagłówka dossier.

Tablice `privateRelays` obu korytarzy nie mogą mieć wspólnego identyfikatora. Wyliczają zarezerwowaną prywatną infrastrukturę, także rezerwacje zapasowe; są niezależne od faktycznie ogłoszonej trasy. Pusta publiczna trasa może nadal rezerwować prywatny przekaźnik i przez to nie nadawać się do użycia obok prawdziwego korytarza. Pusty wabik nie wymaga certyfikacji ładunku, pary potwierdzeń ani aktywnego statusu wydania.

## Dysponent wydania

Rozważ wartości `issuerId` z `releaseLedger`. Dla wybranego wabika i wystawcy znajdź **jedną wspólną tożsamość wydania**, łączącą wszystkie poniższe wpisy:

1. Aktywny wpis rejestru (`id`, `issuerId`).
2. Zaufane potwierdzenie `kind: "release"` z `recordId: "R-077"` oraz zgodnymi `releaseId` i `issuerId`.
3. Zatwierdzony rozkaz przechwycenia o zgodnych `releaseId` i `issuerId`, `corridorId` wybranego wabika, `baitId` z nagłówka oraz nakładających się przedziałach lotu wabika i przechwycenia.
4. Zaufane potwierdzenie `kind: "custody"` o tych samych `releaseId` i `issuerId`. Jego `witnessId` musi różnić się zarówno od identyfikatora wystawcy, jak i od identyfikatora świadka potwierdzenia R-077.

To połączenie dowodów pieczy nie wymaga dodatkowej kolejności czasowej. Nazwisko wystawcy ani obce historyczne podpisy nie zastępują tych identyfikatorów. Wynik wskazuje podejrzany łańcuch autoryzacji, nie dowodzi, że wymieniony dysponent osobiście wpisał rozkaz. Ziemscy śledczy muszą osobno potwierdzić odpowiedzialność.

## Przejrzyj wynik i wyślij

Znajdź jedną trójkę spełniającą wszystkie trzy sekcje. Możesz poprosić agenta o analizę JSON, ale sprawdź jego dowody: identyfikatory wpisów, różnych świadków, zgodne rewizje, porównania przedziałów i połączenie dowodów pieczy. Przed wysłaniem wyjaśnij, dlaczego pozostali kandydaci odpadają.

Odpowiedź ma postać `return-<real_corridor>-<decoy_corridor>-<issuer_id>` z identyfikatorami wpisów. Serwer usuwa białe znaki z brzegów i zamienia litery na małe. Nie wysyłaj nazwiska ani przetłumaczonej nazwy korytarza.

W grze ukończ cztery zadania M5 i aktywuj **Okno powrotu** w Wieży Łącza. Użyj `/support`, by skorzystać z dotychczasowego połączenia z Ziemią i obsługi `earthctl`. Sprawdź aktywną misję, a następnie prześlij zweryfikowaną odpowiedź dla `q-m5-return-window`; podpowiedź misji prowadzi tutaj. Osobisty token API pozostaw w swojej dotychczasowej konfiguracji lokalnej; nigdy nie dodawaj go do dossier ani nie wysyłaj innemu graczowi.

`MISSION_NOT_READY` oznacza, że zapisane warunki nie dotarły: ukończ zadania M5, aktywuj zadanie w Wieży Łącza i pozwól grze zapisać stan przed ponowieniem. Błędna odpowiedź zwraca podpowiedź. Poprawna przygotowuje łączność i okno powrotu za **0 XP**; nie odbudowuje CORE, nie budzi Harrisa i nie zezwala na start.

Wróć do gry i poczekaj na wynik albo odśwież stronę. Jeśli punkt misji nadal oczekuje na wynik, sprawdź aktywną misję i bezpiecznie ponów tę samą odpowiedź. Zgłoszenia już ukończone lub oczekujące są potwierdzane bez dodawania kolejnej nagrody. Po uzyskaniu gotowości odwiedź wnękę z rdzeniem w Wieży Łącza i konsolę zaopatrzenia na statku. Nie trzeba resetować dawnych zadań.
