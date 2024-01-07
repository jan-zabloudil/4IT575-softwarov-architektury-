# Architektura backend aplikace

## ID

3

## Status 

Accepted

## Context 

Na základě závěrů [ADR 1](1-platforms.md) a [ADR 1.1](1.1-server-client.md) je třeba zvolit architekturu pro serverovou (backend) aplikaci.

## Decision  

Při výběru architektury byly jako klíčové určeny následující vlastnosti:
- škálovatelnost,
- elasticita,
- odolnost vůči chybám,
- výkonnost.

Aplikace musí být schopná zvládnout prudký nárůst uživatelů v konkrétních časových úsecích (např. při zahájení prodeje listků na očekáváný koncert), při takových situacích musí být výkonná a odolná vůči chybám. Některé události je třeba zpracovat okamžitě (např. označení určitého místa za koupené), naopak u jiných událostí může dojít k prodlení (odeslání potvrzovacího emailu).

Jako vhodné byly vybrány [**Událostmi řízená architektura**](architectures-eda.md) a [**Microservice architektura**](architectures-microservice.md).

> [!IMPORTANT]
> Bylo rozhodnuto více rozpracovat **Událostmi řízenou architekturu** a to z následujících důvodů:
> - Aplikace nevyžaduje tak rozlišnou míru funkcionality, aby byl plně využit potenciál mikroslužeb.
> - Událostmi řízená architektura je výkonnější a umožňuje dobře implementovat asynchronní chování.
> - Obě architektury jsou komplexní a vyžadují správnou implementaci, aby nedošlo k narušení integrace dat.

## Consequences

**Integrita dat a zpracování chyb**
- Při implementaci klást důraz na schopnost udržet integritu dat a zpracování chyb, protože tyto činnosti mohou být slabým místem architektury.
- Důležitost monitoringu a logování chyb.

**Message broker**
- Je třeba zvolit message broker, který bude mít na starost řízení událostí.

### [Zpět na obsah](../README.md#obsah)