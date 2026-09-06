# Audyt przekazania — polityka v1

Splot zebrał meldunki „gotowe”, lecz Moreau chce dowodu odbioru i niezależnego review. Znajdź jedno zadanie z prawidłowo zakończonym przekazaniem. Wszystkie zapisy są fikcyjne; zegary załóg celowo się różnią.

## Reguły normatywne

1. `seq` jest unikalnym numerem przyjęcia wpisu przez jeden centralny rejestr, wspólnym dla `assignments.csv`, `artifacts.csv` i `receipts.csv`. Porównuj wyłącznie liczby `seq`. `actorTime` jest lokalnym zegarem autora i nie określa kolejności między wpisami. `metadata.csv` potwierdza tę politykę. Nie ma bieżącego terminu.
2. Dla każdego `jobId` wybierz przydział z największym `seq` w `assignments.csv`. Jego `ownerId`, `receiverId` i `reviewerId` są rozstrzygające. Wszystkie trzy ID muszą być różne. Starszy przydział nie potwierdza obecnej odpowiedzialności.
3. Dla zadania wybierz wpis artefaktu o największym `seq` spośród `committed: true`. Musi istnieć, mieć `seq` większe niż wybrany przydział i zgodne `ownerId`. To jego `id` i `revision` określają bieżący artefakt. Nie wybieraj starszego artefaktu tylko dlatego, że ma więcej potwierdzeń. Wpis `committed: false` nie jest wydaniem i nie zastępuje ostatniego zatwierdzonego wpisu.
4. Potrzebne są dwa zaufane potwierdzenia (`trusted: true`) o `seq` ściśle większym niż wybrany artefakt i zgodnych `jobId`, `artifactId` oraz `revision`: jedno `kind: received` z `witnessId` równym `receiverId` i jedno `kind: reviewed` z `witnessId` równym `reviewerId`. Obie role są konieczne. Duplikat odbioru, `sent`, własne review lub potwierdzenie starej rewizji nie zastępują brakującej roli. Obce wpisy można zignorować, jeśli poprawna para istnieje.
5. Rozważ wszystkie zadania. Dokładnie jedno spełnia wszystkie warunki. Odpowiedź: `handoff-<jobId>-<ownerId>-<artifactId>`, z aktualnego przydziału i artefaktu. Serwer usuwa białe znaki z brzegów i zamienia litery na małe.

## Przegląd dowodów

Agent porównuje przydział, ostatnie zatwierdzone wydanie i dwa potwierdzenia. Niezależny recenzent próbuje obalić wniosek, sprawdzając przede wszystkim zmianę właściciela, rewizję i niezależność świadków. Nawigator ogląda numery `seq` oraz odrzucone kandydatury przed zatwierdzeniem odpowiedzi. Sam komunikat „wysłano” nie jest wynikiem pracy.
