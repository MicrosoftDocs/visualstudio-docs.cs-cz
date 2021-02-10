---
title: Použití konfiguračního souboru k definování zdroje dat
description: Naučte se používat zdroj dat definovaný v souboru app.config pro testování částí počínaje vytvořením app.config souboru, který definuje zdroj dat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f234d0285f5a0ed01567bb77c21e4c2d080a5f64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967875"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Návod: použití konfiguračního souboru k definování zdroje dat

Tento návod ukazuje, jak použít zdroj dat definovaný v souboru *app.config* pro testování částí. Naučíte se, jak vytvořit soubor *app.config* definující zdroj dat, který může být použit <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> třídou. Úlohy v tomto návodu zahrnují následující:

- Vytváří se soubor *app.config* .

- Definování vlastního konfiguračního oddílu.

- Definování připojovacích řetězců.

- Definování zdrojů dat.

- Přístup ke zdrojům dat pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> třídy.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto názorného postupu potřebujete:

- Visual Studio Enterprise

- Data pro alespoň jednu z testovacích metod poskytují buď Microsoft Access, nebo Microsoft Excel.

- Řešení sady Visual Studio, které obsahuje projekt testů.

## <a name="add-an-appconfig-file-to-the-project"></a>Přidat soubor app.config do projektu

