---
title: Přidání zdroje dat do testu výkonnosti webu
description: Zjistěte, jak vytvořit vazbu dat, abyste ke stejnému testu poskytovali různé hodnoty, například k poskytnutí různých hodnot parametrů formuláře post.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 71aa3dbf4657896093dae59451140f48f83f1622
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761001"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Přidání zdroje dat do testu výkonnosti webu

Vytvořte vazbu dat, abyste ke stejnému testu poskytovali různé hodnoty, například k poskytnutí různých hodnot parametrů formuláře post.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Vytvoření vazby dat k testu výkonnosti webu](../test/media/web_test_databinding_conceptual.png)

Použijeme ukázkovou aplikaci ASP.NET dat. Má tři *stránky .aspx* – výchozí stránku, červenou stránku a modrou stránku. Výchozí stránka má přepínač pro výběr červeného nebo modrého tlačítka a tlačítka odeslat. Další dvě stránky *.aspx* jsou velmi jednoduché. Jeden má popisek s názvem Red (Červený) a druhý má popisek s názvem Blue (Modrý). Když zvolíte odeslat na výchozí stránce, zobrazí se jedna z ostatních stránek. Můžete si stáhnout [ukázku ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) nebo si jednoduše prohlédněte vlastní webovou aplikaci.

![Spuštění webové aplikace, která se má otestovat](../test/media/web_test_databinding_runwebapp.png)

Vaše řešení by také mělo zahrnovat test výkonnosti webu, který prochází stránky webové aplikace.

![Řešení s testem výkonnosti webu](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Vytvoření databáze SQL

::: moniker range="vs-2017"

1. Pokud nemáte k dispozici Visual Studio Enterprise, můžete si ho stáhnout ze [stránky Visual Studio soubory ke](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stažení.

2. Vytvořte databázi SQL.

     ![Přidání nové databáze SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Vytvořte databázový projekt.

     ![Vytvoření nového projektu z databáze](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Přidejte tabulku do databázového projektu.

     ![Přidání nové tabulky do databázového projektu](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Přidejte do tabulky pole.

     ![Přidání polí do tabulky](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikujte databázový projekt.

     ![Publikování databázového projektu z Průzkumník řešení](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Přidejte data do polí.

     ![Přidání dat do polí](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Pokud nemáte k dispozici Visual Studio Enterprise, můžete si ho stáhnout ze [stránky Visual Studio soubory ke](https://visualstudio.microsoft.com/downloads) stažení.

2. Vytvořte databázi SQL.

     ![Přidání nové databáze SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Vytvořte databázový projekt.

     ![Vytvoření nového projektu z databáze](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Přidejte tabulku do databázového projektu.

     ![Přidání nové tabulky do databázového projektu](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Přidejte do tabulky pole.

     ![Přidání polí do tabulky](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikujte databázový projekt.

     ![Publikování databázového projektu z Průzkumník řešení](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Přidejte data do polí.

     ![Přidání dat do polí](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Přidání zdroje dat

1. Přidejte zdroj dat.

     ![Přidání zdroje dat do testu výkonnosti webu](../test/media/web_test_databinding_sql_adddatasource.png)

2. Zvolte typ zdroje dat a pojmnte ho.

     ![Název zdroje databáze](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Vytvořte připojení.

     ![Volba nového připojení](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Zadejte podrobnosti o připojení.

     ![Zadejte vlastnosti připojení k databázi SQL.](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Vyberte tabulku, kterou chcete použít pro svůj test.

     ![Přidání tabulky Color jako zdroje dat](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tabulka je svázaná s testem.

     ![Přidání uzlu Zdroje dat do testu výkonnosti webu](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Uložte test.

## <a name="bind-the-data"></a>Vytvoření vazby dat

1. Vytvořte **vazbu pole ColorName.**

     ![Vytvoření vazby pole ColorName k hodnotě RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Otevřete soubor *Local.testsettings* v **Průzkumník řešení** a vyberte možnost **Jeden běh na řádek zdroje** dat.

     ![Úprava souboru nastavení testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Uložte test výkonnosti webu.

## <a name="run-the-test-with-the-data"></a>Spuštění testu s daty

1. Spusťte test.

     ![Spuštění testu výkonnosti webu pro ověření vazby](../test/media/web_test_databinding_sql_runtest.png)

     Pro každý řádek dat se zobrazí dvě spuštění. Spuštění 1 odešle požadavek na stránku *Red.aspx* a Run 2 odešle požadavek na stránku *Blue.aspx.*

     ![Výsledky testovacího běhu](../test/media/web_test_databinding_sql_runresults.png)

     Při navázání na zdroj dat můžete porušovat výchozí pravidlo adresy URL odpovědi. V tomto případě je příčinou chyby ve spuštění 2 pravidlo, které očekává stránku *Red.aspx* z původního testovacího záznamu, ale datová vazba ji teď přesměruje na *stránku Blue.aspx.*

2. Opravte chybu ověřování odstraněním ověřovacího **pravidla adresy URL** odpovědi a znovu spuštěním testu.

     ![Odstranění ověřovacího pravidla adresy URL odpovědi](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Test výkonnosti webu teď prochází pomocí datové vazby.

     ![Testovací průchody s využitím datové vazby](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Otázky a odpovědi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Otázka: Jaké databáze můžu použít jako zdroj dat?

**O:** Můžete použít následující:

- Microsoft SQL Azure.

- Libovolná verze Microsoft SQL Server 2005 nebo novější.

- Microsoft SQL Server databázového souboru (včetně SQL Expressu).

- Microsoft ODBC.

- Soubor Aplikace Microsoft Access .NET Framework poskytovatele OLE DB.

- Oracle 7.3, 8i, 9i nebo 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Otázka: Návody jako zdroj dat použít textový soubor s oddělovači (CSV)?

**O:** Tady je postup:

1. Vytvořte složku pro uspořádání artefaktů databáze projektů a přidání položky.

     ![Přidání nové položky do složky Data](../test/media/web_test_databinding_foldernewitem.png)

2. Vytvořte textový soubor.

     ![Pojmete nový textový soubor ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Upravte textový soubor a přidejte následující:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Použijte postup v části [Přidání zdroje dat,](#add-the-data-source)ale jako zdroj dat zvolte Soubor CSV.

     ![Zadejte název a zvolte Soubor CSV.](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Otázka: Co když můj existující soubor CSV neobsahuje záhlaví sloupců?

**O:** Pokud nemůžete přidat záhlaví sloupců, můžete k označení souboru CSV jako k databázi použít soubor s popisem schématu.

1. Přidejte nový textový soubor s názvem *schema.ini*.

     ![Přidání schema.ini souboru](../test/media/web_test_databinding_schemafile.png)

2. Upravte *schema.ini* a přidejte informace popisující strukturu vašich dat. Soubor schématu popisující soubor CSV může například vypadat takhle:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Přidejte do testu zdroj dat.

     ![Přidání zdroje dat do testu výkonnosti webu](../test/media/web_test_databinding_sql_adddatasource.png)

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
