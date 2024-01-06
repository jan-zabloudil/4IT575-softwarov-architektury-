# Microservice architektura

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