---
title: Integrace SQL Server s R
description: Visual Studio podporuje vytváření a spouštění dotazů SQL z R a schopnost jazyka R pracovat s uloženými procedurami.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 2b239059f445d92a5be6709ee7b7a26cb8bb7164
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144711"
---
# <a name="work-with-sql-server-and-r"></a>Práce s SQL Server a R

Vynikající podpora pro SQL Server v rámci sady Visual Studio pomáhá datovým vědcům pracovat s databázemi R a SQL prostřednictvím možnosti vytvářet a spouštět dotazy SQL a pracovat s uloženými procedurami.

> [!Note]
> Pokud chcete pracovat s SQL a R společně, musíte mít nainstalované nástroje SQL Server Data Tools:
> - Visual Studio 2017: Spusťte instalační program sady Visual Studio a vyberte úlohu ukládání a zpracování dat, která zahrnuje SQL Server datových nástrojů.
> - Visual Studio 2015: postupujte podle pokynů ke [stažení SQL Server datových nástrojů](/sql/ssdt/download-sql-server-data-tools-ssdt).

:::row:::
    :::column:::
        ![ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video")
    :::column-end:::
    :::column:::
        [Podívejte se na video (YouTube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) , kde můžete zobrazit přehled SQL Server a R (3m 03s).
    :::column-end:::
:::row-end:::

## <a name="create-and-run-sql-queries"></a>Vytváření a spouštění dotazů SQL

RTVS podporuje přidávání dotazů SQL do projektů jazyka R, což vám umožní iterativní vývoj dotazů SQL v samostatném kontextu, dokud nedosáhnete výsledků, které hledáte.

Chcete-li přidat soubor dotazu SQL, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení, vyberte možnost **Přidat**  >  **novou položku**a vyberte typ souboru **dotazu SQL** :

![Přidat položku dotazu SQL do projektu](media/sql-add-item.png)

Tento příkaz otevře soubor v editoru jazyka Transact-SQL sady Visual Studio, který poskytuje úplnou technologii IntelliSense pro SQL a možnost spouštět dotazy. Aby tyto funkce fungovaly, musíte se připojit k databázi pomocí tlačítka připojit na panelu nástrojů editoru nebo se pokusit spustit dotaz (**CTRL** + **+ SHIFT +** + **E**, který funguje i pro výběr). V obou případech se otevře dialogové okno připojení:

![Dialogové okno připojení SQL](media/sql-connection-dialog.png)

Po navázání připojení můžete spustit dotazy a zobrazit výsledky:

![Výsledky dotazu na okno SQL](media/sql-query-results.png)

Editor Transact-SQL podporuje různé funkce, jako je například zobrazení plánu spuštění dotazu a ladicího programu pro dotazy.
Další informace najdete v tématu [použití editoru jazyka Transact-SQL pro úpravy a spouštění skriptů](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>Práce s uloženými procedurami SQL Server

[SQL Server R Services](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 a novější) umožňuje vložit a spustit kód R z uložené procedury T-SQL. Můžete spustit kód R na SQL Serverovém počítači, pracovat s daty vrácenými z dotazu SQL a vygenerovat sadu výsledků dotazu SQL, kterou lze zpracovat další SQL nebo vrátit do klienta.

RTVS zjednodušuje proces kombinování kódu SQL a R v rámci jednoho příkazu jazyka SQL, který je náchylný k chybám, jak je popsáno v následujících částech:

- [Přidat připojení k databázi](#add-a-database-connection)
- [Zápis a testování uložené procedury SQL](#write-and-test-a-sql-stored-procedure)
- [Publikování uložené procedury SQL](#publish-a-sql-stored-procedure)

:::row:::
    :::column:::
        ![ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video")
    :::column-end:::
    :::column:::
        [Podívejte se na video (YouTube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) , kde můžete zobrazit přehled uložených procedur R a SQL (6 min 09s).
    :::column-end:::
:::row-end:::

### <a name="add-a-database-connection"></a>Přidat připojení k databázi

1. Vyberte **nástroje R**  >  **data**  >  **Přidat připojení k databázi** a zobrazte dialog **Vlastnosti připojení** . Tady zadáte název zdroje dat (v tomto případě SQL Server), název serveru, režim ověřování a název databáze. Před zavřením dialogového okna vyberte možnost **Test připojení** , abyste ověřili vstup.

    ![Dialogové okno připojení SQL](media/sql-connection-string-dialog.png)

1. Jakmile vyberete **OK** s platným připojením, aplikace Visual Studio vygeneruje připojovací řetězec s názvem `dbConnection` v novém *nastavení. Soubor R* . RTVS automaticky (spustí) Tento soubor, takže můžete okamžitě použít připojení ze skriptů R:

![Soubor. R nastavení SQL](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Zápis a testování uložené procedury SQL

Chcete-li přidat novou uloženou proceduru SQL, klikněte pravým tlačítkem myši na projekt, vyberte možnost **Přidat**  >  **novou položku**, v seznamu šablon vyberte **uloženou proceduru SQL** a zadejte název souboru a vyberte **OK**. Výchozí název souboru je *SqlSProc. R*; pro usnadnění čtení se ve zbývající části tohoto oddílu používá název souboru *StoredProcedure. R* . Pokud máte více uložených procedur, každý soubor musí mít jedinečný název souboru.

RTVS vytvoří pro uloženou proceduru tři soubory: *. Soubor r* pro kód r, a *. Soubor Query. SQL* pro kód SQL a *. Soubor Template. SQL* , který kombinuje dva. Druhá se zobrazí v Průzkumník řešení jako podřízené položky *. Soubor R* :

![Průzkumník řešení rozšířené zobrazení uložené procedury SQL pomocí jazyka R](media/sql-solution-explorer-expanded.png)

Rozhraní *. Soubor r* (příklad*StoredProcedure. R* ) je místo, kam píšete kód r. Výchozí obsah:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Jednoduše řečeno, kód obdrží datový rámec R s názvem `InputDataSet` a vrátí jeho výsledky v `OutputDataSet` , přičemž kód šablony zkopíruje vstup pouze do výstupu.

> [!Note]
> Názvy těchto datarámečcích jsou ovládány pomocí `@input_data_1_name` `@output_data_1_name` parametrů a v volání `sp_execute_external_script` systémové uložené procedury. Další podrobnosti o návrhu této konvence volání a některých příkladech jejich použití naleznete v tématu [sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Druhý vygenerovaný kód (v komentářích) poskytuje malý testovací skript, který používá [balíček RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) k přenosu příkazu jazyka SQL do SQL Server, spuštění a načtení jeho sady výsledků jako datový rámec R. Můžete zrušit komentář k tomuto testovacímu kódu pro interaktivní zápis kódu R proti sadě výsledků, kterou získáte z SQL Server.

Rozhraní *. Dotaz. SQL* soubor (*StoredProcedure. Query. SQL* v tomto příkladu) je místo, kam píšete a otestujete dotaz SQL, který generuje data pro `InputDataSet` . V tomto souboru *. SQL* Editor poskytuje všechny běžné funkce jazyka Transact-SQL.

Až budete s vaším kódem SQL spokojeni, Integrujte ho s vaším kódem R přetažením souboru *. SQL* do otevřeného Editoru pro *. Soubor R* . Na obrázku níže byl *StoredProcedure. Query. SQL* přetažen do bodu v *StoredProcedure. R* za čárkou v `sqlQuery(channel, )` :

![Čtení souboru SQL do řetězcové proměnné R](media/sql-reference-sql-file-from-r.png)

Jak vidíte, tento jednoduchý krok automaticky generuje kód R pro otevření souboru *. SQL* , načtení jeho obsahu do řetězce a jeho předání do balíčku RODBC k odeslání do SQL Server.

Nyní můžete interaktivně zapisovat kód R, který pracuje s datovým `InputDataSet` rámcem podle potřeby. Mějte na paměti, že v editoru můžete jednoduše vybrat kód R a poslat ho do [interaktivního okna](interactive-repl-for-r-in-visual-studio.md) stisknutím **klávesy CTRL** + **ENTER**.

Rozhraní *. Soubor Template. SQL* (*StoredProcedure. template. SQL* v tomto příkladu), nakonec obsahuje šablonu pro vygenerování uložené procedury SQL:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- `_RCODE_`Zástupný symbol je nahrazen obsahem *. Soubor R* (například *StoredProcedure. R*).
- `_INPUT_QUERY_`Zástupný symbol je nahrazen obsahem *. Soubor dotazu. SQL* (například *StoredProcedure. Query. SQL*).
- Upravte `WITH RESULT SETS` klauzuli pro popis schématu sady výsledků vrácené z uložené procedury. Konkrétně Identifikujte sloupce z datového `OutputDataSet` rámce, které chcete vrátit volajícímu uložené proceduře.

Například pro následující dotaz:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

`WITH RESULT SETS`K určení datových typů vrácených hodnot použijte následující klauzuli:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publikování uložené procedury SQL

1. Vyberte příkaz **nástroje R**  >  **data**  >  **publikování pomocí** příkazu nabídky možnosti.
1. V dialogovém okně, které se zobrazí, změňte položku **publikovat na:** na **databázi**, zadejte cíl, vyberte **publikovat**a RTVS sestavení a publikujte uloženou proceduru:

    ![Dialog publikovat uloženou proceduru](media/sql-publish-with-options.png)

1. Chcete-li publikovat všechny uložené procedury v projektu, můžete použít příkaz **R Tools**pro  >  **Data**  >  **publikování uložených procedur** pomocí nástrojů jazyka R, který je také k dispozici, když kliknete pravým tlačítkem myši na projekt v Průzkumník řešení.

> [!Tip]
> Pokud máte Průzkumník objektů systému SQL Server otevřít v aplikaci Visual Studio, vaše publikovaná uložená procedura se zobrazí ve **Programmability**  >  složce**uložené procedury** pro programovatelnost databáze. Můžete ho také spustit z Průzkumník objektů tak, že kliknete pravým tlačítkem a vyberete možnost **Spustit**nebo když ho zavoláte interaktivně z okna dotazu *. SQL* .
