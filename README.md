# Reprodukowalność badań — Unreal Engine 5

Repozytorium towarzyszy pracy dyplomowej dotyczącej wpływu wybranych technologii Unreal Engine 5 na wydajność renderowania scen krajobrazowych.

## Cel repozytorium

Celem repozytorium jest umożliwienie **odtworzenia procedury eksperymentalnej** i zweryfikowania sposobu uzyskania wyników bez publikowania kompletnego projektu Unreal Engine, pełnych Blueprintów, kodu źródłowego ani wszystkich zasobów wykorzystanych w scenach.

Repozytorium dokumentuje:
- wersję silnika i konfigurację stanowiska,
- ustawienia renderowania wspólne dla testów,
- warianty eksperymentalne,
- procedurę pomiarową,
- sposób opracowania danych,
- wyniki referencyjne opublikowane w pracy,
- ograniczenia reprodukcji.

## Czego repozytorium nie zawiera

Repozytorium celowo **nie zawiera**:
- kompletnych projektów Unreal Engine,
- pełnego kodu programu,
- kompletnych Blueprintów,
- komercyjnych lub licencjonowanych assetów,
- treści, których dalsze rozpowszechnianie mogłoby naruszać warunki licencyjne.

Brak pełnego projektu nie jest przypadkowy: publikowany jest zestaw informacji wystarczający do odtworzenia metodologii i zbudowania równoważnych wariantów testowych, przy zachowaniu ochrony autorskich rozwiązań i praw do zasobów.

## Najważniejsze parametry wspólne

- Unreal Engine: **5.5.4**
- RHI: **DirectX 12**
- antyaliasing / skalowanie: **TSR**
- profil jakości: **Epic**
- rozdzielczość: **1280 × 720**
- tryb wyświetlania: **Windowed**
- `r.ScreenPercentage = 100`
- `r.DynamicRes.OperationMode = 0`
- `r.VSync = 0`
- `t.MaxFPS = 500`
- `r.Streaming.PoolSize = 2000`

Szczegóły: `configs/common_settings.txt`.

## Procedura pomiarowa w skrócie

1. Uruchomić odpowiedni wariant sceny.
2. Ustawić widok kamery odpowiedni dla danego środowiska i zachować go bez zmian w obrębie porównania.
3. Odczekać okres stabilizacji:
   - standardowo 30 s,
   - dla środowiska 3: co najmniej 180 s.
4. Rejestrować parametry dłużej niż 60 s przy użyciu CSV Profiler.
5. Do analizy wykorzystać 60-sekundowy fragment rozpoczynający się 1 s po rozpoczęciu zapisu.
6. Nie poruszać kamerą ani nie wykonywać innych działań podczas rejestracji.
7. Dla każdej stabilnej konfiguracji wykonać 3 powtórzenia.
8. W wariantach porównawczych wykonywać przebiegi naprzemiennie.

Pełny opis: `docs/measurement_protocol.md`.

## Warianty testowe

Tabela wariantów znajduje się w `configs/test_variants.csv`.

### Środowisko 1
Niewielka scena wewnętrzna o relatywnie niskiej złożoności geometrycznej. W scenie wykorzystanej w pracy znajdowały się m.in. stolik, krzesło, drzwi oraz drobne elementy wyposażenia. Do powtórzenia eksperymentu nie jest wymagane użycie tych samych modeli; istotne jest zachowanie tej samej geometrii, materiałów i kadru kamery pomiędzy porównywanymi wariantami.

Porównanie:
- statycznego, uprzednio wygenerowanego oświetlenia,
- Lumen Global Illumination + Lumen Reflections.

### Środowisko 2
Scena krajobrazowa zawierająca dużą liczbę elementów roślinności widocznych na pierwszym, średnim i dalekim planie. Oryginalne zasoby roślinności pochodziły z Fab, ale do powtórzenia eksperymentu można zastosować równoważny zestaw. Zasoby powinny umożliwiać wykorzystanie Nanite, deformacji WPO oraz klasycznych poziomów LOD. Elementy architektoniczne, np. zamek lub ruiny, nie muszą być identyczne.

Porównanie Nanite ON/OFF:
- bez oceny WPO,
- przy intensywnej deformacji WPO.

Dla wariantu intensywnego WPO:
- Wind Strength = 8.0
- Wind Speed = 2.0
- Wind Noise = 5.0
- Wind Tiling = 0.5

### Środowisko 3
Wykorzystano projekt demonstracyjny **Valley of the Ancient** udostępniany przez Epic Games i pobierany przez Epic Games Launcher. Badania wykonano w wersji projektu dostępnej w okresie realizacji eksperymentów, uruchomionej w Unreal Engine 5.5.4.

Planowane było porównanie Nanite ON/OFF. Wariant OFF okazał się niestabilny po ustawieniu:
- `r.Nanite.ProxyRenderMode = 0`
- `r.Nanite 0`

Pełną serię pomiarową przeprowadzono wyłącznie dla aktywnego Nanite.

### Wymagania dotyczące kadru
Nie jest wymagane odtworzenie identycznych współrzędnych `CameraActor`. W obrębie danego porównania położenie, orientacja i pole widzenia kamery muszą jednak pozostać niezmienne. Kadr powinien zachowywać funkcjonalnie podobny zakres widocznej geometrii:
- środowisko 1 — niewielkie wnętrze z kilkoma obiektami i powierzchniami oświetlanymi w obu wariantach,
- środowisko 2 — duża liczba drzew na pierwszym, średnim i dalekim planie,
- środowisko 3 — wysokoszczegółowa geometria widoczna w pobliżu kamery oraz na średnim i dalekim planie.

## Narzędzia diagnostyczne

- CSV Profiler — rejestracja danych klatkowych,
- `stat unit`,
- `stat GPU`,
- `stat RHI`,
- `stat memory`,
- Unreal Insights — analiza jakościowa i diagnostyka.

## Opracowanie wyników

Dla każdego przebiegu obliczana jest średnia wartość parametru z analizowanego 60-sekundowego fragmentu. Następnie dla 3 powtórzeń obliczana jest średnia oraz odchylenie standardowe z próby.

Szczegóły i wzory: `docs/analysis_method.md`.

## Wyniki referencyjne

Wartości opublikowane w pracy zapisano w:
- `data/reference/results_summary.csv`

Nie są to surowe logi CSV Profiler; służą jako punkt odniesienia do sprawdzenia poprawności ponownego eksperymentu.

## Warunki odtworzenia eksperymentu

Repozytorium umożliwia odtworzenie **metodyki, konfiguracji pomiarowej i sposobu analizy** oraz zbudowanie równoważnych środowisk testowych. Nie jest jego celem odtworzenie identycznych scen piksel w piksel ani publikacja kompletnego projektu Unreal Engine.

Dla poprawnego porównania najważniejsze jest zachowanie tych samych ustawień renderowania i niezmiennego kadru w obrębie danego eksperymentu. Dokładne współrzędne kamery i identyczne modele nie są wymagane, jeśli scena zachowuje opisaną charakterystykę obciążenia.

Repozytorium celowo nie zawiera surowych logów CSV Profiler. Zawiera natomiast zweryfikowane wyniki referencyjne wykorzystane w pracy, parametry wariantów oraz pełną procedurę rejestracji i opracowania danych. Szczegóły: `docs/reproducibility_scope.md`.

## Prawa i wykorzystanie

Patrz `LICENSE_NOTICE.md`.
