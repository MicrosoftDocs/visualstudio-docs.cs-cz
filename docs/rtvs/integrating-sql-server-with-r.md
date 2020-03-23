---
title: Integrace SQL Serveru s R
description: Visual Studio podporuje vytváření a spouštění dotazů SQL z R a schopnost R pracovat s uložené procedury.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 10b5dfee629b5b6e67ab544ca0bdd905ed2a120a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72888447"
---
# <a name="work-with-sql-server-and-r"></a>Práce se servery SQL Server a R

Visual Studio vynikající podporu sql serveru pomáhá datovým vědcům pracovat s R a SQL databází prostřednictvím schopnost vytvářet a spouštět dotazy SQL a pracovat s uložené procedury.

> [!Note]
> Chcete-li společně pracovat s sql a r, musíte mít nainstalované nástroje SQL Server Data Tools:
> - Visual Studio 2017: spusťte instalační program Visual Studia a vyberte úlohu úložiště a zpracování dat, která zahrnuje nástroje SQL Server Data.
> - Visual Studio 2015: Postupujte podle pokynů ke [stažení sql server datové nástroje](/sql/ssdt/download-sql-server-data-tools-ssdt).

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Podívejte se na video") | [Podívejte se na video (youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) pro přehled SQL Server a R (3m 03s). |

## <a name="create-and-run-sql-queries"></a>Vytváření a spouštění dotazů SQL

RTVS podporuje přidávání dotazů SQL do projektů R, což umožňuje iterativně vyvíjet dotazy SQL v samostatném kontextu, dokud nezískáte výsledky, které hledáte.

Chcete-li přidat soubor dotazu SQL, klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení, vyberte **Přidat** > **novou položku**a vyberte typ souboru **dotazu SQL:**

![Přidání položky dotazu SQL do projektu](media/sql-add-item.png)

Tento příkaz otevře soubor v editoru Transact-SQL sady Visual Studio, který poskytuje úplnou aplikaci IntelliSense pro SQL a možnost spouštět dotazy. Aby tyto funkce fungovaly, musíte se připojit k databázi pomocí tlačítka připojit v panelu nástrojů editoru nebo se pokusit spustit dotaz (**Ctrl**+**Shift**+**E**, který funguje také na výběru). V obou směrech se zobrazí dialogové okno připojení:

![Dialogové okno připojení SQL](media/sql-connection-dialog.png)

Po navázání připojení můžete spouštět dotazy a zobrazit výsledky:

![Výsledky dotazu v okně SQL](media/sql-query-results.png)

