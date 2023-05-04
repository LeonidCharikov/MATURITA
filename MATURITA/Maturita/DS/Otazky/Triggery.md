Tigger

- Triggery jsou speciální typy SQL příkazů, které se automaticky spouštějí v případě, že dojde k určité události v databázi. Tyto události mohou být například změna údajů v tabulce nebo vložení nového řádku. Triggery se často používají k automatizaci úkonů, jako je kontrola integrity dat nebo aktualizace souvisejících tabulek.

----------------------------------------------------------------------

- Triggery se dělí na dva typy podle toho, kdy se mají spustit: před událostí (BEFORE) nebo po události (AFTER).
    -   ==BEFORE== triggery se spouštějí před tím, než dojde k události, např. před vložením nového řádku do tabulky. Tyto triggery se často používají k ověřování integrity dat nebo k úpravě hodnot, které se mají vložit do tabulky.
    -   ==AFTER== triggery se spouštějí po tom, co dojde k události, např. po updatu nebo smazání řádku z tabulky. Tyto triggery se často používají k aktualizaci souvisejících tabulek nebo k logování změn v databázi.

-----------------------------------------------------------------------

- SQL triggery se také dělí podle typu události, pro kterou jsou určeny.
    -   ==INSERT== triggery se spouštějí při vložení nového řádku do tabulky.
    -   ==UPDATE== triggery se spouštějí při změně hodnot v řádku tabulky.
    -   ==DELETE== triggery se spouštějí při smazání řádku z tabulky.


Příklady
```sql
CREATE TRIGGER update_product_price
AFTER UPDATE ON products
FOR EACH ROW
BEGIN
    UPDATE order_items
    SET price = NEW.price
    WHERE product_id = NEW.id;
END;
```
- Tento trigger se spustí po update na tabulce products a updatuje cenu v tabulce order_items, kde se shoduje product_id s novou hodnotou v tabulce products.


```sql
CREATE TRIGGER check_employee_salary
BEFORE INSERT ON employees 
FOR EACH ROW 
BEGIN
IF NEW.salary < 1000 
THEN SET NEW.salary = 1000; 
END IF; 
END;
```
- Tento trigger se spustí pred vlozenim noveho zaznamu do tabulky employees a zkontroluje hodnotu salary, pokud je mensi nez 1000, nastavi se na 1000.

