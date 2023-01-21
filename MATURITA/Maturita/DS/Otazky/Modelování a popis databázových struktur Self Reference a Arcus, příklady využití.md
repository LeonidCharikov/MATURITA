Modelování a popis databázových struktur Self Reference a Arcus, příklady využití

- Modelování databázových struktur je proces, který se týká návrhu a plánování databázových tabulek a relací mezi nimi. Existuje několik různých metod modelování databázových struktur, jako je například Entitně-vztahové (ER) modelování nebo relační modelování.

- ==Self Reference je metoda==, kdy se tabulka odkazuje sama na sebe. Toto se často používá pro reprezentaci hierarchií nebo grafů.


Příklad:
```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(255),
  manager_id INT,
  FOREIGN KEY (manager_id) REFERENCES employees(id)
);
```
Tento příkaz vytvoří tabulku employees s primárním klíčem id, sloupcem name a sloupcem manager_id, který odkazuje na primární klíč tabulky employees.

-----------------------------------------------------------------------

- ==Arcus je metoda modelování==, kdy se pro reprezentaci mnoha k mnoha vztahů vytvoří nová tabulka, která obsahuje sloupce pro klíče z obou propojovaných tabulek.


Příklad:
```sql
CREATE TABLE products (
  id INT PRIMARY KEY,
  name VARCHAR(255)
);

CREATE TABLE orders (
  id INT PRIMARY KEY,
  customer_id INT,
  order_date DATE
);

CREATE TABLE product_orders (
  product_id INT,
  order_id INT,
  PRIMARY KEY (product_id, order_id),
  FOREIGN KEY (product_id) REFERENCES products(id),
  FOREIGN KEY (order_id) REFERENCES orders(id)
);
```
Tento příkaz vytvoří tabulky products, orders a product_orders. Tabulka product_orders slouží jako Arcus tabulka, která propojuje tabulky products a orders pomocí sloupců product_id a order_id, kde product_id odkazuje na products.id a order_id odkazuje na orders.id.


- ==Self reference a Arcus metoda== jsou dvě z možností, jak modelovat databázové struktury. Je důležité zvolit správnou metodu pro konkrétní potřeby a správně implementovat relace mezi tabulkami, aby byly data správně organizována a snadno přístupná.