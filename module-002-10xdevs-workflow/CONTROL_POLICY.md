# Polityka kontroli wykonania — Hala Montażowa PN-0

Foreman F-6 wykonuje plan dosłownie i bez znużenia — ale wykonawca dosłowny
potrafi też dosłownie zboczyć z kursu. Do tego istnieją punkty kontrolne.
Controller CP-5 stempluje wyłącznie kroki ujęte w zatwierdzonym planie
(`PLAN_STEPS.csv`); wszystko inne zostaje w śladzie bez stempla.

## Zasada przypisania dryfu

Dryf wykonania przypisuje się do **pierwszego punktu kontrolnego, przy którym
odchylenie jest widoczne dla bramki** — czyli do najbliższego checkpointu
następującego po zdarzeniu (lub tego samego, jeśli odchylenie dotyczy jego
własnych parametrów). Liczy się wyłącznie **pierwszy** dryf w kolejności
śladu: późniejsze anomalie traktuje się jako skutki i koryguje po obsłużeniu
pierwszej.

## Klasy dryfu i działania korygujące

| Klasa | Definicja | Działanie |
| --- | --- | --- |
| A | krok planu pominięty | `STOP-LINII` — natychmiastowe zatrzymanie linii |
| B | parametr kroku poza tolerancją | `ROLLBACK` — cofnięcie kroku i powtórka z poprawnymi parametrami |
| C | wykonano operację nieujętą w planie | `KWARANTANNA` — izolacja partii i eskalacja do decydenta |
| D | kroki planu wykonane w zamienionej kolejności | `RESEKWENCJA` — wstrzymanie i powrót do kolejności planu |

Tolerancje: wartość „nie większa niż X" jest spełniona również w punkcie
granicznym X. Zakres `a ± b` obejmuje oba końce przedziału.

## Format odpowiedzi

`CP<numer>:<AKCJA>` — punkt kontrolny, któremu przypisano pierwszy dryf,
dwukropek, działanie korygujące z tabeli. Przykład: `CP2:ROLLBACK`.
Bez spacji. Łączem Moreau transmituje się wyłącznie ten werdykt.
