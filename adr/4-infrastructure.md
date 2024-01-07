# Infrastruktura

## ID

4

## Status 

Accepted

## Context 

Je třeba rozhodnout, kde bude systém umístěn a prozován.

## Decision 

Vzhledem k tomu, že systém musí být schopný zvládnout prudký nárůst uživatelů v konkrétních časových úsecích, je škálovatelnost a elasticita klíčová. Z tohoto důvodu bylo rozhodnuto, že **systém bude provozován v cloudu**, což nabízí následující výhody:
- škálovatelnost a elasticita,
- skvělá podpora pro vybrané architektury,
- bezpečnost,
- monitoring,
- bohatá funkcionalita (load balancers,...).

3 největší cloudové služby jsou Amazon Web Services, Google Cloud, Microsoft Azure. Byl zvolen **Amazon Web Services**, a to z následujících důvodů:
- Platforma byla ověřena na minulých projektech.
- Skvělá podpora pro všechy využívané technologie - Nuxt, PostgreSQL, Kafka.
- Přijatelná cena.
- Nabízí veškerou funkcionalitu pro implementaci událostmi řízené architektury.

## Consequences

Je třeba navrhnout celé DevOps workflow.