Indexy a indexace dat v databázi (UNIQUE, INDEX)

- Indexy v SQL jsou struktury, které se používají k urychlení vyhledávání a filtrování dat v databázi. Jsou to jakési mapy, které obsahují hodnoty sloupců a odkazy na řádky v tabulce, kde se tato hodnota vyskytuje. Díky indexům se může databáze rychleji orientovat v obsahu tabulky a tím zrychlit vyhledávání.

- Existují dva typy indexů:
    -   ==UNIQUE== indexy se používají k ověření, že hodnota v sloupci je unikátní a není v tabulce vícekrát.
    -   ==INDEX== indexy se používají k urychlení vyhledávání a řazení dat v tabulce.


Example:
```sql
CREATE UNIQUE INDEX email_index ON users (email);
```
Tento příkaz vytvoří UNIQUE index na sloupec email v tabulce users. Díky tomuto indexu se ověří, že v tabulce nejsou dva řádky se stejnou hodnotou v emailu.


```sql
CREATE INDEX name_index ON products (name);
```
Tento příkaz vytvoří INDEX na sloupec name v tabulce products. Díky tomuto indexu se urychlí vyhledávání a řazení produktů podle jména.


Indexy se mohou vytvaret i viacenasobne a na vice sloupcu napr.
```sql
CREATE INDEX name_and_price_index ON products (name,price);
```
Tento příkaz vytvoří INDEX na sloupce name a price v tabulce products. Díky tomuto indexu se urychlí vyhledávání a řazení produktů podle jména a ceny.


- Je důležité mít na paměti, že indexy zvyšují rychlost vyhledávání dat, ale zároveň zpomalují vkládání, updaty a mazání dat. Je tedy nutné rozumně rozhodnout, které sloupce indexovat a které ne.