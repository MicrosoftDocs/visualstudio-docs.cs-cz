---
title: Integrace systému SQL Server s R
description: Visual Studio podporuje vytváření a spouštění dotazů SQL z R a možnost R pro práci s uložené procedury.
ms.date: 06/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 3b9fa1f675754257a2278c7282c45d9816c034cd
ms.sourcegitcommit: 4e605891d0dfb3ab83150c17c074bb98dba29d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36946910"
---
# <a name="work-with-sql-server-and-r"></a>Práce s systému SQL Server a R

Visual Studio vynikající podpora pro SQL Server pomáhá data, která vědců pracovat s R a SQL databáze pomocí umožňuje vytvářet a spouštět dotazy SQL a práci s uloženými procedurami.

> [!Note]
> Spolupracovat s SQL a R, musíte mít nainstalovaný SQL Server Data Tools:
> - Visual Studio 2017: Spusťte instalační program sady Visual Studio a vyberte úložiště dat a zpracování úloh, který obsahuje nástroje, dat systému SQL Server.
> - Visual Studio 2015: podle pokynů na [stáhnout SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (webu youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) přehled systému SQL Server a R (3 m 03s). |

## <a name="create-and-run-sql-queries"></a>Vytvářet a spouštět dotazy SQL

RTVS podporuje přidání dotazy SQL do projektů R, umožňuje interaktivně vyvíjet dotazů SQL v samostatných kontextu, dokud nezískáte výsledků, které hledáte.

Chcete-li přidat soubor dotaz SQL, klikněte pravým tlačítkem na projekt v Průzkumníku řešení, vyberte **přidat** > **nová položka**a vyberte **dotazu SQL** typ souboru:

![Přidání dotazu SQL položku do projektu](media/sql-add-item.png)

Tento příkaz otevře v editoru jazyka Transact-SQL Visual Studio, které poskytuje úplný IntelliSense pro SQL a umožňuje spouštět dotazy. Pro tyto funkce pro práci, budete muset připojit k databázi pomocí tlačítka připojit v okně editor panelu nástrojů nebo pokus o spuštění dotazu (**Ctrl**+**Shift**+**E** , který funguje taky na výběr). V obou případech se vyvolá dialogové okno připojení:

![Dialogové okno připojení SQL](media/sql-connection-dialog.png)

Po navázání připojení můžete spouštět dotazy a zobrazte výsledky:

![Výsledky dotazu SQL – okno](media/sql-query-results.png)

Editor Transact-SQL podporuje celou řadu dalších funkcí, například zobrazení plán spuštění dotazu a ladicí program dotazu.
Další informace najdete v tématu [pomocí jazyka Transact-SQL editoru upravit a spustit skripty](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>Práce s uložené procedury SQL serveru

[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 a novější) umožňuje vložit a spustit kód R z T-SQL uložené procedury. Můžete spustit na počítači systému SQL Server kód R, fungovat na data vrácená z dotazu SQL a generovat je sada výsledků dotazu SQL, která se dá zpracovat další SQL nebo vrácen do klienta.

RTVS zjednodušuje proces jinak nepraktické a náchylné kombinace kódu SQL a R uvnitř jednoho příkazu SQL, jak je popsáno v následujících částech:

- [Přidat připojení k databázi](#add-a-database-connection)
- [Psaní a testování uloženou proceduru SQL](#write-and-test-a-sql-stored-procedure)
- [Publikování uloženou proceduru SQL](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (webu youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) pro přehled R a SQL uložené procedury (6 m 09s). |

### <a name="add-a-database-connection"></a>Přidat připojení k databázi

1. Vyberte **R nástroje** > **Data** > **přidat připojení k databázi** se zprovoznit **vlastnosti připojení** Dialogové okno. Sem zadejte název zdroje dat (SQL Server v tomto případě), název serveru, režim ověřování a název databáze. Vyberte **Test připojení** ověřit váš vstup předtím, než uzavření dialogového okna.

    ![Dialogové okno připojení SQL](media/sql-connection-string-dialog.png)

1. Jakmile vyberete **OK** se platné připojení, Visual Studio generuje připojovací řetězec s názvem `dbConnection` v nové *nastavení. R* souboru. RTVS automaticky zdroje (spuštěno) tento soubor, abyste mohli okamžitě používat připojení z skripty R:

![Soubor SQL Settings.R](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Psaní a testování uloženou proceduru SQL

Chcete-li přidat novou uloženou proceduru SQL, klikněte pravým tlačítkem na projekt, vyberte možnost **přidat** > **nová položka**, vyberte **uloženou proceduru SQL s R** ze seznamu šablon Zadejte název souboru a vyberte **OK**. Výchozí název souboru je *SqlSProc.R*; pro snadnější čtení, název souboru *StoredProcedure.R* se používá ve zbývající části této části. Pokud máte více uložené procedury, každý soubor musí mít jedinečný název souboru.

RTVS vytvoří tři soubory pro uložené procedury: *. R* soubor pro váš kód R *. Query.SQL* v souboru kódu SQL a *. Template.SQL* soubor, který kombinuje dva. Jejich pozdější dva zobrazí v Průzkumníku řešení jako podřízené objekty *. R* souboru:

![Průzkumník řešení rozšířit zobrazení SQL uloženou proceduru s R](media/sql-solution-explorer-expanded.png)

*. R* souboru (*StoredProcedure.R* v tomto příkladu) je, kde můžete napsat kód R. Výchozí obsah jsou:

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

Jednoduše řečeno, obdrží kód R dataframe názvem `InputDataSet` a vrátí své výsledky v `OutputDataSet`, kódem šablony pouze zkopírujete vstup výstupu.

> [!Note]
> Názvy těchto dataframes jsou řízeny `@input_data_1_name` a `@output_data_1_name` parametry ve volání `sp_execute_external_script` systémové uložené procedury. Další informace o návrhu Tato konvence volání a několik příkladů jeho použití naleznete v tématu [uloženou proceduru sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Další generovaný kód (v komentářích) poskytuje testu malých skript, který se používá [RODBC balíček](https://cran.r-project.org/web/packages/RODBC/index.html) k přenosu příkazu jazyka SQL do systému SQL Server, spusťte ji a načíst její sadu výsledků jako R dataframe. Můžete Odkomentujte, že tento kód testovací interaktivně zapsat svůj kód R s výsledek nastaven, můžete získat z SQL serveru.

*. Query.SQL* souboru (*StoredProcedure.Query.sql* v tomto příkladu) určuje, kde zapsat a otestovat dotaz SQL, který generuje data pro `InputDataSet`. Pomocí této *.sql* souboru editoru poskytuje všechny potřebné obvyklé Transact-SQL pro vás.

Jakmile budete spokojeni s kódu SQL, integrovat do vašeho kódu jazyka R přetažením *.sql* soubor do otevřete editor pro *. R* souboru. Na obrázku níže *StoredProcedure.Query.sql* má byla přetáhnout do bodu v *StoredProcedure.R* za desetinnou čárkou v `sqlQuery(channel, )`:

![Čtení souboru SQL do proměnné řetězec R](media/sql-reference-sql-file-from-r.png)

Jak můžete vidět, tento krok jednoduché automaticky generuje kód R otevřete *.sql* souboru, přečtěte si jeho obsah do řetězce a předejte ji do RODBC balíček, který chcete odeslat do systému SQL Server.

Teď můžete interaktivně zápisu R kód, který zpracovává `InputDataSet` dataframe podle potřeby. Nezapomeňte, že můžete právě vyberte v editoru kódu jazyka R a odeslat ho do [interaktivních okna](interactive-repl-for-r-in-visual-studio.md) stisknutím **Ctrl**+**Enter**.

*. Template.SQL* souboru (*StoredProcedure.Template.sql* v tomto příkladu), nakonec obsahuje šablony pro generování SQL uloženou proceduru:

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

- `_RCODE_` Zástupný symbol je nahrazena obsah *. R* souboru (například *StoredProcedure.R*).
- `_INPUT_QUERY_` Zástupný symbol je nahrazena obsah *. Query.SQL* souboru (například *StoredProcedure.Query.sql*).
- Upravit `WITH RESULT SETS` klauzule k popisu schéma sada výsledků vrácená z uložené procedury. Konkrétně identifikovat sloupců z `OutputDataSet` dataframe, který chcete vrátit do volající uložené procedury.

Například následující dotaz:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Byste použili následující `WITH RESULT SETS` klauzule určit typy dat vrácené hodnoty:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publikování uloženou proceduru SQL

1. Vyberte **R nástroje** > **Data** > **s možností publikování** příkazu nabídky.
1. V dialogovém okně se zobrazí, změnit **publikování pro:** k **databáze**, zadejte cíl, vyberte **publikovat**, a RTVS sestavení a publikuje uložené procedury:

    ![Uložená procedura dialogového okna publikování](media/sql-publish-with-options.png)

1. Chcete-li publikovat všechny uložené procedury v projektu, můžete použít **R nástroje** > **Data** > **publikování uložené procedury** příkaz, který je také Tato možnost je k dispozici, když kliknete pravým tlačítkem na projekt v Průzkumníku řešení.

> [!Tip]
> Pokud máte v sadě Visual Studio otevřete Průzkumník objektů SQL serveru, se zobrazí vaše publikované uložené procedury v **programovatelnosti** > **uložené procedury** složku databáze. Můžete také jej spustíte v Průzkumníku objektů tak, že kliknete pravým tlačítkem a vyberete **provést proceduru**, nebo voláním interaktivně z *.sql* okno dotazu.
