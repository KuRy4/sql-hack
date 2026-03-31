# Penetrační test – SQL Injection

**Autor:** KuRy4  
**Datum:** 31. 3. 2026

## Průzkum
Vložením `'` do vyhledávacího pole se objevila SQL chyba „1st ORDER BY term out of range - should be between 1 and 2“.  
Tím byla potvrzena zranitelnost proti SQL Injection.

## Zjištění struktury
Pomocí `ORDER BY` jsem zjistil, že dotaz má **2 sloupce**.  
Pomocí payloadu `' UNION SELECT 1, name FROM sqlite_master WHERE type='table' --` jsem našel tabulku `config`.

## Exfiltrace dat
Finálním payloadem jsem vypsal obsah tabulky `config` a získal vlajku.

**Finální payload:**

**Získaná vlajka:** `FLAG{Sql_Un1on_M4st3r_S0SE}`

## Screenshot
![Vlajka v aplikaci]<img width="1920" height="1036" alt="Screenshot_20260331_102239" src="https://github.com/user-attachments/assets/e9ef139c-414b-42c6-946d-63756692aedc" />
