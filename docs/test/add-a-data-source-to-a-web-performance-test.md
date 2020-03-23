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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565406"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Přidání zdroje dat do testu výkonnosti webu

Vazby data poskytnout různé hodnoty na stejné test, například poskytnout různé hodnoty parametry příspěvku formuláře.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Vazba dat na test výkonu webu](../test/media/web_test_databinding_conceptual.png)

Použijeme ukázkovou aplikaci ASP.NET. Má tři *stránky .aspx* – výchozí stránku, červenou stránku a modrou stránku. Výchozí stránka má rádiový ovládací prvek pro výběr červené nebo modré a tlačítko odeslat. Další dvě *stránky .aspx* jsou velmi jednoduché. Jeden má štítek s názvem Red a druhý má štítek s názvem Modrá. Když zvolíte odeslat na výchozí stránce, zobrazíse jedna z dalších stránek. Můžete si stáhnout ukázku [ColorWebApp,](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) nebo jen sledovat spolu s vlastní webovou aplikací.

![Spuštění webové aplikace, která má být testována](../test/media/web_test_databinding_runwebapp.png)

Vaše řešení by také mělo obsahovat test výkonu webu, který prochází stránky webové aplikace.

![Řešení s testem výkonu webu](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Vytvoření databáze SQL

::: moniker range="vs-2017"

1. Pokud visual studio enterprise nemáte, můžete si ho stáhnout ze stránky [Stažení sady Visual Studio.](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

2. Vytvořte databázi SQL.

     ![Přidání nové databáze SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Vytvořte databázový projekt.

     ![Vytvořit nový projekt z databáze](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Přidejte tabulku do databázového projektu.

     ![Přidání nové tabulky do databázového projektu](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Přidejte do tabulky pole.

     ![Přidání polí do tabulky](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikujte databázový projekt.

     ![Publikovat databázový projekt z Průzkumníka řešení](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Přidejte data do polí.

     ![Přidání dat do polí](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Pokud visual studio enterprise nemáte, můžete si ho stáhnout ze stránky [Stažení sady Visual Studio.](https://visualstudio.microsoft.com/downloads)

2. Vytvořte databázi SQL.

     ![Přidání nové databáze SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Vytvořte databázový projekt.

     ![Vytvořit nový projekt z databáze](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Přidejte tabulku do databázového projektu.

     ![Přidání nové tabulky do databázového projektu](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Přidejte do tabulky pole.

     ![Přidání polí do tabulky](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikujte databázový projekt.

     ![Publikovat databázový projekt z Průzkumníka řešení](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Přidejte data do polí.

     ![Přidání dat do polí](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Přidání zdroje dat

1. Přidejte zdroj dat.

     ![Přidání zdroje dat do testu výkonu webu](../test/media/web_test_databinding_sql_adddatasource.png)

2. Zvolte typ zdroje dat a pojmenujte jej.

     ![Pojmenování zdroje databáze](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Vytvořte připojení.

     ![Zvolte nové připojení](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Zadejte podrobnosti o připojení.

     ![Zadání vlastností připojení databáze SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Vyberte tabulku, kterou chcete použít pro test.

     ![Přidání tabulky Barva jako zdroje dat](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tabulka je vázána na test.

     ![Uzel Zdroje dat přidat do testu výkonu webu](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Uložte test.

## <a name="bind-the-data"></a>Svázat data

1. Spojte pole **ColorName.**

     ![Vazba pole ColorName na hodnotu RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Otevřete soubor *Local.testsettings* v **Průzkumníku řešení** a vyberte možnost **Jedno spuštění na řádek zdroje dat.**

     ![Úprava souboru nastavení testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Uložte test výkonu webu.

## <a name="run-the-test-with-the-data"></a>Spuštění testu s daty

1. Spusťte test.

     ![Spuštění testu výkonu webu k ověření vazby](../test/media/web_test_databinding_sql_runtest.png)

     Dva spuštění jsou zobrazeny pro každý řádek dat. Spuštění 1 odešle požadavek na stránku *Red.aspx*a Spustit 2 odešle požadavek na stránku *Blue.aspx*.

     ![Výsledky testu](../test/media/web_test_databinding_sql_runresults.png)

     Při svázání spoje se zdrojem dat můžete porušit výchozí pravidlo adresy URL odpovědi. V tomto případě je chyba v Run 2 je způsobena pravidlem, které očekává, že stránka *Red.aspx* z původního testovacího záznamu, ale datová vazba ji nyní přesměruje na stránku *Blue.aspx.*

2. Opravte chybu ověření odstraněním ověřovacího pravidla **adresy URL odpovědi** a znovu spuštěním testu.

     ![Odstranění ověřovacího pravidla adresy URL odpovědi](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Test výkonu webu nyní prochází pomocí datové vazby.

     ![Testovací průchody pomocí datové vazby](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Otázky a odpovědi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Otázka: Jaké databáze lze použít jako zdroj dat?

**A:** Můžete použít následující:

- Microsoft SQL Azure.

- Libovolná verze serveru Microsoft SQL Server 2005 nebo novější.

- Databázový soubor serveru Microsoft SQL Server (včetně sql expressu).

- Microsoft ODBC.

- Soubor aplikace Microsoft Access pomocí zprostředkovatele rozhraní .NET Framework pro technologie OLE DB.

- Oracle 7.3, 8i, 9i nebo 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Otázka: Jak lze použít textový soubor s oddělenými čárkami (CSV) jako zdroj dat?

**A:** Postup je:

1. Vytvořte složku pro uspořádání artefaktů databáze projektů a přidejte položku.

     ![Přidání nové položky do složky Data](../test/media/web_test_databinding_foldernewitem.png)

2. Vytvořte textový soubor.

     ![Pojmenování nového textového souboru ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Upravte textový soubor a přidejte následující:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Použijte postup v [části Přidání zdroje dat](#add-the-data-source), ale jako zdroj dat zvolte soubor CSV.

     ![Zadejte název a zvolte soubor CSV.](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Otázka: Co když můj existující soubor CSV neobsahuje záhlaví sloupců?

**A:** Pokud nemůžete přidat záhlaví sloupců, můžete použít soubor popisu schématu k tomu, abyste se souborem CSV považovali za databázi.

1. Přidejte nový textový soubor s názvem *schema.ini*.

     ![Přidání souboru schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Upravte soubor *schema.ini* a přidejte informace popisující strukturu dat. Například soubor schématu popisující soubor CSV může vypadat takto:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Přidejte do testu zdroj dat.

     ![Přidání zdroje dat do testu výkonu webu](../test/media/web_test_databinding_sql_adddatasource.png)

4. Pokud používáte soubor *schema.ini,* zvolte jako zdroj dat **databázi** (ne soubor CSV) a pojmenujte ji.

     ![Přidání zdroje dat databáze](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Vytvořte nové připojení.

     ![Zvolte nové připojení](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Vyberte zprostředkovatele dat rozhraní .NET Framework pro technologie OLE DB.

     ![Vyberte zprostředkovatele dat OLE DB rozhraní .NET framework.](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Zvolte **Upřesnit**.

     ![Zvolte Upřesnit](../test/media/web_test_databinding_advanced.png)

8. Pro vlastnost Provider vyberte Microsoft.Jet.OLEDB.4.0 a nastavte **rozšířené vlastnosti** na text; HDR=NE.

     ![Použití rozšířených vlastností](../test/media/web_test_databinding_advancedproperties.png)

9. Zadejte název složky, která obsahuje soubor schématu, a otestujte připojení.

     ![Zadání cesty ke složce dat](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Vyberte soubor CSV, který chcete použít.

     ![Výběr textového souboru](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Po dokončení se soubor CSV zobrazí jako tabulka.

     ![Zdroj dat přidaný do testu](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Otázka: Jak se používá soubor XML jako zdroj dat?

**Odpověď:** Ano.

1. Vytvořte složku pro uspořádání artefaktů databáze projektů a přidejte položku.

     ![Přidání nové položky do složky Data](../test/media/web_test_databinding_foldernewitem.png)

2. Vytvořte soubor XML.

     ![Přidání souboru ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Upravte soubor XML a přidejte data:

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

4. Použijte postup v [části Přidání zdroje dat](#add-the-data-source), ale jako zdroj dat zvolte soubor XML.

     ![Zadání názvu a volba souboru XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Otázka: Lze přidat datovou vazbu do požadavku webové služby, který používá SOAP?

**A:** Ano, je nutné změnit SOAP XML ručně.

1. Zvolte požadavek webové služby ve stromu požadavků a v okně Vlastnosti zvolte tři tečky (...) ve vlastnosti Tělo řetězce.

     ![Úprava těla řetězce webové služby](../test/media/web_test_databinding_webservicerequest.png)

2. Nahraďte hodnoty v těle SOAP hodnotami hodnotami vázanými na data pomocí následující syntaxe:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Například pokud máte následující kód:

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

    Můžete ji změnit na toto:

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

3. Uložte test.