1. Pokud váš projekt testů již obsahuje soubor *app.config* , použijte příkaz [definovat vlastní konfigurační oddíl](#define-a-custom-configuration-section).

2. Klikněte pravým tlačítkem na projekt testů v **Průzkumník řešení** a pak vyberte **Přidat**  >  **novou položku**.

     Otevře se okno **Přidat novou položku** .

3. Vyberte šablonu **konfigurační soubor aplikace** a klikněte na **Přidat**.

## <a name="define-a-custom-configuration-section"></a>Definovat vlastní konfigurační oddíl

Prověřte soubor *app.config* . Obsahuje alespoň deklaraci XML a kořenový element.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Přidání oddílu vlastní konfigurace do souboru app.config

1. Kořenový element *app.config* by měl být **konfigurační** element. Vytvořte element **configSections** v rámci **konfiguračního** elementu. **ConfigSections** by měl být prvním prvkem v souboru *app.config* .

2. V rámci elementu **configSections** vytvořte **oddíl** elementu.

3. V elementu **oddílu** přidejte atribut s názvem `name` a přiřaďte mu hodnotu `microsoft.visualstudio.testtools` . Přidejte další atribut `type` s názvem a přiřaďte mu hodnotu `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions` .

Element **Section** by měl vypadat nějak takto:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Název sestavení musí odpovídat verzi, kterou používáte.

## <a name="define-connection-strings"></a>Definování připojovacích řetězců

Připojovací řetězce definují informace specifické pro poskytovatele pro přístup ke zdrojům dat. Připojovací řetězce definované v konfiguračních souborech poskytují znovu použitelné informace o poskytovateli dat v rámci aplikace. V této části vytvoříte dva připojovací řetězce, které budou použity zdroji dat, které jsou definovány v části vlastní konfigurace.

### <a name="to-define-connection-strings"></a>Definování připojovacích řetězců

1. Za element **configSections** vytvořte element **connectionStrings** .

2. V rámci elementu **connectionStrings** vytvořte dva prvky **Add** .

3. V prvním prvku **Přidat** vytvořte následující atributy a hodnoty pro připojení k databázi aplikace Microsoft Access:

|Atribut|Hodnoty|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

Ve druhém elementu **Add přidejte** následující atributy a hodnoty pro připojení k tabulce aplikace Microsoft Excel:

|Atribut|Hodnoty|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

Element **connectionStrings** by měl vypadat nějak takto:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definování zdrojů dat

Část zdroje dat obsahuje čtyři atributy, které používá testovací modul k načtení dat ze zdroje dat.

- `name` definuje identitu, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> kterou používá k určení zdroje dat, který se má použít.

- `connectionString` Určuje připojovací řetězec vytvořený v předchozím oddílu definování připojovacích řetězců.

- `dataTableName` definuje tabulku nebo list obsahující data, která se mají použít v testu.

- `dataAccessMethod` definuje techniku pro přístup k datovým hodnotám ve zdroji dat.

V této části definujete dva zdroje dat, které se použijí při testování částí.

### <a name="to-define-data-sources"></a>Definování zdrojů dat

1. Po elementu **connectionStrings** vytvořte prvek **Microsoft. VisualStudio. TestTools** . Tento oddíl byl vytvořen v části definice vlastního konfiguračního oddílu.

2. V rámci elementu **Microsoft. VisualStudio. TestTools** vytvořte element **DataSources** .

3. V elementu **DataSources** vytvořte dva prvky **Přidat** .

4. V prvním prvku **Přidat** vytvořte následující atributy a hodnoty pro zdroj dat Microsoft Access:

|Atribut|Hodnoty|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

Ve druhém elementu **Add** element vytvořte následující atributy a hodnoty pro zdroj dat aplikace Microsoft Excel:

|Atribut|Hodnoty|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

Element **Microsoft. VisualStudio. TestTools** by měl vypadat nějak takto:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Konečný *app.config* soubor by měl vypadat nějak takto:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Vytvoření testu jednotek, který používá zdroje dat definované v app.config

Nyní, když je definován soubor *app.config* , vytvoříte test jednotky, který používá data umístěná ve zdrojích dat, které jsou definovány v souboru *app.config* . V této části budeme:

- Vytvořte zdroje dat nalezené v souboru *app.config* .

- Použijte zdroje dat ze dvou testovacích metod, které porovnávají hodnoty v jednotlivých zdrojích dat.

### <a name="to-create-a-microsoft-access-data-source"></a>Vytvoření zdroje dat aplikace Microsoft Access

1. Vytvořte databázi aplikace Microsoft Access s názvem *testdatasource. accdb*.

2. Vytvořte tabulku a pojmenujte ji `MyDataTable` v *testdatasource. accdb*.

3. Vytvořte dvě pole v `MyDataTable` pojmenovaném `Arg1` a `Arg2` pomocí `Number` datového typu.

4. Přidejte pět entit do `MyDataTable` s následujícími hodnotami pro `Arg1` a `Arg2` , v uvedeném pořadí: (10, 50), (3, 2), (6, 0), (0, 8) a (12312, 1000).

5. Uložte a zavřete databázi.

6. Změňte připojovací řetězec tak, aby odkazoval na umístění databáze. Změňte hodnotu tak, `Data Source` aby odrážela umístění databáze.

### <a name="to-create-a-microsoft-excel-data-source"></a>Vytvoření zdroje dat v aplikaci Microsoft Excel

1. Vytvořte tabulku aplikace Microsoft Excel s názvem *data.xlsx*.

2. Vytvořte list s názvem, `Sheet1` Pokud ještě neexistuje v *data.xlsx*.

3. Vytvořte dvě záhlaví sloupců a pojmenujte je `Val1` a `Val2` v `Sheet1` .

4. Přidejte pět entit do `Sheet1` s následujícími hodnotami pro `Val1` a `Val2` , v tomto pořadí: (1, 1), (2, 2), (3, 3), (4, 4) a (5, 0).

5. Uložte a zavřete tabulku.

6. Změňte připojovací řetězec tak, aby odkazoval na umístění tabulky. Změňte hodnotu tak, `dbq` aby odrážela umístění tabulky.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Postup vytvoření testu jednotek pomocí app.config zdrojů dat

1. Přidejte test jednotek do testovacího projektu.

2. Automaticky generovaný obsah testu jednotek nahraďte následujícím kódem:

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3. Projděte si atributy DataSource. Všimněte si názvů nastavení ze souboru *app.config* .

4. Sestavte řešení a spusťte testy MyTestMethod a MyTestMethod2.

> [!IMPORTANT]
> Nasaďte položky jako zdroje dat tak, aby byly přístupné pro test v adresáři nasazení.

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Postupy: vytvoření testu jednotek řízených daty](../test/how-to-create-a-data-driven-unit-test.md)
