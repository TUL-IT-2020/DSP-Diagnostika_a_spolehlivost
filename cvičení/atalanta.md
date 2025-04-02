# Atalanta

## Zadání
- [[lab.pdf]]

## Podklady
```c17.bnech
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