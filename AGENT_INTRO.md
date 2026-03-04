# Witaj w Earth HQ

To jest naziemne centrum kontroli misji dla Kosmicznych Odkrywców. Jako Nawigator Misji monitorujesz postępy astronautów na orbicie, odbierasz ich meldunki i przekazujesz rozwiązania misji przez narzędzie transmisyjne `earthctl`.

## Jak działa to repozytorium

Repozytorium składa się z trzech elementów:

- **README.md** — protokół wejścia do Earth HQ. Wyjaśnia, jak uruchomić centrum kontroli i przygotować kanał transmisji.
- **AGENT_INTRO.md** — (ten plik) opis systemu misji. Tłumaczy, jak działa współpraca repozytorium, agenta i narzędzia `earthctl`.
- **AGENTS.md** — instrukcje operacyjne dla agenta AI. Definiują jego rolę, styl komunikacji i procedury.

Za komunikację z flotą kosmiczną odpowiada opublikowana biblioteka CLI **`@10xdevspl/earth-ctl`**, która udostępnia komendę `earthctl`.

## Jak działa kanał `earthctl`

`earthctl` jest oficjalnym kanałem transmisyjnym Earth HQ. To on:

- odczytuje token astronauty z bezpieczniejszej lokalizacji poza repozytorium
- komunikuje się z systemem misji przez UPLINK
- zwraca agentowi uporządkowane odpowiedzi JSON
- pilnuje błędów autoryzacji i awarii łączności

Token powinien być skonfigurowany lokalnie na maszynie deweloperskiej, poza repozytorium. Zalecane opcje to:

- zmienna środowiskowa `EARTHHQ_TOKEN` ustawiona w lokalnej sesji lub profilu powłoki
- plik użytkownika `~/.earthhq/token` na macOS/Linux lub `%USERPROFILE%\.earthhq\token` na Windows

Nie zaleca się przekazywania tokenu inline w treści komendy lub rozmowy, jeśli można zapisać go wcześniej na maszynie deweloperskiej.

## Jak obsługiwać misje

Moduł UPLINK jest obsługiwany przez agentowe narzędzia AI — takie jak **Claude Code**, **GitHub Copilot (Agent mode)**, **OpenAI Codex** czy inne narzędzia zdolne do samodzielnego wykonywania poleceń w terminalu.

Nie musisz ręcznie wywoływać surowych endpointów API. Zamiast tego:

1. Zainstaluj kanał transmisyjny:
   - globalnie: `npm install -g @10xdevspl/earth-ctl`
   - jednorazowo: `npx @10xdevspl/earth-ctl status`
2. Umieść token astronauty na swojej maszynie deweloperskiej poza repozytorium, najlepiej w `EARTHHQ_TOKEN` albo `~/.earthhq/token`.
3. Otwórz repozytorium w swoim narzędziu AI.
4. Wydaj polecenie w języku naturalnym, np.:
   - *„Sprawdź status aktualnej misji."*
   - *„Prześlij odpowiedź do questa o podanym ID."*
5. Agent użyje `earthctl`, aby wykonać transmisję do systemów misji.

## Ważne zasady

- Nie przechowuj tokenu astronauty w plikach repozytorium.
- Preferuj lokalną konfigurację tokenu na maszynie deweloperskiej zamiast przekazywania go inline przy każdej komendzie.
- `earthctl status` służy do pobierania statusu aktualnej misji.
- `earthctl submit --quest-id <id> --answer <answer>` służy do przesyłania odpowiedzi.
- Przed przesłaniem rozwiązania agent zawsze powinien potwierdzić `quest_id` i treść odpowiedzi.
- W razie błędu łączności sprawdź poprawność tokenu oraz dostępność narzędzia `earthctl`.

---

Centrum kontroli czuwa. Powodzenia na orbicie.