Editor Transact-SQL podporuje řadu dalších funkcí, jako je například zobrazení plánu spuštění pro dotaz a ladicí program dotazu.
Další informace naleznete [v tématu Použití editoru Transact-SQL k úpravám a spouštění skriptů](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>Práce s uloženými procedurami serveru SQL Server

[Sql Server R Services](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 a novější) umožňuje vložit a spustit kód R z uložené procedury T-SQL. Můžete spustit kód R v počítači sql serveru, pracovat s daty vrácenými z dotazu SQL a generovat sadu výsledků SQL, která může být zpracována dalšísql nebo vrácena klientovi.

RTVS zjednodušuje jinak těžkopádný a náchylný k chybám proces kombinování kódu SQL a R uvnitř jednoho příkazu SQL, jak je popsáno v následujících částech:

- [Přidání připojení k databázi](#add-a-database-connection)
- [Zápis a testování uložené procedury SQL](#write-and-test-a-sql-stored-procedure)
- [Publikování uložené procedury SQL](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Podívejte se na video") | [Podívejte se na video (youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) přehled r a SQL uložené procedury (6m 09s). |

### <a name="add-a-database-connection"></a>Přidání připojení k databázi

1. Vyberte **Nástroje R** > **Datové** > **připojení k datům,** chcete-li vyvolat dialogové okno **Vlastnosti připojení.** Zde zadáte název zdroje dat (v tomto případě SQL Server), název serveru, režim ověřování a název databáze. Před zavřením dialogového okna vyberte **Testovat připojení,** chcete-li ověřit vstup.

    ![Dialogové okno připojení SQL](media/sql-connection-string-dialog.png)

1. Jakmile vyberete **OK** s platným připojením, Visual `dbConnection` Studio vygeneruje připojovací řetězec pojmenovaný v novém *nastavení. R* soubor. RTVS automaticky zdroje (spustí) tento soubor, takže můžete okamžitě použít připojení ze skriptů R:

![Soubor SQL Settings.R](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Zápis a testování uložené procedury SQL

Chcete-li přidat novou proceduru uloženou v SQL, klepněte pravým tlačítkem myši na projekt, vyberte **položku Přidat** > **novou položku**, vyberte příkaz **SQL Stored Procedure with R** ze seznamu šablon, pojmenujte soubor a vyberte **OK**. Výchozí název souboru je *SQLSProc.R*; pro snadné čtení, název souboru *StoredProcedure.R* se používá ve zbývající části této části. Pokud máte více uložených procedur, musí mít každý soubor jedinečný název souboru.

RTVS vytvoří tři soubory pro uloženou proceduru: *. R* pro váš R kód, *a . Soubor Query.sql* pro kód SQL a *soubor . Template.sql* soubor, který kombinuje dva. Tyto poslední dva se zobrazí v Průzkumníku řešení jako *podřízené . Soubor R:*

![Rozšířené zobrazení rozšířeného zobrazení uložené procedury SQL pomocí jazyka R](media/sql-solution-explorer-expanded.png)

V *. R* soubor *(StoredProcedure.R* v tomto příkladu) je místo, kde píšete kód R. Výchozí obsah je:

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

Jednoduše řečeno, kód obdrží r datový `InputDataSet` snímek s `OutputDataSet`názvem a vrátí jeho výsledky v , s kódem šablony pouze kopírování vstupu do výstupu.

> [!Note]
> Názvy těchto datových rámců `@input_data_1_name` `@output_data_1_name` jsou řízeny parametry `sp_execute_external_script` a ve volání uložené procedury systému. Další podrobnosti o návrhu této konvence volání a některé příklady jeho použití naleznete [v tématu sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Druhý generovaný kód (v komentářích) poskytuje malý testovací skript, který používá [balíček RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) k přenosu příkazu SQL na SQL Server, spuštění a načtení jeho sady výsledků jako datového rámce R. Tento testovací kód můžete odkomentovat a interaktivně napsat kód R proti sadě výsledků, kterou získáte ze serveru SQL Server.

V *. Query.sql* file *(StoredProcedure.Query.sql* in this example) je místo, kde píšete `InputDataSet`a testujete dotaz SQL, který generuje data pro . Pomocí tohoto souboru *.sql* vám editor poskytuje všechny obvyklé funkce Transact-SQL.

Jakmile budete spokojeni s kódem SQL, integrujte jej s kódem R přetažením souboru *.sql* do otevřeného editoru pro *. R* soubor. Na obrázku níže *storedprocedure.query.sql* byl přetažen do bodu v *StoredProcedure.R* po čárku v `sqlQuery(channel, )`:

![Čtení souboru SQL do proměnné řetězce R](media/sql-reference-sql-file-from-r.png)

Jak můžete vidět, tento jednoduchý krok automaticky generuje kód R pro otevření souboru *.sql,* čtení jeho obsahu do řetězce a jeho předání balíčku RODBC k jeho odeslání na SQL Server.

Nyní můžete interaktivně psát R kód, který manipuluje s datovým rámcem `InputDataSet` podle potřeby. Nezapomeňte, že stačí vybrat R kód v editoru a odeslat jej do [interaktivního okna](interactive-repl-for-r-in-visual-studio.md) stisknutím **Ctrl**+**Enter**.

V *. Template.sql* file *(StoredProcedure.Template.sql* in this example) finally obsahuje šablonu pro generování uložené procedury SQL:

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

- Zástupný `_RCODE_` symbol se nahrazuje obsahem *. R* (například *StoredProcedure.R*).
- Zástupný `_INPUT_QUERY_` symbol se nahrazuje obsahem *. Soubor Query.sql* (například *StoredProcedure.Query.sql).*
- Upravte `WITH RESULT SETS` klauzuli popisující schéma sady výsledků vrácené z uložené procedury. Konkrétně identifikovat sloupce `OutputDataSet` z datového rámce, který chcete vrátit volajícímu uložené procedury.

Například pro následující dotaz:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Následující `WITH RESULT SETS` klauzuli byste použili k určení datových typů vrácených hodnot:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publikování uložené procedury SQL

1. Vyberte příkaz nabídky Publikovat**data** >  **nástrojů** > R**s možnostmi.**
1. V zobrazeném dialogovém okně **změňte možnost Publikovat na:** do **databáze**, zadejte cíl, vyberte **Publikovat**a RTVS vytvoří a publikuje uloženou proceduru:

    ![Dialogové okno Publikovat uloženou proceduru](media/sql-publish-with-options.png)

1. Chcete-li publikovat všechny uložené procedury v projektu, můžete použít příkaz **Nástroje R** > **Publikovat** > **uložené procedury,** který je k dispozici také po klepnutí pravým tlačítkem myši na projekt v Průzkumníku řešení.

> [!Tip]
> Pokud máte v sadě Visual Studio otevřenou aplikaci SQL Server Object Explorer, zobrazí se publikovaná uložená procedura ve složce **Programovatelnost** > **uložené procedury** v databázi. Můžete jej také spustit z Průzkumníka objektů klepnutím pravým tlačítkem myši a výběrem **příkazu Spustit proceduru**nebo jeho interaktivním voláním z okna dotazu *.sql.*
