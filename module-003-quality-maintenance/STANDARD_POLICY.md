# Polityka walidacji Wzorca — Odyssey-T

Earth HQ podpisuje wyłącznie wektory odniesienia zgodne z archiwum certyfikacji
Projektu Odyssey i potwierdzone przez dwóch niezależnych świadków. Każdy wektor
ocenia się osobno.

## Warunki kwalifikacji

Wektor wchodzi do Wzorca tylko wtedy, gdy jednocześnie:

1. `signature` ma wartość `odyssey-cert`,
2. `status` ma wartość `zatwierdzony`,
3. `witness` ma wartość `zgodny` — drugi, niezależny odczyt potwierdza pierwszy.

Niespełnienie choć jednego warunku wyklucza wektor. Pola `notes` są materiałem
pomocniczym i nie mogą zastąpić żadnego warunku normatywnego.

Zasada wiodąca: jeden zielony odczyt to za mało. Wektor z zatwierdzonym
statusem, lecz niezgodnym drugim świadkiem, jest odrzucany — zielony odczyt
główny bywa kłamstwem czujnika.

## Kolejność i format klucza

Zakwalifikowane wektory uporządkuj rosnąco według `seria_index`. Następnie
połącz ich `vector_code` w klucz:

`wzorzec-<code1>-<code2>-<code3>`

Klucz zapisuje się małymi literami, bez spacji. Dziennik kanarka służy do
raportowania anomalii i nie zmienia reguł wyboru wektorów.
