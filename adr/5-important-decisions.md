# Důležité vlastnostni systému

## ID

5

## Status 

Accepted

## Context 

Jako klíčové vlastnosti systému byly definovány následujcí vlastnosti:
- Umožnit souběžný nákup vstupenek.
- Neprodat žádné místo více než jednou.
- Nakupující vidí přehled zbývajících míst.

 Je třeba rozhodnout, jak bude zajištěno, aby těmito vlastnosti systém skutečně disponoval. 

## Decision 

Chování systému v kontextu výše zmíněných vlastnosti bylo definováno následovně:
- Uživatel po přidání vstupenek do nákupního košíku má 15 minut na dokončení nákupu. Pokud tak neučiní, vstupenky mu budou z košíku vyhozeny (a opět dostupné k rezervaci). Uživatel bude přesměrován zpět na 1. krok nákupního košíku a v košíku zůstanou pouze vstupenky, u kterých zatím neuběhla 15 minutová lhůta.
- Pokud v jednu chvíli bude vstupenky na určitý koncert vybírat více než 5000 lidí, dalším uživatelům už nebude přístup umožněn a budou zařazeni do fronty. A k nákupu budou vpuštěni, jakmile lidé před nimi dokončí nákup či opustí stránku. 
- Oba výše zmíněné parametry jsou konfigurovatelné v administraci systému. 
- Události rezervace a nákupu vstupenky jsou v systému zpracovány přednostně a mají největší prioritu. Pokud by nedošlo k úspěšnému zpracování takové události, systém chyby detekuje a ihned upozorní administrátory systému. 

**TODO dospat, že je to formou asynchronního zpracování -> lidé vidí volná místa, mohou nakupovat souběžně**

## Consequences

**TODO**