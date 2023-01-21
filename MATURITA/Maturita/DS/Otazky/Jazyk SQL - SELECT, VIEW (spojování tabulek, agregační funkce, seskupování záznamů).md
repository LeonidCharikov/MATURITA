Jazyk SQL - SELECT, VIEW (spojování tabulek, agregační funkce, seskupování záznamů)


- ==SELECT== příkaz je jedním z nejdůležitějších příkazů v jazyku SQL. Slouží k výběru dat z tabulky nebo více tabulek.


Příklad:
```sql
SELECT * FROM products;
```
Tento příkaz vybere všechny sloupce a řádky z tabulky products.

```sql
SELECT name, price FROM products WHERE price > 10 ORDER BY price DESC;
```
Tento příkaz vybere sloupce name a price z tabulky products, kde je cena větší než 10 a seřadí je sestupně podle ceny.

-----------------------------------------------------------------------

- Views jsou virtuální tabulky, které se skládají z dat jiných tabulek. Jsou to jakési dotazy, které se dají opakovaně spouštět bez nutnosti opakovaně psát dotaz.


Příklad:
```sql
CREATE VIEW expensive_products AS
SELECT name, price FROM products WHERE price > 100;
```
Tento příkaz vytvoří virtuální tabulku expensive_products, která obsahuje data z tabulky products, kde je cena větší než 100.

```sql
SELECT * FROM expensive_products;
```
Tento příkaz vybere všechny sloupce a řádky z virtuální tabulky expensive_products.


 - Spojování tabulek je proces, který umožňuje propojit data z více tabulek. Je to jedna z klíčových funkcí pro práci s databází.

Příklad:
```sql
SELECT users.name, products.name FROM users
JOIN orders ON users.id = orders.user_id
JOIN products ON orders.product_id = products.id;
```
Tento příkaz vybere sloupce name z tabulky users a products, přičemž propojuje řádky z tabulky users s tabulkou orders pomocí sloupce user_id a tabulky orders s tabulkou products pomocí sloupce product_id.

-----------------------------------------------------------------------

- Agregační funkce jsou funkce, které se používají k seskupování a agregaci dat. Tyto funkce jsou ==COUNT, SUM, AVG, MIN, MAX==.


Příklad:
```sql
SELECT COUNT(id) FROM products;
```
Tento příkaz vybere počet řádků v tabulce products.


```sql
SELECT SUM(price) FROM products WHERE category = 'Electronics';
```
Tento příkaz vybere průměrnou cenu produktů podle kategorie z tabulky products.

-----------------------------------------------------------------------

- Seskupování záznamů se používá k agregaci dat v rámci skupiny řádků.


Příklad:
```sql
SELECT category, SUM(price) FROM products GROUP BY category;
```
Tento příkaz vybere kategorii a součet cen produktů v kategoriích z tabulky products. Data jsou seskupena podle kategorie.


- Je důležité si uvědomit, že SELECT, VIEW, spojování tabulek, agregační funkce a seskupování záznamů jsou klíčové funkce pro práci s databází. Je důležité dobře znát jazyk SQL a správně používat jednotlivé funkce pro různé účely. Je také důležité znát principy normalizace dat, aby bylo možné data správně seskupit a agregovat.

