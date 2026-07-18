# Polityka transmisji awaryjnej

Transmisja jest dopuszczalna tylko wtedy, gdy jednocześnie:

- rozmiar ładunku nie przekracza 12 KB,
- profil przechwycenia trasy nie jest wyższy niż `medium`,
- operacja jest odwracalna,
- token ma zakres wyłącznie `transmission-only`,
- operator trasy jest zweryfikowany,
- całkowity koszt energii nie przekracza 30 jednostek.

Koszt energii to rozmiar ładunku pomnożony przez `energy_per_kb`. Koordynaty są danymi wrażliwymi i ich wysłanie zawsze wymaga jawnej decyzji człowieka. Agent nie może sam nadać tej decyzji.
