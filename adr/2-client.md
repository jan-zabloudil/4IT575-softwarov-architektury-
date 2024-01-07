# Architektura klientské aplikace

## ID

2

## Status 

Accepted

## Context 

Na základě závěrů z [ADR 1](1-platforms.md) a [ADR 1.1](1.1-server-client.md) je třeba rozhodnout, jak bude vyvíjena klientská webová aplikace. 

## Decision 

Bylo rozhodnuto, že aplikace bude vyvíjena v technologii Nuxt.js:
- Framework pro vytváření webových aplikací postavený na Vue.js
- Bohatá funkcionalita:
  - Vue.js (javascriptový framework) umožňuje vytvářet interaktivní rozhraní,
  - routing,
  - data fetching (komunikace se server aplikací),
  - caching,
  - deployment,
  - testings.

Tato technologie se osvědčila při vývoji jiných projektů, naopak frontendoví vývojáři nemají zkušenosti s vývojem s využitím knihovny React či frameworku AngularJS, které se nabízejí jako alternativy.   

## Consequences

Při návrhu infrastruktury je potřeba vybrat platformu, která umožňuje nasazení bezproblémové nasazení Nuxt aplikací.