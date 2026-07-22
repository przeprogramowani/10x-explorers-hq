# Polityka walidacji Planu Głównego — Odyssey-F

Earth HQ podpisuje wyłącznie bloki harmonogramu zgodne z rewizją faktycznie
wdrożoną w lodowej wykuwni. Każdy blok ocenia się niezależnie.

## Warunki kwalifikacji

Blok wchodzi do Planu Głównego tylko wtedy, gdy jednocześnie:

1. `signature` ma wartość `odyssey-build`,
2. `status` ma wartość `zatwierdzony`,
3. `build_rev` ma wartość `F-11`.

Niespełnienie choć jednego warunku wyklucza blok. Pola `notes` są materiałem
pomocniczym i nie mogą zastąpić żadnego warunku normatywnego.

## Kolejność i format klucza

Zakwalifikowane bloki uporządkuj rosnąco według `takt_index`. Następnie połącz
ich `block_code` w klucz:

`plan-<code1>-<code2>-<code3>`

Klucz zapisuje się małymi literami, bez spacji. Dziennik uzgodnienia służy
do raportowania anomalii i nie zmienia reguł wyboru bloków.
