---
title: Přidání zdroje dat do testu výkonnosti webu
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94ad53e4ac3d65bfe6cf08bf03f1f79c2075e03d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289063"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Přidání zdroje dat do testu výkonnosti webu

Vázání dat k poskytnutí různých hodnot stejnému testu, například k poskytnutí různých hodnot parametrům post formuláře.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Vázání dat k testu výkonnosti webu](../test/media/web_test_databinding_conceptual.png)

Budeme používat ukázkovou aplikaci ASP.NET. Má tři stránky *. aspx* – výchozí stránku, červenou stránku a modrou stránku. Výchozí stránka obsahuje ovládací prvek přepínač pro výběr červeného nebo modrého tlačítka a tlačítka Odeslat. Ostatní dvě stránky *aspx* jsou velmi jednoduché. Jeden má popisek s názvem Red a druhý má popisek s názvem modrý. Když zvolíte odeslat na výchozí stránce, zobrazíme jednu z dalších stránek. Můžete si stáhnout ukázku [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) nebo jenom sledovat vlastní webovou aplikaci.

![Spuštění webové aplikace, která se má testovat](../test/media/web_test_databinding_runwebapp.png)

Vaše řešení by mělo také zahrnovat test výkonnosti webu, který prochází stránky webové aplikace.

![Řešení s testem výkonnosti webu](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Vytvoření databáze SQL

::: moniker range="vs-2017"

1. Pokud nemáte Visual Studio Enterprise, můžete si ho stáhnout ze stránky [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) .

2. Vytvořte databázi SQL.

     ![Přidat novou databázi SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Vytvořte projekt databáze.

     ![Vytvořit nový projekt z databáze](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Přidejte tabulku do projektu databáze.

     ![Přidat novou tabulku do projektu databáze](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Přidejte pole do tabulky.

     ![Přidat pole do tabulky](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikování databázového projektu.

     ![Publikovat databázový projekt z Průzkumník řešení](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Přidejte data do polí.

     ![Přidat data do polí](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Pokud nemáte Visual Studio Enterprise, můžete si ho stáhnout ze stránky [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) .

2. Vytvořte databázi SQL.

     ![Přidat novou databázi SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Vytvořte projekt databáze.

     ![Vytvořit nový projekt z databáze](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Přidejte tabulku do projektu databáze.

     ![Přidat novou tabulku do projektu databáze](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Přidejte pole do tabulky.

     ![Přidat pole do tabulky](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikování databázového projektu.

     ![Publikovat databázový projekt z Průzkumník řešení](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Přidejte data do polí.

     ![Přidat data do polí](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Přidat zdroj dat

1. Přidejte zdroj dat.

     ![Přidat zdroj dat do testu výkonnosti webu](../test/media/web_test_databinding_sql_adddatasource.png)

2. Vyberte typ zdroje dat a pojmenujte ho.

     ![Pojmenování zdroje databáze](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Vytvořte připojení.

     ![Zvolit nové připojení](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Zadejte podrobnosti připojení.

     ![Zadejte vlastnosti připojení k databázi SQL.](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Vyberte tabulku, kterou chcete použít pro test.

     ![Přidat tabulku barev jako zdroj dat](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tabulka je svázána s testem.

     ![Uzel zdroje dat přidání do testu výkonnosti webu](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Uložte test.

## <a name="bind-the-data"></a>Svázání dat

1. Navažte pole **Color** .

     ![Navázání pole Color k hodnotě RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. V **Průzkumník řešení** otevřete soubor *Local. testsettings* a vyberte jednu možnost **Spustit na řádek zdroje dat** .

     ![Upravit soubor nastavení testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Uložte test výkonnosti webu.

## <a name="run-the-test-with-the-data"></a>Spustit test s daty

1. Spusťte test.

     ![Spustit test výkonnosti webu pro ověření vazby](../test/media/web_test_databinding_sql_runtest.png)

     Pro každý řádek dat se zobrazí dva běhy. Spuštění 1 odešle požadavek na stránku *Red. aspx*a spuštění 2 odešle požadavek na stránku *Blue. aspx*.

     ![Výsledky testovacího běhu](../test/media/web_test_databinding_sql_runresults.png)

     Při vytváření vazby na zdroj dat můžete narušit výchozí pravidlo adresy URL odpovědi. V tomto případě Chyba v běhu 2 je způsobena pravidlem, které očekává stránku *Red. aspx* z původního záznamu testu, ale datovou vazbu je nyní směruje na stránku *Blue. aspx* .

2. Opravte chybu ověřování tak, že odstraníte pravidlo pro ověření **adresy URL odpovědi** a znovu spustíte test.

     ![Odstraní pravidlo pro ověření adresy URL odpovědi.](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Test výkonnosti webu nyní projde pomocí datové vazby.

     ![Test průchodů pomocí datové vazby](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Otázky a odpovědi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Otázka: Jaké databáze lze použít jako zdroj dat?

**A:** Můžete použít následující:

- Microsoft SQL Azure.

- Všechny verze Microsoft SQL Server 2005 nebo novější.

- Soubor databáze Microsoft SQL Server (včetně SQL Express).

- Rozhraní Microsoft ODBC.

- Soubor aplikace Microsoft Access s použitím poskytovatele .NET Framework pro OLE DB.

- Oracle 7,3, 8i, 9i nebo 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Otázka: Návody jako zdroj dat použít textový soubor s oddělovači (CSV)?

**A:** Tady je postup:

1. Vytvořte složku pro uspořádání artefaktů databáze projektů a přidejte položku.

     ![Přidat novou položku do složky data](../test/media/web_test_databinding_foldernewitem.png)

2. Vytvořte textový soubor.

     ![Pojmenujte nový textový soubor ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Upravte textový soubor a přidejte následující:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Použijte postup v části [Přidat zdroj dat](#add-the-data-source), ale jako zdroj dat vyberte soubor CSV.

     ![Zadejte název a vyberte soubor CSV.](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Otázka: Co když můj existující soubor CSV neobsahuje záhlaví sloupců?

**A:** Pokud nemůžete přidat záhlaví sloupců, můžete použít soubor s popisem schématu, který zachází se souborem CSV jako s databází.

1. Přidejte nový textový soubor s názvem *schema.ini*.

     ![Přidat soubor schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Úpravou souboru *schema.ini* přidejte informace, které popisují strukturu vašich dat. Například soubor schématu popisující soubor CSV může vypadat takto:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Přidejte zdroj dat do testu.

     ![Přidat zdroj dat do testu výkonnosti webu](../test/media/web_test_databinding_sql_adddatasource.png)

4. Pokud používáte soubor *schema.ini* , vyberte jako zdroj dat možnost **databáze** (ne soubor CSV) a pojmenujte ji.

     ![Přidat zdroj dat databáze](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Vytvořte nové připojení.

     ![Zvolit nové připojení](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Vyberte .NET Framework Zprostředkovatel dat OLE DB.

     ![Vyberte poskytovatele dat OLE DB .NET Framework.](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Klikněte na tlačítko **Upřesnit**.

     ![Zvolit pokročilé](../test/media/web_test_databinding_advanced.png)

8. U vlastnosti poskytovatel vyberte Microsoft. Jet. OLEDB. 4.0 a pak nastavte **Rozšířené vlastnosti** na text. HDR = NO.

     ![Použít pokročilé vlastnosti](../test/media/web_test_databinding_advancedproperties.png)

9. Zadejte název složky, která obsahuje soubor schématu a otestujte připojení.

     ![Zadejte cestu ke složce dat.](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Vyberte soubor CSV, který chcete použít.

     ![Vyberte textový soubor.](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Po dokončení se soubor CSV zobrazí jako tabulka.

     ![Zdroj dat přidaný do testu](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Otázka: Návody použít soubor XML jako zdroj dat?

**Odpověď:** Ano.

1. Vytvořte složku pro uspořádání artefaktů databáze projektů a přidejte položku.

     ![Přidat novou položku do složky data](../test/media/web_test_databinding_foldernewitem.png)

2. Vytvoří soubor XML.

     ![Přidat ColorData.xml soubor](../test/media/web_test_databinding_additemxmlfile.png)

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

4. Použijte postup v části [Přidat zdroj dat](#add-the-data-source), ale jako zdroj dat vyberte soubor XML.

     ![Zadejte název a vyberte soubor XML.](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Otázka: mohu přidat datovou vazbu k požadavku webové služby, který používá protokol SOAP?

**A:** Ano, kód SOAP XML je nutné ručně změnit.

1. Ve stromové struktuře žádosti vyberte požadavek webové služby a v okno Vlastnosti vyberte tři tečky (...) ve vlastnosti tělo řetězce.

     ![Upravit tělo řetězce webové služby](../test/media/web_test_databinding_webservicerequest.png)

2. Nahraďte hodnoty v těle SOAP hodnotami vázanými daty pomocí následující syntaxe:

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

3. Uložte test.
