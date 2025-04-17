# Spolehlivost

- Zjištování ... měření
- Předvídání ... predikce
- Řízení ... FMECA

> [!tip] Spolehlivost
> Schopnost plnit požadovanou funkci v daném čase a podmínkách.

dependebility:
- bezpuruchovost, udržovatelnost, ...

## Distribuční funkce
V nekonečnu se vše rozbije.

F(t) - pravděpodobnost, že porucha nenastane do doby t
- t - doba do poruchy
- 0 <= F(t) <= 1
- F v nekonečnu je 0

Q(t) - pravděpodobnost, že porucha nastane do doby t
- Q(t) = 1 - F(t)
- 0 <= Q(t) <= 1
- Q v nekonečnu je 1

### Emperická hodnota:
$$
\hat Q(t) = \frac{n(t)}{\bar n}
$$
- $n (t)$ - počet poruch, do doby t
- $\bar n$ - počet zařízení

## Hustota poruch:
$$
f(t) = \frac{dQ(t)}{dt}
$$

### Empericky:
$$
\hat f(t) = \frac{\bar n (t+ \Delta t) - \bar n (t)}{n \cdot \Delta t}
$$

## Intezita poruch

Počet porušených za dt.
Ku
Počeu neporušených krát dt.

## Střední doba do poruchy:
$$
T = 1/ \lambda
$$
- polovina výrobků se porouchá do doby T.

MTTF - mean time to failure
Střední doba do "první" poruchy.

### Vanová křivka
"Bath curve"
- Velké množství poruch na začátku, pak klesá.
- Pak užitečná životnost.
- Pak opět vzrůstá, končí se životnost.

## Modely systému
Seriový model

Paralelní model

