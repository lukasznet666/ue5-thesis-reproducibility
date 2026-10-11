# Ograniczenia reprodukcji

1. Badania przeprowadzono na jednej platformie sprzętowej, dlatego wartości bezwzględne
   nie powinny być bezpośrednio przenoszone na inne komputery.

2. Środowisko 1 porównuje dwa kompletne sposoby realizacji oświetlenia, a nie pojedynczy
   przełącznik Lumen ON/OFF.

3. Po wyłączeniu Nanite w środowisku 2 wykorzystywane były istniejące poziomy LOD assetów.
   Nie były one specjalnie ujednolicane na potrzeby eksperymentu.

4. Warianty Nanite ON i OFF w środowisku 2 nie były całkowicie równoważne wizualnie.
   Wyniki opisują rzeczywistą konfigurację zastosowanych assetów.

5. W środowisku 3 nie uzyskano stabilnego wariantu Nanite OFF, dlatego nie ma ilościowego
   porównania ON/OFF.

6. W środowisku 3 trzy powtórzenia wykonano w ramach jednej ustabilizowanej sesji.
   SD opisuje zatem głównie powtarzalność w tej sesji.

7. Repozytorium służy do odtworzenia metody i równoważnych warunków testowych, a nie identycznej kopii scen.
   Na innym sprzęcie lub przy użyciu innych, równoważnych zasobów wartości bezwzględne mogą się różnić;
   podstawą porównania pozostają zależności pomiędzy wariantami w obrębie tego samego środowiska.
