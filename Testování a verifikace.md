# Testování a verifikace
Testujeme i na neočekávané vstupy

Verifikace -> ověření návrhu pracuje s modelem (umí Pentium počítat?)
Testování -> ověření fyzické součástky (vyrobili jsme to dobře?)

Formální verifikace -> porovnáváme zda dva různého modely téhož mají stejnou funkci.

Diagnostika = lokalizace
Testování = detekce

## Testování 

> [!info] "Testování"
> Funguje to vs nefunguje to.

> [!warning] Očekáváme že v jeden čas existuje právě jedna porucha

### Terminologie:
Funkční -> testuji všechny vstupu (známe chování obvodu, popis jeho funkcí)
Strukturní -> menší počet vektorů, testujeme strukturu (známe vnitřní strukturu)

Test vector -> digitální vzorky které přivádíme na vstupy
Test pattern -> testovac vekor + jeho odezva
Test set -> množina vstupů a výstupů
Test sequnce -> testovací vzory v časové posloupnosti

- Fault simulation - chování v případě poruchy
### Test
Test je množina kroků ověřující funkčnost.
Krok testů (dvojice vstup výstup).

úplný test -> pokrývá všechny poruchy (otestuje celý hw)
minimální test -> čas jsou peníze, tak ať to netrvá dlouho


Testování na různé úrovni:
- program,
- ISA,
- registry,
- hradla,
- tranzistory.

### Návrh testů:
- Chování
- struktura
- fyzikální jevy

|             | Domain                 |                |                |
| ----------- | ---------------------- | -------------- | -------------- |
| Level       | **Behavioral**         | **Structural** | **Physical**   |
| **System**  | System Specifications  | Blocks         | Chip           |
| **RTL**     | RTL Specifications     | Registers      | Macro Cells    |
| **Logic**   | Boolean Functions      | Logic Gates    | Standard Cells |
| **Circuit** | Differential Equations | Transistors    | Masks          |

### Design pro snadnou testovatelnost
Přidáme: 
- Testovací body do obvodu (sledovací).
- Nastavovací body (pro nastavení citlivé cesty)

Potřeba přístupu do všech registrů!
Problém -> příliš mnoho pinů.

Nahradilo se to posuvnými registry (máme přístup ke všem registrům).

Příliš mnoho registrů, dlouhá doba nahrávání do obvodu!
Přidání generátoru testů přímo do čipu.

BIST -> Build-in Self-Test
LSFR nám vygeneruje náhodné vstupu pro otestování.

## Metody testování

### IDDQ
- IDD - napájecí proud
- Q - trvalá změna napájecího proudu při určitém vstupu
Odhalování poruch měřením spotřeby obvodu, zejména u unipolárních tranzistorů.

### Intuitivní zcitlivění cesty
> [!tip] Intuitivní zcitlivění cesty
Nastavíme obvod (vstupním vektorem hodnot) tak aby se chyba (t1, t0) projevila až na výstupu.

Musíme znát strukturu obvodu.

### D-algoritmus
Hledáme jaké vstupy má mít obvod aby při dané poruše došlo ke změně výstupu. 

> [!note]
Formální tvoření citlivé cesty bez intuice.

1. Vytvoříme D-krychle obvodu.
2. Zvolíme si poruchu.
3. Vytvoříme primitivní D-krychle poruchy.
4. Propagace D na výstup (citlivá cesta)
5. Konzistence vektorů (zpětný průchod)
6. Pokračuji krokem 2 a zvolím si jinou poruchu.

D-krychle základních logických hradel

### Boolovská diference
Nemusíme znát strukturu obvodu.
Hledá pouze chybu na vstupu obvodu.

> [!tip]
Hledáme vektor vstupů takový, že při změně hodnoty na jednom vstupu a projeví se jako změna výstupu.

Vektory určíme z pravdivostní tabulky. 
Nebo odvodíme z funkce. 

