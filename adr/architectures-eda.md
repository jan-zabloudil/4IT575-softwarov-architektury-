# Událostmi řízená architektura

Cílem aplikace je umožnit nákup vstupenek, což je jen sled událostí od výběru koncertu až po zakoupení lístků a proto byla zvolena událostmi řízená architektura, **mezi její výhody patří:**
- Asynchronní zpracování
- Škálovatelnost
- Výkonnost 
- Odolnost vůči chybám

**Nevýhody architektury:**
- Komplexní workflow
- Zpracování chyb
- Horší zotavitelnost z pádu 
- Hrozí nekonzistence dat