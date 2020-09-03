---
title: 'Návod: použití konfiguračního souboru k definování zdroje dat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 34
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f669c4dcfb91579ac50270914112cd6388e2743
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547976"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Návod: Použití konfiguračního souboru k definování zdroje dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak použít zdroj dat definovaný v souboru app.config pro testování částí. Naučíte se, jak vytvořit soubor app.config definující zdroj dat, který může být použit <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> třídou. Úlohy v tomto návodu zahrnují následující:

- Vytváří se soubor app.config.

- Definování vlastního konfiguračního oddílu.

- Definování připojovacích řetězců.

- Definování zdrojů dat.

- Přístup ke zdrojům dat pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> třídy.

## <a name="prerequisites"></a>Předpoklady
 K dokončení toho návodu budete potřebovat:

- Visual Studio Enterprise

- Data pro alespoň jednu z testovacích metod poskytují buď Microsoft Access, nebo Microsoft Excel.

- Řešení sady Visual Studio, které obsahuje projekt testů.

## <a name="create-the-appconfig-file"></a>Vytvoření souboru App.config

#### <a name="to-add-an-appconfig-file-to-the-project"></a>Přidání souboru app.config do projektu

1. Pokud váš projekt testů již obsahuje soubor app.config, použijte příkaz [definovat vlastní konfigurační oddíl](#DefineCustomConfigurationSection).

2. Klikněte pravým tlačítkem na projekt testů v **Průzkumník řešení**, přejděte na **Přidat**a klikněte na **Nová položka**.

     Otevře se okno **Přidat novou položku** .

3. Vyberte šablonu **konfigurační soubor aplikace** a klikněte na **Přidat**.

## <a name="define-a-custom-configuration-section"></a><a name="DefineCustomConfigurationSection"></a> Definovat vlastní konfigurační oddíl
 Prověřte soubor app.config. Obsahuje alespoň deklaraci XML a kořenový element.

#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Přidání oddílu vlastní konfigurace do souboru app.config

1. Kořenový element app.config by měl být `configuration` element. Vytvořte `configSections` element v rámci `configuration` elementu. `configSections`Měl by být prvním prvkem v souboru app.config.

2. V rámci `configSections` elementu vytvořte `section` element.

3. V `section` elementu přidejte atribut s názvem `name` a přiřaďte mu hodnotu Equal `microsoft.visualstudio.testtools` . Přidejte další atribut `type` s názvem a přiřaďte mu hodnotu EQUAL `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

   `section`Element by měl vypadat nějak takto:

```
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
```

> [!NOTE]
> Název sestavení musí odpovídat Microsoft Visual Studiomu sestavení .NET Framework, které používáte. Nastavte verzi na 9.0.0.0, pokud používáte sadu Visual Studio .NET Framework 3,5. Pokud používáte sadu Visual Studio .NET Framework 2,0, nastavte verzi na 8.0.0.0.

## <a name="define-connection-strings"></a>Definování připojovacích řetězců
 Připojovací řetězce definují informace specifické pro poskytovatele pro přístup ke zdrojům dat. Připojovací řetězce definované v konfiguračních souborech poskytují znovu použitelné informace o poskytovateli dat v rámci aplikace. V této části vytvoříte dva připojovací řetězce, které budou použity zdroji dat, které jsou definovány v části vlastní konfigurace.

#### <a name="to-define-connection-strings"></a>Definování připojovacích řetězců

1. Po `configSections` elementu vytvořte `connectionStrings` element.

2. V rámci `connectionStrings` elementu vytvořte dva `add` elementy.

3. V prvním `add` elementu vytvořte následující atributy a hodnoty pro připojení k databázi aplikace Microsoft Access:

|Atribut|Hodnoty|
|---------------|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

 V druhém `add` elementu vytvořte následující atributy a hodnoty pro připojení k tabulce aplikace Microsoft Excel:

|Atribut|Hodnoty|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

 `connectionStrings`Element by měl vypadat nějak takto:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definování zdrojů dat
 Část zdroje dat obsahuje čtyři atributy, které používá testovací modul k načtení dat ze zdroje dat.

- `name` definuje identitu, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> kterou používá k určení zdroje dat, který se má použít.

- `connectionString` Určuje připojovací řetězec vytvořený v předchozím oddílu definování připojovacích řetězců.

- `dataTableName` definuje tabulku nebo list obsahující data, která se mají použít v testu.

- `dataAccessMethod` definuje techniku pro přístup k datovým hodnotám ve zdroji dat.

  V této části definujete dva zdroje dat, které se použijí při testování částí.

#### <a name="to-define-data-sources"></a>Definování zdrojů dat

1. Po `connectionStrings` elementu vytvořte `microsoft.visualstudio.testtools` element. Tento oddíl byl vytvořen v části definice vlastního konfiguračního oddílu.

2. V rámci `microsoft.visualstudio.testtools` elementu vytvořte `dataSources` element.

3. V rámci `dataSources` elementu vytvořte dva `add` elementy.

4. V prvním `add` elementu vytvořte následující atributy a hodnoty pro zdroj dat Microsoft Access:

|Atribut|Hodnota|
|---------------|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

 V druhém `add` elementu vytvořte následující atributy a hodnoty pro zdroj dat aplikace Microsoft Excel:

|Atribut|Hodnota|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

 `microsoft.visualstudio.testtools`Element by měl vypadat nějak takto:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

 Konečný app.config soubor by měl vypadat nějak takto:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Vytvoření testu jednotek pomocí zdrojů dat definovaných v app.config
 Nyní, když je definován soubor app.config, vytvoříte test jednotky, který používá data umístěná ve zdrojích dat, které jsou definovány v souboru app.config. V této části budeme:

- Vytvořte zdroje dat nalezené v souboru app.config.

- Použijte zdroje dat ze dvou testovacích metod, které porovnávají hodnoty v jednotlivých zdrojích dat.

#### <a name="to-create-a-microsoft-access-data-source"></a>Vytvoření zdroje dat aplikace Microsoft Access

1. Vytvořte databázi aplikace Microsoft Access s názvem `testdatasource.accdb` .

2. Vytvořte tabulku a pojmenujte ji `MyDataTable` v `testdatasource.accdb` .

3. Vytvořte dvě pole v `MyDataTable` pojmenovaném `Arg1` a `Arg2` pomocí `Number` datového typu.

4. Přidejte pět entit do `MyDataTable` s následujícími hodnotami pro `Arg1` a `Arg2` , v uvedeném pořadí: (10, 50), (3, 2), (6, 0), (0, 8) a (12312, 1000).

5. Uložte a zavřete databázi.

6. Změňte připojovací řetězec tak, aby odkazoval na umístění databáze. Změňte hodnotu tak, `Data Source` aby odrážela umístění databáze.

#### <a name="to-create-a-microsoft-excel-data-source"></a>Vytvoření zdroje dat v aplikaci Microsoft Excel

1. Vytvořte tabulku aplikace Microsoft Excel s názvem `data.xlsx` .

2. Vytvořte list s názvem, `Sheet1` Pokud ještě neexistuje v `data.xlsx` .

3. Vytvořte dvě záhlaví sloupců a pojmenujte je `Val1` a `Val2` v `Sheet1` .

4. Přidejte pět entit do `Sheet1` s následujícími hodnotami pro `Val1` a `Val2` , v tomto pořadí: (1, 1), (2, 2), (3, 3), (4, 4) a (5, 0).

5. Uložte a zavřete tabulku.

6. Změňte připojovací řetězec tak, aby odkazoval na umístění tabulky. Změňte hodnotu tak, `dbq` aby odrážela umístění tabulky.

#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Postup vytvoření testu jednotek pomocí app.config zdrojů dat

1. Přidejte test jednotek do testovacího projektu.

     Další informace naleznete v tématu [vytváření a spouštění testů jednotek pro existující kód](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173).

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

3. Projděte si atributy DataSource. Všimněte si názvů nastavení ze souboru app.config.

4. Sestavte řešení a spusťte testy MyTestMethod a MyTestMethod2.

> [!IMPORTANT]
> Nasaďte položky jako zdroje dat tak, aby byly přístupné pro test v adresáři nasazení.

## <a name="see-also"></a>Viz také
 [Testování částí kódu](../test/unit-test-your-code.md) [vytváření a spouštění testů jednotek pro existující testování kódu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) [aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [: vytvoření testu jednotek řízených daty](../test/how-to-create-a-data-driven-unit-test.md)
