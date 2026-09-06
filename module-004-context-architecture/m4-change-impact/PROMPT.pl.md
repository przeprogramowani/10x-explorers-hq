# Zasięg zmiany — Earth HQ

Misja opcjonalna: `q-m4-change-impact`. Przeczytaj [politykę](POLICY.pl.md) i [wersję angielską](POLICY.en.md), jeśli jej potrzebujesz.

Warunek gry: **przywrócenie pamięci M4**, zapisane na serwerze. Nie musisz aktywować tego zadania.

Prowadź pracę stopniowo, zgodnie z [zasadami HQ](../../AGENTS.md). Po każdym kroku przedstaw ustalenia Nawigatorowi i poczekaj na decyzję.

1. Wyjaśnij wymagany etap gry oraz format odpowiedzi z polityki. Status nadal dotyczy głównej misji; ta analiza używa jawnego ID i niczego nie aktywuje.
2. Przeczytaj pliki CSV poniżej i zaproponuj sposób analizy.
3. Zbuduj tabelę dowodów i odrzuconych kandydatów.
4. Zleć niezależną krytykę na podstawie danych i reguł. Osobny przegląd z czystym kontekstem jest dopuszczalny, jeśli drugi agent nie jest dostępny.
5. Pokaż Nawigatorowi `quest_id`, dowody i gotową odpowiedź. **Zatrzymaj się przed transmisją i uzyskaj jawne potwierdzenie.**
6. Dopiero po potwierdzeniu użyj `earthctl submit --quest-id q-m4-change-impact --answer <odpowiedz>`. Nagroda: 0 XP i opcjonalny znacznik ukończenia; główna misja pozostaje aktywna.

- [contracts.csv](contracts.csv)
- [dependencies.csv](dependencies.csv)
- [metadata.csv](metadata.csv)
- [nodes.csv](nodes.csv)
- [tests.csv](tests.csv)

`MISSION_NOT_READY`: ukończ wymagany etap i pozwól grze zapisać stan przed ponowieniem. Po przyjęciu odpowiedzi wróć do gry albo odśwież stronę. Opcjonalne ukończenie dopisze się obok głównej misji. Ponowienie przyjętej odpowiedzi nie daje XP ani drugiego ukończenia.
