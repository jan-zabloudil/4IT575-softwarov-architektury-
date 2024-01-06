# Architektura backend aplikace

## ID

3

## Status 

Accepted

## Context 

Na základě závěrů ADR 1 a ADR 1.1 je třeba zvolit architekturu pro serverovou (backendovou) aplikaci.

## Decision  

Při výběru architektury byly jako klíčové určeny následující vlastnosti:
- Škálovatelnost
- Elasticita
- Odolnost vůči chybám
- Výkonnost

Aplikace musí být schopná zvládnout prudký nárůst uživatelů v konkrétních časových úsecích (např. při zahájení prodeje listků na očekáváný koncert), při takových situacích musí být výkonná a odolná vůči chybám. Některé události je třeba zpracovat okamžitě (např. označení určitého místa za koupené), naopak i jiných událostí může dojít k prodlení (odeslání potvrzovacího emailu).

Jako vhodné byly vybrány **Událostmi řízená architektura** a **Microservice architektura**.

### Událostmi řízená architektura

Cílem aplikace je umožnit nákup vstupenek, což je jen sled událostí od výběru koncertu až po zakoupení lístků a proto byla zvolena událostmi řízená architektura, **mezi její výhody patří**
- Asynchronní zpracování
- Škálovatelnost
- Výkonnost 
- Odolnost vůči chybám

**Nevýhody architektury**
- Komplexní workflow
- Zpracování chyb
- Horší zotavitelnost z pádu 
- Hrozí nekonzistence dat

### Microservice architektura

Architektura oddělených služeb, které spolu komunikují přes sít pomocí nezávislých protokolů (např. HTTP). 

**Výhody architektury**
- Elasticita a škálovatelnost
- Udržitelné a dobře testovatelné
- Lze je samostatně nasazovat
- Jednotlivé služby lze vyvíjet v odlišných programovacích jazycích, pro každou službu lze tak zvolit jazyk, který nejlépe funguje pro daný případ užití.

**Nevýhody architektury**
- Často náročné určit správnou míru granuality (jak rozdělit aplikaci do jednotlivých služeb)
- Pokud není implementované správně, údržba je naopak náročná (příliš mnoho služeb, odlišné programovací jazyky...)
- Nižší celkový výkon (komunikace přes síť)
- Hrozí ztráta integrace dat
- Velice drahé

> [!IMPORTANT]
> Bylo rozhodnuto více rozpracovat *událostmi řízenou architekturu* a to z následujících důvodů:
> - Aplikace nevyžaduje tak rozlišnou míru funkcionality, aby byl plně využit potenciál microslužeb
> - Událostmi řízená architektura je výkonnější a umožňuje dobře implementovat asynchronní chování
> - Obě architektury jsou komplexní a vyžadují správnou implementaci, aby nedošlo k narušení integrace dat.

## Consequences

**Integrita dat a zpracování chyb**
- Při implementaci klást důraz na schopnost udržet integritu dat a zpracování chyb, protože tyto činnosti mohou být slabým místem architektury.
- Důležitost monitoringu a logování chyb

**Message broker**
- Je třeba zvolit message broker, který bude mít na starost řízení událostí.