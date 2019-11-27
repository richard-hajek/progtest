# Progtest Tester Skript

Skript testující progtestový projekt, možnost automaticky otestovat -fsanitize=address i valgrind.

## Použití
```
progtest-tester <project directory> [-v|--valgrind] [-a|--address] [-h|--help] [-i|--interactive] [-t|--test <testnum>] [-s|--sort] [-l|--linesort]
```

Tento skript očekává jako první argument složku, obsahující progtestový projekt, tedy soubor main.c nebo main.cpp. Dále musí obsahovat složku tests s progtestovými testy. (Tedy soubory cislo_in.txt a cislo_out.txt)

By default, tento skript projede všechny testy a reportne neproházející.

Pomocí `-t test` skript spustí jenom jeden test a vypíše detaily testu

`-i` spustí program v interaktivním režimu - bez testů

`-a` zkompiluje projekt s `-fsanitize=address`

`-v` spustí program pomocí `valgrind`

`-h` vypíše help

## Vysvětlení `-s` a `-l`

Některé programy nemusí mít na řádek stejný vstup, jako např. program Letová kontrola, kde vstupy

```
Alpha - Beta
Gamma - Delta
```

je ekvivalentní

```
Beta - Alpha
Delta - Gamma
```

To ale diff nechápe

Vlajky `-s` a `-l` různě manipulují výstupem, aby ho diff mohl zkontrolovat

### `-s`

`-s` seřadí řádky očekávaného výstupu i výstupu programu. Efektivně na oboje provede `| sort`

Tudíž je vhodný na programy, kde jednotlivé řádky musí být stejné, ale mohou být v jiném pořadí

### `-l`

`-l` seřadí celý očekávaný výstup i výstup programu na jeden řádek. 

Například z

```
Asdfg
po.lk
zzzzzzzz
```

se stane

```
.Adfglopzzzzzzz
```

Vlajka je tedy vhodná, když slova na každém řádku musí být stejná, ale mohou být v jiném pořadí. Toto pořadí se totiž ztratí a zůstane jenom dlouhý string s všemy písmeny výstupů

** Vlajka -l je zvláště náchylná na false positive! Např výstup 2.14 je roven 4.12**


*Autor není zodpovědný za jakékoli škody způsobené používáním skriptu, obsahující ale ne limitující se na: špatně vyhodnocené testy, 0 z progtestu, vymazání celého disku nebo početí 3. světové války*
