Jazyk SQL - DDL, DML příkazy

- Jazyk SQL se skládá z různých typů příkazů, které slouží k různým účelům. Mezi nejdůležitější patří DDL (Data Definition Language) příkazy a DML (Data Manipulation Language) příkazy.

 - ==DDL příkazy== slouží k definování a úpravě struktury databáze. Tyto příkazy se týkají tabulek, sloupců, indexů, atd.
    -   ==CREATE== - vytváří novou tabulku, index, nebo jinou strukturu v databázi
    -   ==ALTER== - mění stávající strukturu tabulky, např. přidává nebo odebírá sloupec
    -   ==DROP== - odstraňuje tabulku, index nebo jinou strukturu z databáze


Příklad:
```sql
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    price DECIMAL(10,2)
);
```
Tento příkaz vytvoří novou tabulku products s třemi sloupci id, name a price. Id bude primarnim klicem, name nebude moct byt NULL a price bude decimalni hodnota s 2 desetinnymi misty.

```sql
ALTER TABLE products
ADD stock INT;
```
Tento příkaz přidá nový sloupec stock do tabulky products.


```sql
DROP TABLE products;
```
Tento příkaz odstraní tabulku products z databáze.

-----------------------------------------------------------------------

- ==DML příkazy== slouží k manipulaci s daty v databázi. Tyto příkazy se týkají řádků v tabulkách.
    -  ==SELECT== - vybírá data z tabulky
    -   ==INSERT== - vkládá nové řádky do tabulky
    -   ==UPDATE== - mění hodnoty v řádcích tabulky
    -   ==DELETE== - odstraňuje řádky z tabulky

Příklad:
```sql
SELECT * FROM products WHERE price > 10;
```
Tento příkaz vybere všechny sloupce z tabulky products, kde je cena větší než 10.

```sql
INSERT INTO products (name, price) VALUES ('product1', 15);
```
Tento příkaz vloží nový řádek do tabulky products s hodnotami 'product1' pro sloupec name a 15 pro sloupec price.

```sql
UPDATE products SET price = 20 WHERE id = 1;
```
Tento příkaz aktualizuje hodnotu sloupce price na 20 pro řádek s id 1 v tabulce products.

```sql
DELETE FROM products WHERE name = 'product1';
```
Tento příkaz odstraní řádek z tabulky products, kde je hodnota sloupce name 'product1'.

Je důležité si uvědomit, že DDL příkazy se týkají struktury databáze a DML příkazy se týkají dat v databázi. Je důležité správně používat tyto příkazy, aby se databáze nedostala do nekonzistentního stavu.



