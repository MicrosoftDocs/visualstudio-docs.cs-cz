---
title: Definování zdroje dat pomocí konfiguračního souboru
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a4f5731a828eb04e57f56a46fe399125b5ded2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75776160"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Návod: Definování zdroje dat pomocí konfiguračního souboru

Tento návod ukazuje, jak používat zdroj dat definovaný v souboru *app.config* pro testování částí. Dozvíte se, jak vytvořit soubor *app.config,* který definuje zdroj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> dat, který může třída používat. Úkoly prezentované v tomto návodu zahrnují následující:

- Vytvoření souboru *app.config.*

- Definování oddílu vlastní konfigurace.

- Definování připojovacích řetězců.

- Definování zdrojů dat.

- Přístup ke zdrojům <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> dat pomocí třídy.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto názorného postupu potřebujete:

- Visual Studio Enterprise

- Aplikace Microsoft Access nebo Microsoft Excel poskytují data alespoň pro jednu z testovacích metod.

- Řešení visual studio, který obsahuje testovací projekt.

## <a name="add-an-appconfig-file-to-the-project"></a>Přidání souboru app.config do projektu

1. Pokud váš testovací projekt již obsahuje soubor *app.config,* přejděte do [části Definovat vlastní konfiguraci](#define-a-custom-configuration-section).

2. Klepněte pravým tlačítkem myši na testovací projekt v **Průzkumníku řešení**a pak vyberte **přidat** > **novou položku**.

     Otevře se okno **Přidat novou položku.**

3. Vyberte šablonu **Konfigurační soubor aplikace** a klepněte na **tlačítko Přidat**.

## <a name="define-a-custom-configuration-section"></a>Definování oddílu vlastní konfigurace

Zkontrolujte soubor *app.config.* Obsahuje alespoň deklaraci XML a kořenový prvek.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Přidání oddílu vlastní konfigurace do souboru app.config

1. Kořenový prvek *app.config* by měl být **konfigurační** prvek. Vytvořte element **configSections** v rámci **konfiguračního** prvku. **ConfigSections** by měl být prvním prvkem v souboru *app.config.*

2. V rámci elementu **configSections** vytvořte element **oddílu.**

3. V elementu **section** přidejte `name` volaný atribut `microsoft.visualstudio.testtools`a přiřaďte mu hodnotu . Přidejte další `type` volaný atribut `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions`a přiřaďte mu hodnotu .

Prvek **oddílu** by měl vypadat podobně jako tento:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Název sestavení se musí shodovat s verzí, kterou používáte.

## <a name="define-connection-strings"></a>Definování připojovacích řetězců

Připojovací řetězce definují informace specifické pro zprostředkovatele pro přístup ke zdrojům dat. Připojovací řetězce definované v konfiguračních souborech poskytují opakovaně použitelné informace o poskytovateli dat v celé aplikaci. V této části vytvoříte dva připojovací řetězce, které budou použity zdroji dat, které jsou definovány v části Vlastní konfigurace.

### <a name="to-define-connection-strings"></a>Definování připojovacích řetězců

1. Po **elementu configSections** vytvořte prvek **connectionStrings.**

2. V rámci **connectionStrings** element, vytvořte dva **elementy add.**

3. V prvním **prvku add** vytvořte následující atributy a hodnoty pro připojení k databázi aplikace Microsoft Access:

|Atribut|Hodnoty|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

V druhém prvku **add** vytvořte následující atributy a hodnoty pro připojení k tabulce aplikace Microsoft Excel:

|Atribut|Hodnoty|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**ConnectionStrings** element by měl vypadat podobně jako tento:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definování zdrojů dat

Část zdroje dat obsahuje čtyři atributy, které testovací modul používá k načtení dat ze zdroje dat.

- `name`definuje identitu používanou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> k určení zdroje dat, který má být použit.

- `connectionString`identifikuje připojovací řetězec vytvořený v předchozí části Definovat připojovací řetězce.

- `dataTableName`definuje tabulku nebo list, který obsahuje data, která mají být v testu používána.

- `dataAccessMethod`definuje techniku pro přístup k datovým hodnotám ve zdroji dat.

V této části definujete dva zdroje dat, které se použijí v testování částí.

### <a name="to-define-data-sources"></a>Definování zdrojů dat

1. Po **connectionStrings** element, vytvořte **microsoft.visualstudio.testtools** element. Tato část byla vytvořena v části Definovat vlastní konfiguraci.

2. V rámci prvku **microsoft.visualstudio.testtools** vytvořte element **dataSources.**

3. V rámci **elementu dataSources** vytvořte dva elementy **add.**

4. V prvním **prvku add** vytvořte pro zdroj dat aplikace Microsoft Access následující atributy a hodnoty:

|Atribut|Hodnoty|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

V druhém prvku **add** vytvořte následující atributy a hodnoty pro zdroj dat aplikace Microsoft Excel:

|Atribut|Hodnoty|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

Prvek **microsoft.visualstudio.testtools** by měl vypadat podobně jako tento:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Konečný soubor *app.config* by měl vypadat podobně jako tento:

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

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Vytvoření testování částí, které používá zdroje dat definované v souboru app.config

Nyní, když byl definován soubor *app.config,* vytvoříte test částí, který používá data umístěná ve zdrojích dat, které jsou definovány v souboru *app.config.* V této části:

- Vytvořte zdroje dat nalezené v souboru *app.config.*

- Zdroje dat použijte ve dvou zkušebních metodách, které porovnávají hodnoty v každém zdroji dat.

### <a name="to-create-a-microsoft-access-data-source"></a>Vytvoření zdroje dat aplikace Microsoft Access

1. Vytvořte databázi aplikace Microsoft Access s názvem *testdatasource.accdb*.

2. Vytvořte tabulku a `MyDataTable` pojmenujte ji v *souboru testdatasource.accdb*.

3. Vytvořte dvě `MyDataTable` `Arg1` pole `Arg2` v `Number` pojmenované a pomocí datového typu.

4. Přidejte pět `MyDataTable` entit s `Arg1` následujícími hodnotami pro a `Arg2`, v uvedeném pořadí: (10,50), (3,2), (6,0), (0,8) a (12312,1000).

5. Uložte a zavřete databázi.

6. Změňte připojovací řetězec tak, aby přecšlápne na umístění databáze. Změňte hodnotu `Data Source` tak, aby odrážela umístění databáze.

### <a name="to-create-a-microsoft-excel-data-source"></a>Vytvoření zdroje dat aplikace Microsoft Excel

1. Vytvořte tabulku aplikace Microsoft Excel s názvem *data.xlsx*.

2. Vytvořte list `Sheet1` s názvem, pokud již neexistuje v *souboru data.xlsx*.

3. Vytvořte dvě záhlaví sloupců `Val2` `Sheet1`a pojmenujte je `Val1` a v .

4. Přidejte pět `Sheet1` entit s `Val1` následujícími hodnotami pro a `Val2`, v uvedeném pořadí: (1,1), (2,2), (3,3), (4,4) a (5,0).

5. Uložte a zavřete tabulku.

6. Změňte připojovací řetězec tak, aby ukazoval na umístění tabulky. Změňte hodnotu `dbq` aplikace tak, aby odrážela umístění tabulky.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Vytvoření testování částí pomocí zdrojů dat app.config

1. Přidejte test částí do testovacího projektu.

2. Automaticky generovaný obsah testu částí se nahradí následujícím kódem:

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

3. Prozkoumejte atributy DataSource. Všimněte si názvů nastavení ze souboru *app.config.*

4. Sestavte si řešení a spusťte testy MyTestMethod a MyTestMethod2.

> [!IMPORTANT]
> Nasaďte položky, jako jsou zdroje dat, aby byly přístupné testu v adresáři nasazení.

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Postup: Vytvoření testu částí řízených daty](../test/how-to-create-a-data-driven-unit-test.md)
