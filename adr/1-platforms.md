# Platformy systému

## ID

1

## Status 

Accepted

## Context 

Navrhujeme nový portál pro prodej vstupenek na koncerty a potřebujeme rozhodnout, na jakých platformách budou moci uživatelé vstupenky zakoupit.

## Decision 

Rozhodnutí je vyvinout prozatím pouze **webovou aplikací** a to z následujících důvodů:
- Vytváříme zcela nový systém a chceme ověřit funkcionalitu a business model předtím, než investujeme do vývoje aplikací na více platformách.
- Webová aplikace umožňuje uživatelům využívat platformu na všech standardních zařízeních - mobilních telefonech, tabletech i počítačích.
- Většina uživatelů nakupuje vstupenky v jednotkách případů ročně, tudíž i sami preferují nákup z webové aplikace, protože nejsou ochotni instalovat aplikaci na své mobilní zařízení. 
- Společnost investuje převážně do internetové reklamy propagující jednotlivé koncerty. Reklamy směřují přímo do webové aplikace, kde je možné vstupenky zakoupit.

Nicméně společnost plánuje, že pokud se funkcionalita systému osvědčí, budu vytvořena také mobilní aplikace pro operační systém Android a iOS.

## Consequences

Nákup vstupenek na koncert je poměrně jednoduchá operace, a velká část uživatelů tak bude využívat aplikaci na svém mobilním zařízení, je tedy třeba brát v potaz následující:
- Aplikace musí mít responzivní design a být dostatečně interaktivní.
- Aplikace musí být optimalizovaná pro použití na mobilních telefonech se slabším připojením. Je třeba dbát na rychlost aplikace a datovou náročnost (optimalizace multimediálního obsahu apod.).

Je třeba navrhnout takovou architekturu, aby bylo možné v budoucnu implementovat mobilní aplikaci.

###[Zpět na obsah](../README.md#obsah)