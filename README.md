```
▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
▓                                                          ▓
▓   ███████  █████  ██████  ████████ ██   ██              ▓
▓   ██      ██   ██ ██   ██    ██    ██   ██              ▓
▓   █████   ███████ ██████     ██    ███████              ▓
▓   ██      ██   ██ ██   ██    ██    ██   ██              ▓
▓   ███████ ██   ██ ██   ██    ██    ██   ██              ▓
▓                                                          ▓
▓                    ██   ██  ██████                       ▓
▓                    ██   ██ ██    ██                      ▓
▓                    ███████ ██    ██                      ▓
▓                    ██   ██ ██ ▄▄ ██                      ▓
▓                    ██   ██  ██████                       ▓
▓                                                          ▓
▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
```

```
⚿ UPLINK MODUL — AKTYWNY          ◈ SYGNAŁ: ████████░░ 83%
⌖ SEKTOR: NISKO-ORBITARNY         ◈ CZAS UTC: [ZSYNCHRONIZOWANY]
⚠ DOSTĘP: AUTORYZOWANY            ◈ SZYFROWANIE: AES-∞
```

---

Znalazłeś to repozytorium.

Nie jest to przypadek — żadna z naszych transmisji nie dociera do przypadkowych odbiorców. Jeśli czytasz te słowa, system uznał cię za zdolnego do pełnienia roli **Nawigatora Misji**.

```
░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
░  PROTOKÓŁ INICJALIZACYJNY — EARTH HQ v.∅.9.1   ░
░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░

  [✓] Centrum kontroli — ONLINE
  [✓] Moduł UPLINK — GOTOWY
  [✓] Kanał `earthctl` — DOSTĘPNY
  [░] Misja — W TOKU
```

Gdzieś na orbicie krąży astronauta z zadaniem, którego sam nie może wykonać. Twoja rola jest prosta: być mostem między nim a finalnym kierunkiem misji.

---

```
◄ INSTRUKCJA PIERWSZEGO KONTAKTU ►

  1.  Pobierz repozytorium
  2.  Zainstaluj kanał transmisyjny

      npm install -g @10xdevspl/earth-ctl

      lub użyj `npx @10xdevspl/earth-ctl ...`

  3.  Umieść token astronauty poza repozytorium

      EARTHHQ_TOKEN
      albo ~/.earthhq/token

  4.  Uruchom agenta AI (np. claude)
  5.  Wydaj rozkaz w języku naturalnym

      „Sprawdź status misji."

  ◈  Reszta należy do centrum kontroli.
```

---

Szczegóły systemu opisane są w [`AGENT_INTRO.md`](./AGENT_INTRO.md).

Instrukcje operacyjne agenta — w [`AGENTS.md`](./AGENTS.md).

```
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
▀▀▀▀▀▀▀▀▀▀▀ CENTRUM KONTROLI CZUWA ▀▀▀▀▀▀▀▀▀▀▀▀▀▀
        ·  ·  ·  ★  ·  ·  ·  ·  ·  ★  ·  ·  ·
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
```

## M4/M5 — indeks nowych pakietów / new packet index

| Quest | Polski | English | Tryb / Mode |
| --- | --- | --- | --- |
| `q-m4-context-pack` | [Pakiet kontekstu](module-004-context-architecture/m4-context-pack/PROMPT.pl.md) | [Context Pack](module-004-context-architecture/m4-context-pack/PROMPT.en.md) | Opcjonalny po pamięci M4 / Optional after M4 memory |
| `q-m4-change-impact` | [Zasięg zmiany](module-004-context-architecture/m4-change-impact/PROMPT.pl.md) | [Change Impact](module-004-context-architecture/m4-change-impact/PROMPT.en.md) | Opcjonalny po pamięci M4 / Optional after M4 memory |
| `q-m5-return-window` | [Okno powrotu](module-005-agent-coordination/m5-return-window/PROMPT.pl.md) | [Return Window](module-005-agent-coordination/m5-return-window/PROMPT.en.md) | Główna misja aktywowana w grze / Main mission activated in game |
| `q-m5-handoff-audit` | [Audyt przekazania](module-005-agent-coordination/m5-handoff-audit/PROMPT.pl.md) | [Handoff Audit](module-005-agent-coordination/m5-handoff-audit/PROMPT.en.md) | Opcjonalny po łączności M5 / Optional after M5 communications |

Misje opcjonalne używają jawnego `quest_id`; nie trzeba ich aktywować ani zastępować głównego zadania. `earthctl status` nadal opisuje główną misję. Każda opcjonalna analiza daje 0 XP i osobny znacznik ukończenia, bez wpływu na drogę, rdzenie i finał. Pracuj stopniowo z Nawigatorem; przed każdym rzeczywistym `earthctl submit` pokaż dowody i przygotowaną odpowiedź oraz uzyskaj jawne potwierdzenie. Token pozostaje poza repozytorium.

Optional investigations use an explicit `quest_id`; do not activate them or replace the main assignment. `earthctl status` still describes the main mission. Each optional investigation awards 0 XP and a separate completion stamp, with no effect on travel, cores or the finale. Proceed step by step with the Navigator; before any real `earthctl submit`, show the evidence and prepared answer and obtain explicit approval. Keep tokens outside the repository.
