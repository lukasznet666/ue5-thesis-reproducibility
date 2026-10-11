# Warunki odtworzenia eksperymentu

Pakiet dokumentuje konfigurację wspólną, warianty eksperymentalne, procedurę pomiarową, sposób opracowania danych oraz wyniki referencyjne. Jego celem jest umożliwienie zbudowania równoważnych środowisk testowych i powtórzenia sposobu wykonania eksperymentu bez publikowania kompletnego projektu Unreal Engine.

## Środowisko 1

Należy zastosować niewielką scenę wewnętrzną o relatywnie niskiej złożoności geometrycznej, zawierającą kilka prostych obiektów i powierzchni. W scenie użytej w pracy znajdowały się m.in. stolik, krzesło, drzwi oraz drobne elementy wyposażenia. Te same modele nie są wymagane. Geometria, materiały oraz kadr kamery muszą natomiast pozostać niezmienne pomiędzy wariantem ze statycznym oświetleniem i wariantem Lumen.

## Środowisko 2

Należy przygotować scenę krajobrazową zawierającą dużą liczbę elementów roślinności widocznych na pierwszym, średnim i dalekim planie. Oryginalna roślinność pochodziła z Fab, jednak można wykorzystać równoważny zestaw zasobów, jeżeli umożliwia on zastosowanie Nanite, deformacji WPO oraz klasycznych poziomów LOD. Zamek, ruiny i pozostałe elementy architektury mogą zostać zastąpione innymi obiektami o podobnej roli kompozycyjnej.

## Środowisko 3

Wykorzystano projekt demonstracyjny **Valley of the Ancient** udostępniany przez Epic Games i pobierany za pośrednictwem Epic Games Launcher. Badania wykonano w wersji projektu dostępnej w okresie realizacji eksperymentów, uruchomionej w Unreal Engine 5.5.4.

## Kamera

Nie jest wymagane odtworzenie identycznych wartości `Location`, `Rotation` ani `Field of View` obiektu `CameraActor`. W obrębie danego porównania wartości te muszą jednak pozostać niezmienne. Kadr powinien zachowywać funkcjonalnie podobny zakres widocznej geometrii i charakter obciążenia sceny.

## Dane pomiarowe

Pakiet nie zawiera surowych logów CSV Profiler. Udostępniono zweryfikowane wyniki referencyjne wykorzystane w pracy (`data/reference/results_summary.csv`) oraz kompletny opis rejestracji i opracowania danych. Pozwala to powtórzyć procedurę i porównać zależności pomiędzy wariantami bez konieczności publikowania niezweryfikowanych surowych logów.
