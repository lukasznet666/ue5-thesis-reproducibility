# Protokół pomiarowy

## 1. Warunki wspólne

- identyczna platforma sprzętowa dla porównywanych wariantów,
- identyczne ustawienia renderowania,
- identyczna pozycja, orientacja i pole widzenia kamery w obrębie danego porównania,
- brak ruchu kamery podczas rejestracji,
- brak interakcji użytkownika mogących zmienić renderowaną scenę.

## 2. Stabilizacja

### Środowiska 1 i 2
Po ustawieniu docelowego widoku: 30 s stabilizacji.

### Środowisko 3
Co najmniej 180 s stabilizacji z powodu dłużej utrzymujących się procesów inicjalizacji
i strumieniowania danych.

## 3. Rejestracja

Główne narzędzie: CSV Profiler.

Rejestrację prowadzono dłużej niż 60 s. Do analizy pobierano 60-sekundowy fragment
rozpoczynający się po upływie pierwszej sekundy od uruchomienia zapisu.

## 4. Powtórzenia

Dla każdej stabilnej konfiguracji: n = 3.

Warianty porównawcze mierzono naprzemiennie:
- przebieg 1 wariantu bazowego,
- przebieg 1 wariantu badanego,
- przebieg 2 wariantu bazowego,
- przebieg 2 wariantu badanego,
- przebieg 3 wariantu bazowego,
- przebieg 3 wariantu badanego.

Celem było ograniczenie wpływu zmian temperatury i warunków pracy platformy.

## 5. Monitorowane parametry

Podstawowe:
- Frame Time,
- GPU Time,
- Render Thread,
- Game Thread,
- FPS.

Uzupełniające:
- RHI Thread,
- draw calls,
- wybrane charakterystyki geometrii,
- wskaźniki wykorzystania pamięci jako dane pomocnicze.

## 6. Narzędzia

- CSV Profiler,
- stat unit,
- stat GPU,
- stat RHI,
- stat memory,
- Unreal Insights.

## 7. Nanite

Wyłączenie:
`r.Nanite 0`

Włączenie:
`r.Nanite 1`

Dla środowiska 3 przed wyłączeniem Nanite:
`r.Nanite.ProxyRenderMode 0`

W środowisku 2 po wyłączeniu Nanite działanie klasycznych poziomów LOD zweryfikowano
widokiem diagnostycznym Mesh LOD Coloration.
