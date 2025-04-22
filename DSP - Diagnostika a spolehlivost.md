# Diagnostika a spolehlivost

## Literatura
- ČVUT Jan Hlavička Diagnostika a Spolehlivost
- [[Diagnostika a spolehlivost - cvičení.pdf]]
## Obsah předmětu:
1. Úvod do diagnostiky, základní pojmy, typy testů. 
2. Testování číslicových obvodů: defekty, chyby, selhání, poruchy. Generování testů kombinačních obvodů, intuitivní zcitlivění cesty.
 3. Booleovská diference, D-algoritmus.
 4. Generování testů pro sekvenční obvody,tabulky úplných testů, minimalizace testů, lokalizace poruch.
 5. Testování mikroprocesorů, obvodů SoC, pamětí.
 6. IDDQ testování, testery, Návrh obvodu pro snadnou testovatelnost.
 7. Vestavěné diagnostické prostředky – generování test. vzorků, komprese vzorků a odezev.
 8. Zabezpečení proti poruchám, samočinně kontrolované obvody.  
 9. Úvod do teorie spolehlivosti. Spolehlivostní modely, výpočty spolehlivostních ukazatelů.
 10. Zálohování systémů, statická a dynamická záloha. Systémy odolné proti poruchám, jejich návrh a použití.
## Cvičení

Doma, projít si skripta:
- [x] Kapitola 2. do vypracovat úlohy 
- [x] 2.2
	- [x] D-krychle přes XOR
- [ ] 2.3
	- [ ] Boolovská diference (vyzkoušet si)
		- [ ] Z definice
		- [ ] F, F' tabulku (důležitější)
- [ ] 3
	- [ ] Minimalizace testů
- [ ] 6
  - [ ] návrh snadno testovatelných obvodů
- [ ] Spolehlivost
- [x] [[atalanta.md|Atalanta]]
  - [x] Jednoduchý obvod
  - [x] Složité obvody
  - [x] Přidat větší množství opakování pro navýšení pokrytí.

## Zkouška
Ústní zkoušení. 
- Vypracovat cvičení, 
- projít přednášky.
## Poznámky:

- [ ] Dopsat poznámky k automatům

- [[Defekty a poruchy]]
- [[Testování a verifikace]]
	- [[D-algoritmus]]
	- [[Boolovská diference]]
	- [[IDDQ]]
	- [[Testování sekvenčních obvodů]]
- [[Obvody bezpečné proti poruchám]]
- [[CIT_Spolehlivost|Spolehlivost]]

[[Boundry Scan - JTAG]]
[[BIST]]


### Zkratky
- VLSI - very large system integration
- SoC - system on chip

- SAT solvers - Satisfiability solvers
- TPG - Test pattern generator
- ATPG - Automatic test pattern generator
- TAM - Test Access Mechanism

Simulace - v software
Emulace - v HW (fpga)

## Další 

### SSBDD
BDD - binární rozhodovací strom (diagram)
SS - strukturně syntetizovaný


