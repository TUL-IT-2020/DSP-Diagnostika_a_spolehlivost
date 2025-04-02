# Atalanta

## Zadání
![[lab.pdf]]

## Zpracování
Vytvoření úplného testu pro obvod `c17`.
```bash
.\atalanta.exe -l c17.lst c17.bench
```
Vytvoří se soubory:
- `c17.test`,
- `c17.lst`.

Otestování:
```bash
hope.exe -l hope.log -t c17.test c17.bench –u
```
Vytvoří se soubor:
- `hope.log`.