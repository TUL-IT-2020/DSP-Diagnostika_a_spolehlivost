# Spolehlivost

![[Spolehlivost.png]]

Všechny prvky mají parametr pravděpodobnosti poruchy na: $1^{-6}$

> [!example]
> - R - 2 sériově
> - G - TMR
> - B - 2 paralelně
> - Bl - jeden

![[Srovnání NMR.png]]

> [!example]
> - R - 5MR
> - G - 3MR
> - B - 3 paralelně
> - Bl - jeden

U 3 paralelně stačí aby byl "funkční" jen jeden a systém funguje dále. Problém je že moduly musí umět detekovat vlastní chybu.

O proti tomu NMR obsahuje vouter - majoritní hlasování.
3MR - alespoň 2 funkční.
5MR - alespoň 3 funkční.

5MR klesá v pozdějším čase rychleji než 3MR, protože čím více modulů tvoří náš systém, tím je větší šance, že nějaký z nich selže. 