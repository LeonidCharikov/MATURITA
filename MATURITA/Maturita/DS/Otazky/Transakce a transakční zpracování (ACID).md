Transakce a transakční zpracování (ACID)

- SQL transakce jsou jednou nebo více SQL příkazů, které se provádějí jako celek. Buď se všechny příkazy úspěšně provedou, nebo se žádný neprovede. Tím se zajišťuje, že databáze zůstane v konzistentním stavu, i když se vyskytnou chyby nebo selhání.

-----------------------------------------------------------------------

- ==Transakční zpracování (ACID)== je sadou vlastností, které zajišťují, že transakce jsou prováděny správně a že databáze zůstane v konzistentním stavu. Tyto vlastnosti jsou:

-----------------------------------------------------------------------

-   Atomicita (Atomicity) - Buď se všechny příkazy transakce provedou, nebo se žádný neprovede.
    -   ==Izolace (Isolation)== - Transakce jsou izolovány od ostatních transakcí, takže se jedna transakce nemůže dotýkat dat, která jsou zpracovávána jinou transakcí.
    -   ==Trvání (Durability)== - Po provedení transakce jsou změny trvale uloženy v databázi.
    -   ==Konzistence (Consistency)== - Transakce zajišťují, že databáze zůstává v konzistentním stavu.

Příklad:
```sql
BEGIN TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```
- V tomto příkladu se provádí transakce, která převádí 100 jednotek z účtu 1 na účet 2. Příkazy se provádějí jako celek. Pokud by se vyskytla chyba při provedení druhého příkazu, např. že účet 2 neexistuje, pak by se ani první příkaz neprovedl, takže by se databáze nezměnila a zůstala by v konzistentním stavu.

- Dalsim prikladem by mohlo byt zruseni objednavky, kde by se transakce zahajovala vlozenim nove objednavky do databaze a dokoncovala by se zrusenim objednavky. Pokud by se vyskytla chyba napr. vlozeni objednavky, transakce by se zrusila pomoci ==ROLLBACK== a databaze by zustala v puvodnim stavu, bez nove vlozene objednavky.

-----------------------------------------------------------------------
- Transakce se spravidla zahajuji pomoci ==BEGIN TRANSACTION==, ktery oznacuje zacatek transakce. Provedene prikazy se potvrdi pomoci ==COMMIT==, ktery ulozi provedene zmeny do databaze. Pokud se vyskytne chyba nebo se nechce transakce ulozit, muzeme ji zrusit pomocí příkazu ==ROLLBACK==. Tento příkaz zruší všechny změny provedené v rámci transakce a vrátí databázi do stavu před zahájením transakce.

-----------------------------------------------------------------------
- V praxi se transakce často používají například při platbách nebo převodech peněz mezi účty, kdy je nutné zajistit, aby se peníze neztratily ani nezduplikovaly. Díky transakcím se zajistí, že se peníze odečtou z jednoho účtu a připíšou na druhý účet současně, a že se databáze nezmění, pokud by se vyskytla chyba.