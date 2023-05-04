Jazyk SQL - DCL, TCL příkazy

- ==DCL (Data Control Language)== příkazy slouží k řízení přístupu k datům a uživatelům v databázi. Tyto příkazy se týkají práv uživatelů a rolí.
    -   ==GRANT== - uděluje práva uživatelům nebo rolím
    -   ==REVOKE== - odebírá práva uživatelům nebo rolím

Příklad:
```sql
GRANT SELECT ON products TO user1;
```
Tento příkaz uděluje uživateli user1 právo SELECT na tabulce products.

```sql
REVOKE SELECT ON products FROM user1;
```
Tento příkaz odebírá uživateli user1 právo SELECT na tabulce products.

-----------------------------------------------------------------------

- ==TCL (Transaction Control Language)== příkazy slouží k řízení transakcí v databázi. Tyto příkazy se týkají transakčního zpracování.
    -   ==BEGIN TRANSACTION== - zahajuje novou transakci
    -   ==COMMIT== - potvrzuje provedené změny v transakci
    -  ==ROLLBACK== - zruší změny provedené v transakci
    -   ==SAVEPOINT== - umožňuje definovat bod, do kterého lze vrátit transakci pomocí ROLLBACK

Příklad:
```sql
BEGIN TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```
V tomto příkladu se provádí transakce, která převádí 100 jednotek z účtu 1 na účet 2. Příkazy se provádějí jako celek a provedené změny se potvrdí pomocí příkazu COMMIT.


```sql
SAVEPOINT savepoint1;
UPDATE products SET stock = stock - 5 WHERE id = 1;
ROLLBACK TO savepoint1;
```
V tomto příkladu se nejprve definuje bod savepoint1, potom se provede update kde se snizi hodnota stock o 5. Pokud by se chtelo zrusit jen tento update, tak se provede ROLLBACK TO savepoint1.

- Je důležité si uvědomit, že DCL příkazy se týkají přístupu k datům a TCL příkazy se týkají transakčního zpracování. Je důležité správně používat tyto příkazy, aby se databáze nedostala do nekonzistentního stavu nebo aby nebyly uděleny nebo odebrány práva nebo transakce nebyly správně ukončené. Při práci s databází je důležité mít dobrou znalost jazyka SQL a správně používat jednotlivé příkazy pro různé účely.