# Atalanta

## Zadání
- [[lab.pdf]]

## Podklady
- [Atalanta manuál](https://ddd.fit.cvut.cz/www/prj/Atalanta-M/index.php?page=manual)

```c17.bench
# c17
# 5 inputs
# 2 outputs
# 0 inverter
# 6 gates ( 6 NANDs )

INPUT(1)
INPUT(2)
INPUT(3)
INPUT(6)
INPUT(7)

OUTPUT(22)
OUTPUT(23)

10 = NAND(1, 3)
11 = NAND(3, 6)
16 = NAND(2, 11)
19 = NAND(11, 7)
22 = NAND(10, 16)
23 = NAND(16, 19)
```

## Zpracování
Vytvoření úplného testu pro obvod **c17**.
```bash
.\atalanta.exe -l c17.lst c17.bench
```
Vytvoří se soubory:
- `c17.test`,
- `c17.lst`.

Ověřte výsledek testu tím, že zkontrolujete všechny vygenerované soubory Spusťte 
poruchový simulátor HOPE příkazem:
```bash
.\hope.exe -l hope.log -t c17.test c17.bench -u
```
Vytvoří se soubor:
- `hope.log`.

Proveďte příkaz:
```bash
.\atalanta.exe -l c17.lst -N c17.bench
```
Získáte soubor `c17.test` který obsahuje vyšší počet vektorů (nebyla provedena 
kompakce vektorů), který je lépe využitelný pro sestavení slovníku poruch. 

### 4. Sestavení  komprimovaného slovníku poruch
Sestavte  komprimovaný  slovník  poruch  metodou  záznamu  první  chybné  odezvy.  
Slovník  získáme  tak,  že  ze  seznamu  vygenerovaných  testovacích  vektorů  odstraníme  
postupně poslední vektory a postupně spouštíme simulátor HOPE. Seznam 
nedetekovaných  poruch  bude  odpovídat  poruchám  detekovatelným  v krocích  testu,  
odpovídajících odstraněným vektorům.

```text
* Test patterns and fault free responses:
   1: 00000 00
   2: 10001 01
   3: 01100 11
   4: 00110 00
   5: 01010 11
   6: 10110 10
   7: 11110 10
   8: 11111 10
```

```text
* List of undetected faults:
   1. 22 /1
   2. 10 /1
   3. 22 /0
   4. 16->22 /1
   5. 3->10 /1
   6. 1 /1
   7. 3 /0
   8. 3 /1
   9. 16 /1
  10. 16 /0
  11. 11->16 /1
  12. 2 /1
  13. 11 /0
  14. 3->11 /1
  15. 11 /1
  16. 6 /1
  17. 23 /1
  18. 19 /1
  19. 23 /0
  20. 16->23 /1
  21. 11->19 /1
  22. 7 /1
```

Slovník poruch:

| Vektor | ff response | Detekovaná porucha |
|--------|-------------|--------------------|
| 11111  | 10          | 11->19 /1          |
| 11110  | 10          | 11->16 /1, 11 /1   |
| 10110  | 10          | 10 /1, 3 /0        |
| 01010  | 11          | 3->11 /1           |
| 00110  | 00          | 1 /1               |
| 01100  | 11 | 22 /0, 16->22 /1, 16 /1, 6 /1, 16->23 /1 |
| 10001  | 01 | 3->10 /1, 3 /1, 11 /0, 19 /1, 23 /0 |
| 00000  | 00 | 22 /1, 16 /0, 2 /1, 23 /1, 19 /1, 7 /1 |

#### Testování poruch na simulátoru

Soubor `c17.circ` otevřete v programu Logisim.

![[c17.png]]

### Generování testu pro větší obvod
```bash
.\atalanta.exe -l c7552.lst -N c7552.bench
```

```text
1. Circuit structure
   Name of the circuit                       : c7552
   Number of primary inputs                  : 207
   Number of primary outputs                 : 108
   Number of gates                           : 3512
   Level of the circuit                      : 43

2. ATPG parameters
   Test pattern generation mode              : RPT + DTPG + TC
   Limit of random patterns (packets)        : 16
   Backtrack limit                           : 10
   Initial random number generator seed      : 1744807243

3. Test pattern generation results
   Number of test patterns                   : 380
   Fault coverage                            : 98.252 %
   Number of collapsed faults                : 7550
   Number of identified redundant faults     : 71
   Number of aborted faults                  : 61
   Total number of backtrackings             : 816

4. Memory used                               : 19800 Kbytes

5. CPU time
   Total                                     : 1.567 secs
```

| Obvod | Počet testů | Pokrytí | Čas na CPU |
|-------|-------------|---------|------------|
| c17   | 8           | 100%    | 0.001 sec  |
| c432  | 81          | 99%    | 0.001 sec   |
| c1908 | 168         | 99%    | 0.001 sec   |
| c5315 | 216         | 98.897% | 0.001 sec  |
| c6288 | 59          | 98.5%   | 0.267 sec  |
| c7552 | 380         | 98.252% | 1.567 sec  |

Přidat větší množství opakování pro navýšení pokrytí.