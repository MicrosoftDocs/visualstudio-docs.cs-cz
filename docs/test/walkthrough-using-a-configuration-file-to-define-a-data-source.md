---
title: Použití konfiguračního souboru k definování zdroje dat
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
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776160"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Návod: Použití konfiguračního souboru k definování zdroje dat

Tento návod ukazuje, jak používat zdroj dat definované v *app.config* soubor pro testování částí. Se dozvíte, jak vytvořit *app.config* soubor, který definuje zdroje dat, který mohou využívat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> třídy. Úkoly uvedené v tomto návodu zahrnují následující:

- Vytvoření *app.config* souboru.

- Definování vlastního konfiguračního oddílu.

- Definování připojovacích řetězců.

- Definování datových zdrojů.

- Přistupuje k datům zdrojů pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> třídy.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat:

- Visual Studio Enterprise

- Aplikace Microsoft Access nebo aplikace Microsoft Excel poskytující data pro alespoň jeden testovací metody.

- Řešení sady Visual Studio, který obsahuje testovací projekt.

## <a name="add-an-appconfig-file-to-the-project"></a>Přidejte do projektu soubor app.config

1. Pokud je testovací projekt už *app.config* souboru, přejděte na [definování vlastního konfiguračního oddílu](#define-a-custom-configuration-section).

2. Klikněte pravým tlačítkem na projekt testů v **Průzkumníka řešení**a pak vyberte **přidat** > **nová položka**.

     **Přidat novou položku** otevře se okno.

3. Vyberte **konfiguračního souboru aplikace** šablonu a klikněte na tlačítko **přidat**.

## <a name="define-a-custom-configuration-section"></a>Definování vlastního konfiguračního oddílu

Zkontrolujte *app.config* souboru. Obsahuje nejméně deklarace XML a kořenový element.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Chcete-li přidat vlastní konfigurační oddíl do souboru app.config

1. Kořenový element *app.config* by měl být **konfigurace** elementu. Vytvoření **configSections** element v rámci **konfigurace** elementu. **ConfigSections** by měl být prvním elementem v *app.config* souboru.

2. V rámci **configSections** elementu, vytvořit **části** elementu.

3. V **části** elementu, přidejte atribut s názvem `name` a přiřaďte ho hodnotu `microsoft.visualstudio.testtools`. Přidat jiný atribut `type` a přiřaďte ho hodnotu `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions`.

**Části** prvek by měl vypadat nějak takto:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Název sestavení musí odpovídat verzi, kterou používáte.

## <a name="define-connection-strings"></a>Definujte připojovací řetězce

Připojovací řetězce definují informace specifické pro zprostředkovatele pro přístup ke zdrojům dat. Připojovací řetězce, které jsou definované v konfiguračních souborech poskytují informace poskytovatele opakovaně použitelné dat v aplikaci. V této části vytvoříte dva připojovací řetězce, které se použijí podle zdroje dat, které jsou definovány v části vlastní konfigurace.

### <a name="to-define-connection-strings"></a>K definování připojovacích řetězců

1. Po **configSections** elementu, vytvořit **connectionStrings** elementu.

2. V rámci **connectionStrings** elementu, pak vytvoříte další dva **přidat** elementy.

3. V prvním **přidat** elementu, vytvořte následující atributy a hodnoty pro připojení k databázi aplikace Microsoft Access:

|Atribut|Hodnoty|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

Ve druhém **přidat** elementu, vytvořte následující atributy a hodnoty pro připojení k Microsoft Excelové tabulce:

|Atribut|Hodnoty|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**ConnectionStrings** prvek by měl vypadat nějak takto:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definování zdrojů dat

Zdroje dat obsahuje čtyři atributy, které se používají modulem test k načtení dat ze zdroje dat.

- `name` definuje identitu používanou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> k určení, která data zdroje používat.

- `connectionString` Určuje připojovací řetězec vytvořený v předchozím oddílu definovat připojovací řetězce.

- `dataTableName` Určuje tabulky nebo listu, obsahující data, která mají v testu používáte.

- `dataAccessMethod` Definuje techniku pro přístup k hodnotám dat ve zdroji dat.

V této části budete nadefinujeme dva zdroje dat pro použití v testu jednotek.

### <a name="to-define-data-sources"></a>K definování zdroje dat

1. Po **connectionStrings** elementu, vytvořit **microsoft.visualstudio.testtools** elementu. Tato část byl vytvořen v definovat vlastní konfigurační oddíl.

2. V rámci **microsoft.visualstudio.testtools** elementu, vytvořit **zdroje dat** elementu.

3. V rámci **zdroje dat** elementu, pak vytvoříte další dva **přidat** elementy.

4. V prvním **přidat** elementu, vytvořte následující atributy a hodnoty pro zdroj dat Microsoft Access:

|Atribut|Hodnoty|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

Ve druhém **přidat** elementu, vytvořte následující atributy a hodnoty pro zdroj dat aplikace Microsoft Excel:

|Atribut|Hodnoty|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

**Microsoft.visualstudio.testtools** prvek by měl vypadat nějak takto:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Finální *app.config* soubor by měl vypadat nějak takto:

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

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Vytvoření testování částí, která používá zdroje dat, které jsou definovány v souboru app.config

Teď, když *app.config* definoval souboru, bude vytvoření testování částí, která používá data umístěná v zdroje dat, které jsou definovány v *app.config* souboru. V této části provedeme následující:

- Vytvoření datového zdroje najdete v *app.config* souboru.

- Zdroje dat ve dvou testovací metody, které porovnat hodnoty u každého zdroje dat použijte.

### <a name="to-create-a-microsoft-access-data-source"></a>Chcete-li vytvořit zdroj dat Microsoft Access

1. Vytvoření databáze Microsoft Access s názvem *testdatasource.accdb*.

2. Vytvořte tabulku s názvem `MyDataTable` v *testdatasource.accdb*.

3. Vytvořte dvě pole v `MyDataTable` s názvem `Arg1` a `Arg2` pomocí `Number` datového typu.

4. Přidat pět entity, které `MyDataTable` s použitím následujících hodnot pro `Arg1` a `Arg2`v uvedeném pořadí: (10,50), (3,2), (6,0) (0,8) a (12312,1000).

5. Uložte a zavřete databáze.

6. Změňte připojovací řetězec tak, aby odkazoval na umístění databáze. Změňte hodnotu vlastnosti `Data Source` tak, aby odrážely umístění databáze.

### <a name="to-create-a-microsoft-excel-data-source"></a>Chcete-li vytvořit zdroj dat aplikace Microsoft Excel

1. Vytvoření tabulky Microsoft Excel s názvem *data.xlsx*.

2. Vytvořit tabulku s názvem `Sheet1` Pokud již neexistuje v *data.xlsx*.

3. Vytvořte dvě záhlaví sloupců a pojmenujte je `Val1` a `Val2` v `Sheet1`.

4. Přidat pět entity, které `Sheet1` s použitím následujících hodnot pro `Val1` a `Val2`v uvedeném pořadí: (1,1), (2,2) (3,3) (4,4) a (5,0).

5. Uložte a zavřete tabulky.

6. Změňte připojovací řetězec tak, aby odkazoval na umístění tabulky. Změňte hodnotu vlastnosti `dbq` tak, aby odrážely umístění tabulky.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Vytvoření testu jednotky pomocí souboru app.config zdroje dat

1. Testování částí přidejte do projektu testů.

2. Nahraďte obsah automaticky generovaný sady testování částí s následujícím kódem:

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

3. Prozkoumejte atributů DataSource. Všimněte si, že názvy v nastavení *app.config* souboru.

4. Sestavte řešení a spuštění testů MyTestMethod a MyTestMethod2.

> [!IMPORTANT]
> Nasaďte položky jako zdroje dat, takže jsou přístupné pro test v adresáři nasazení.

## <a name="see-also"></a>Viz také:

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Postupy: Vytvoření testu jednotek řízené daty](../test/how-to-create-a-data-driven-unit-test.md)
