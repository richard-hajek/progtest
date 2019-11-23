# Progtest Tester Skript

Skript testující progtestový projekt, možnost automaticky otestovat -fsanitize=address i valgrind.

## Použití
```
progtest <složka projektu> [-t test] [-i] [-a] [-v]
```

Tento skript očekává jako první argument složku, obsahující progtestový projekt, tedy soubor main.c nebo main.cpp. Dále musí obsahovat složku tests s progtestovými testy. (Tedy soubory <cislo>_in.txt a <cislo>_out.txt)

By default, tento skript projede všechny testy a reportne neproházející.

Pomocí `-t test` skript spustí jenom jeden test a vypíše detaily testu

`-i` spustí program v interaktivním režimu - bez testů

`-a` zkompiluje projekt s `-fsanitize=address`

`-v` spustí program pomocí `valgrind`

*Autor není zodpovědný za jakékoli škody způsobené používáním skriptu, obsahující ale ne limitující se na: špatně vyhodnocené testy, 0 z progtestu, vymazání celého disku nebo početí 3. světové války*
