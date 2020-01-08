---
title: Přidání zdroje dat do testu výkonnosti webu
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c7f947be01500b0d45b81d404206722ac71084a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565406"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Přidání zdroje dat do testu výkonnosti webu

Vytvoření vazby dat, poskytující různé hodnoty pro stejný test, například, poskytují různé hodnoty do formuláře Parametry post.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Vazba dat do testu výkonnosti webu](../test/media/web_test_databinding_conceptual.png)

Chceme použít ukázkovou aplikaci ASP.NET. Má tři *.aspx* stránky – výchozí stránku, červenou stránku a modrou stránku. Výchozí stránka obsahuje na přepínač pro výběr červeného nebo modrého tlačítka a tlačítka Odeslat. Další dvě *.aspx* stránky jsou velmi jednoduché. Jeden má popisek s názvem červený a druhý má popisek s názvem modrý. Pokud zvolíte odeslání na výchozí stránce, zobrazíme jednu z ostatních stránek. Můžete stáhnout [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) ukázkový nebo stačí postupovat podle vlastní webové aplikace.

![Spuštění webové aplikace, které má být testována](../test/media/web_test_databinding_runwebapp.png)

Řešení by měl také obsahovat testu výkonnosti webu, který prochází stránkami webové aplikace.

![Řešení s testu výkonnosti webu](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Vytvoření databáze SQL

::: moniker range="vs-2017"

1. Pokud nemáte Visual Studio Enterprise, můžete ho stáhnout [stahování sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránky.

2. Vytvoření databáze SQL.

     ![Přidat novou databázi SQL.](../test/media/web_test_databinding_sql_addnewdb.png)

3. Vytvořte projekt databáze.

     ![Vytvoření nového projektu z databáze](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Přidání tabulky do databázového projektu.

     ![Přidá novou tabulku na databázový projekt](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Přidejte pole do tabulky.

     ![Přidejte pole do tabulky](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikujte projekt databáze.

     ![Publikujte projekt databáze z Průzkumníka řešení](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Přidání dat do pole.

     ![Přidání dat do pole](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Pokud nemáte Visual Studio Enterprise, můžete ho stáhnout [stahování sady Visual Studio](https://visualstudio.microsoft.com/downloads) stránky.

2. Vytvoření databáze SQL.

     ![Přidat novou databázi SQL.](../test/media/web_test_databinding_sql_addnewdb.png)

3. Vytvořte projekt databáze.

     ![Vytvoření nového projektu z databáze](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Přidání tabulky do databázového projektu.

     ![Přidá novou tabulku na databázový projekt](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Přidejte pole do tabulky.

     ![Přidejte pole do tabulky](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikujte projekt databáze.

     ![Publikujte projekt databáze z Průzkumníka řešení](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Přidání dat do pole.

     ![Přidání dat do pole](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Přidat zdroj dat

1. Přidáte zdroj dat.

     ![Přidání zdroje dat do testu výkonnosti webu](../test/media/web_test_databinding_sql_adddatasource.png)

2. Zvolte typ zdroje dat a pojmenujte ho.

     ![Název zdroje databáze](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Umožňuje vytvořte připojení.

     ![Tlačítko nové připojení](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Zadejte podrobnosti připojení.

     ![Zadejte vlastnosti připojení databáze SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Vyberte tabulku, kterou chcete použít pro test.

     ![Přidat tabulku barvy jako zdroj dat](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tabulka je vázána na test.

     ![Přidat uzel zdrojů dat do testu výkonnosti webu](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Uložte tento test.

## <a name="bind-the-data"></a>Svázat data

1. Vytvoření vazby **ColorName** pole.

     ![Svázat pole ColorName RadioButtonList1 hodnotu](../test/media/web_test_databinding_sql_binddatasource.png)

2. Otevřít *Local.testsettings* ve **Průzkumníka řešení** a vyberte **jedno spuštění na řádek zdroje dat** možnost.

     ![Upravit soubor nastavení testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Uložte test výkonnosti webu.

## <a name="run-the-test-with-the-data"></a>Spustit test s daty

1. Spusťte test.

     ![Spuštění testu výkonnosti webu Ověření vazby](../test/media/web_test_databinding_sql_runtest.png)

     Pro každý řádek dat se zobrazují dva běhy. Běh 1 odešle požadavek na stránku *Red.aspx*, a běh 2 odešle požadavek na stránku *Blue.aspx*.

     ![Výsledky testovacího běhu](../test/media/web_test_databinding_sql_runresults.png)

     Když se navážete na zdroj dat, můžete porušit výchozí pravidlo odpovídání URL. V takovém případě je chyba při spuštění 2 způsobena pravidlem, které se očekává, že *Red.aspx* stránky z původního záznamu testu, ale datové vazby nyní směruje na *Blue.aspx* stránky.

2. Opravte chybu ověření odstraněním **adresa URL odpovědi** ověřovací pravidla a znovu spusťte test.

     ![Odstranit ověřovacího pravidla odpověď URL](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Test výkonnosti webu nyní předává pomocí datové vazby.

     ![Test byl úspěšný, použití datových vazeb](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Dotazy a odpovědi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Dotaz: které databáze mohu použít jako zdroj dat?

**Odpověď:** můžete použít následující:

- Microsoft SQL Azure.

- Všechny verze systému Microsoft SQL Server 2005 nebo novější.

- Soubor databáze Microsoft SQL Server (včetně SQL Express).

- Ovladač Microsoft ODBC.

- Soubor aplikace Microsoft Access pomocí zprostředkovatele rozhraní .NET Framework pro OLE DB.

- Oracle 7.3, 8i, 9i nebo 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Otázka: jak použít textový soubor čárkou hodnot s oddělovači (CSV) jako zdroj dat?

**Odpověď:** tady je způsob:

1. Vytvořte složku k uspořádání vašich artefaktů databáze projektů a přidejte položku.

     ![Přidat novou položku do složky dat](../test/media/web_test_databinding_foldernewitem.png)

2. Vytvořte textový soubor.

     ![Pojmenujte nový textový soubor ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Upravte textový soubor a přidejte následující:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Postupujte podle kroků v [přidat zdroj dat](#add-the-data-source), ale zvolte soubor CSV jako zdroj dat.

     ![Zadejte název a zvolte soubor CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Otázka: Co když Můj existující soubor CSV neobsahuje záhlaví sloupců?

**Odpověď:** Pokud nemůžete přidat záhlaví sloupců, můžete použít souboru popisu schématu a pokud chcete se souborem CSV zacházet jako s databází.

1. Přidat nový textový soubor s názvem *schema.ini*.

     ![Přidat soubor schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Upravit *schema.ini* soubor a přidejte informace, které popisují strukturu vašich dat. Například soubor schématu popisující soubor CSV může vypadat takto:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Přidáte zdroj dat do testu.

     ![Přidání zdroje dat do testu výkonnosti webu](../test/media/web_test_databinding_sql_adddatasource.png)

4. Pokud používáte *schema.ini* souboru, zvolte **databáze** (nikoli soubor CSV) jako zdroj dat a pojmenujte ho.

     ![Přidání databázového zdroje dat](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Vytvořte nové připojení.

     ![Tlačítko nové připojení](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Vyberte zprostředkovatele dat .NET Framework pro OLE DB.

     ![Vyberte zprostředkovatele dat OLE DB .NET framework](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Zvolte **Advanced**.

     ![Zvolte pokročilé](../test/media/web_test_databinding_advanced.png)

8. Pro vlastnosti zprostředkovatele vyberte Microsoft.Jet.OLEDB.4.0 a poté nastavte **rozšířené vlastnosti** k textu. HDR = NO.

     ![Použití rozšířených vlastností](../test/media/web_test_databinding_advancedproperties.png)

9. Zadejte název složky, která obsahuje soubor schématu a vyzkoušejte připojení.

     ![Zadejte cestu ke složce data](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Vyberte soubor CSV, který chcete použít.

     ![Vyberte textový soubor](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Po dokončení se zobrazí soubor CSV jako tabulku.

     ![Zdroj dat, které jsou přidány do testu](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Otázka: jak použít soubor XML jako zdroj dat?

**Odpověď:** Ano.

1. Vytvořte složku k uspořádání vašich artefaktů databáze projektů a přidejte položku.

     ![Přidat novou položku do složky dat](../test/media/web_test_databinding_foldernewitem.png)

2. Vytvořte soubor XML.

     ![Přidání souboru ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Upravte soubor XML a přidejte svá data:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Postupujte podle kroků v [přidat zdroj dat](#add-the-data-source), ale zvolte soubor XML jako zdroj dat.

     ![Zadejte název a vyberte soubor XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Dotaz: lze přidat datovou vazbu pro požadavek webové služby využívající SOAP?

**Odpověď:** Ano, je třeba změnit protokol SOAP XML ručně.

1. Ve stromové struktuře požadavku a v okně Vlastnosti vyberte požadavek webové služby, zvolte tři tečky (...) ve vlastnosti tělo řetězce.

     ![Upravit tělo řetězce webové služby](../test/media/web_test_databinding_webservicerequest.png)

2. Nahraďte hodnoty v těle SOAP hodnotami vázaných na data pomocí následující syntaxe:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Pokud například máte následující kód:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Můžete ho změnit na toto:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Uložte tento test.
