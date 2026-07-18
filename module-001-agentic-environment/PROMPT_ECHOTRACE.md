# EchoTrace

Odyssey nie może bezpiecznie wejść do trzech niestabilnych komór. Zbuduj dla używanego przez Nawigatora agenta powtarzalną zdolność pobierania i klasyfikowania chronionych skanów.

1. Uruchom `earthctl status` i potwierdź aktywny `quest_id`.
2. Przeczytaj `ECHO_RESOURCE.md`, `ECHO_SCAN_INDEX.csv` oraz `ECHO_FIELD_GUIDE.md`.
3. Dobierz natywny mechanizm do aktualnego środowiska: skill dla Codex lub Claude Code, instrukcję dla Copilot albo równoważny, wielokrotnie używalny artefakt. Stwórz go samodzielnie. Nie zapisuj tokenu w repozytorium.
4. Użyj tej samej zdolności do pobrania wszystkich trzech skanów i sklasyfikuj każdy na podstawie surowych odczytów. Dla każdego wyniku pokaż krótki dowód z danych.
5. Przygotuj odpowiedź dokładnie w formacie `alpha:<code>|beta:<code>|gamma:<code>`.
6. Pokaż Nawigatorowi `quest_id`, dowody i pełną odpowiedź. Dopiero po jego potwierdzeniu wyślij ją przez `earthctl submit`.

Jeżeli narzędzie nie obsługuje trwałych skilli, zastosuj najbliższy dostępny mechanizm wielokrotnego użycia i wyjaśnij wybór. Celem nie jest konkretny format pliku, lecz świadome zaprojektowanie narzędzia dla agenta.
