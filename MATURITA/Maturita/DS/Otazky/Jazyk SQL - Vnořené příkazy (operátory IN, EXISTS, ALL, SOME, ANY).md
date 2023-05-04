Jazyk SQL - Vnořené příkazy (operátory IN, EXISTS, ALL, SOME, ANY)


- Vnořené příkazy jsou příkazy SQL, které se nacházejí uvnitř jiných příkazů. Tyto příkazy se často používají pro filtrování dat podle hodnot v jiné tabulce nebo podmínky.

- Operátory IN, EXISTS, ALL, SOME, ANY jsou klíčové operátory pro vnořené příkazy.
    -   ==IN== - vybere řádky, kde hodnota sloupce odpovídá jedné z hodnot v seznamu
    -   ==EXISTS== - vybere řádky, kde existuje alespoň jeden řádek ve vnořeném dotazu
    -   ==ALL== - vybere řádky, kde hodnota sloupce splňuje podmínku pro všechny řádky ve vnořeném dotazu
    -   ==SOME/ANY== - vybere řádky, kde hodnota sloupce splňuje podmínku pro alespoň jeden řádek ve vnořeném dotazu


Příklad:
```sql
SELECT * FROM products WHERE id IN (1, 5, 10);
```
Tento příkaz vybere řádky z tabulky products, kde hodnota sloupce id odpovídá 1, 5 nebo 10.


```sql
SELECT * FROM orders WHERE EXISTS (SELECT 1 FROM products WHERE products.id = orders.product_id);
```
Tento příkaz vybere řádky z tabulky orders, kde existuje alespoň jeden řádek ve vnořeném dotazu, kde hodnota sloupce id v tabulce products odpovídá hodnotě sloupce product_id v tabulce orders.


```sql
SELECT * FROM orders WHERE price > ALL (SELECT price FROM products);
```
Tento příkaz vybere řádky z tabulky orders, kde hodnota sloupce price je větší než hodnota sloupce price ve všech řádcích tabulky products.


```sql
SELECT * FROM orders WHERE price > ANY (SELECT price FROM products WHERE category = 'Electronics');
```
Tento příkaz vybere řádky z tabulky orders, kde hodnota sloupce price je větší než hodnota sloupce price v alespoň jednom řádku tabulky products, kde hodnota sloupce category je 'Electronics'.


- Vnořené příkazy a operátory jako IN, EXISTS, ALL, SOME, ANY jsou užitečné pro filtrování a manipulaci s daty v databázi. Je důležité dobře znát jazyk SQL a správně používat tyto operátory pro různé účely.

