# Důležité vlastnostni systému

## ID

5

## Status 

Accepted

## Context 

Jako klíčové byby definovány následující vlastnosti systému:
- Umožnit souběžný nákup vstupenek.
- Neprodat žádné místo více než jednou.
- Nakupující vidí přehled zbývajících míst.

Je třeba rozhodnout, jak bude zajištěno, aby těmito vlastnosti systém skutečně disponoval. 

## Decision 

Chování systému v kontextu výše zmíněných vlastnosti bylo definováno následovně:
- **Uživatel po přidání vstupenek do nákupního košíku má 15 minut na dokončení nákupu**. Pokud tak neučiní, vstupenky mu budou z košíku vyhozeny (a opět dostupné k rezervaci). Uživatel bude přesměrován zpět na 1. krok nákupního košíku a v košíku zůstanou pouze vstupenky, u kterých zatím neuběhla 15 minutová lhůta.
  - Vstupence je v databázi nastaven příznak rezervace a je přiřazena konkrétnímu uživateli.
  - Zároveň je vytvořena událost, která po 15 minutách příznak v databázi zruší, pokud v mezičase uživatel vstupenku nezakoupí či neodebere z košíku.
- Pokud v jednu chvíli **bude vstupenky na určitý koncert vybírat více než 5000 lidí, dalším uživatelům už nebude přístup umožněn a budou zařazeni do fronty**. K nákupu budou vpuštěni, jakmile uživatelé před nimi dokončí nákup či opustí stránku. 
- Oba výše zmíněné parametry jsou konfigurovatelné v administraci systému. 
- Aby byl schopný systém obsloužit najednou velké množství uživatelů, byla zvolena architektura s asynchronním zpracováním události - viz [ADR 3](../adr/3-backend.md).
- Události **rezervace a nákupu vstupenky jsou v systému zpracovány přednostně a mají největší prioritu**, tak aby byla dostupnost vstupenek vždy aktuální.
- Prioritně nejsou zpracovány všechny události nákupu a rezervace vstupenek, ale pouze následující:
  - Označení vstupenky jako rezervované/prodané/opět dostupné v databází. 
  - Aktualizace pohledu s přehledem dostupných vstupenek.
  - Akce jako odeslání potvrzovacího e-mailu mohou byt zpracovány asynchronně s větším odstupem.
- Pokud by nedošlo k úspěšnému zpracování události rezervace či nákupu vstupenky, systém chyby detekuje a ihned upozorní administrátory systému. 

### [Zpět na obsah](../README.md#obsah)