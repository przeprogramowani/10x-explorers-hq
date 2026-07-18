# Chroniony zasób skanów

Każdy skan jest dostępny pod adresem:

`https://przeprogramowani-edu.pages.dev/api/game/resources/echo/<scan_id>`

Żądanie GET wymaga tokenu astronauty jako `Authorization: Bearer <token>`. Pobieraj token z `EARTHHQ_TOKEN`, `~/.earthhq/token` albo mechanizmu używanego przez `earthctl`. Nie kopiuj sekretu do promptów, logów ani plików repozytorium.

Odpowiedź zawiera surowe cechy pomiaru. Klasyfikację wykonuje agent; endpoint nie zwraca gotowego kodu odpowiedzi.
