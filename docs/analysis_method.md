# Opracowanie danych

## Zakres danych

Dla każdego przebiegu analizowany jest 60-sekundowy fragment rejestracji,
rozpoczynający się po pierwszej sekundzie od rozpoczęcia zapisu CSV Profiler.

## Etap 1 — średnia z pojedynczego przebiegu

Dla każdej mierzonej wielkości wyznaczana jest średnia z kolejnych klatek
należących do analizowanego fragmentu.

## Etap 2 — agregacja trzech powtórzeń

Dla każdej konfiguracji wyznacza się:
- średnią z wartości uzyskanych w trzech przebiegach,
- odchylenie standardowe z próby.

Wzór:

SD = sqrt( sum((x_i - mean(x))^2) / (n - 1) )

gdzie n = 3.

## FPS

FPS wyznaczano na podstawie średniego czasu generowania klatki:

FPS = 1000 / FrameTime_ms

## Zmiana procentowa

Delta X [%] = ((X_badany - X_bazowy) / X_bazowy) * 100

Interpretacja zależy od parametru:
- wzrost FPS = poprawa wydajności,
- spadek Frame Time / GPU Time / czasów CPU = poprawa wydajności.

## Ważne ograniczenie

Wskaźniki pamięci nie stanowią głównej podstawy ilościowego porównania,
ponieważ używany Radeon 760M jest zintegrowanym GPU korzystającym z pamięci współdzielonej.
