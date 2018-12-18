---
title: 'Návod: Použití konfiguračního souboru k definování zdroje dat | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 34
ms.author: gewarren
manager: douge
ms.openlocfilehash: f3dca876e777e8f40773ca42b05fece1c22fe33e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843038"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Návod: Použití konfiguračního souboru k definování zdroje dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak používat zdroj dat definované v souboru app.config pro testování částí. Se dozvíte, jak vytvořit soubor app.config, který definuje zdroje dat, který mohou využívat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> třídy. Úkoly uvedené v tomto návodu zahrnují následující:  
  
-   Vytvoření souboru app.config.  
  
-   Definování vlastního konfiguračního oddílu.  
  
-   Definování připojovacích řetězců.  
  
-   Definování datových zdrojů.  
  
-   Přistupuje k datům zdrojů pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> třídy.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení toho návodu budete potřebovat:  
  
-   Visual Studio Enterprise  
  
-   Aplikace Microsoft Access nebo aplikace Microsoft Excel poskytující data pro alespoň jeden testovací metody.  
  
-   Řešení sady Visual Studio, který obsahuje testovací projekt.  
  
## <a name="create-the-appconfig-file"></a>Vytvoření souboru App.config  
  
#### <a name="to-add-an-appconfig-file-to-the-project"></a>Chcete-li přidat soubor app.config pro projekt  
  
1.  Pokud testovací projekt už obsahuje soubor app.config, přejděte na [definovat vlastní konfigurační oddíl](#DefineCustomConfigurationSection).  
  
2.  Klikněte pravým tlačítkem na projekt testů v **Průzkumníka řešení**, přejděte na **přidat**a potom klikněte na tlačítko **nová položka**.  
  
     **Přidat novou položku** otevře se okno.  
  
3.  Vyberte **konfiguračního souboru aplikace** šablonu a klikněte na tlačítko **přidat**.  
  
##  <a name="DefineCustomConfigurationSection"></a> Definování vlastního konfiguračního oddílu  
 Zkontrolujte v souboru app.config. Obsahuje nejméně deklarace XML a kořenový element.  
  
#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Chcete-li přidat vlastní konfigurační oddíl do souboru app.config  
  
1. Musí být kořenovým prvkem souboru app.config `configuration` elementu. Vytvoření `configSections` element v rámci `configuration` elementu. `configSections` By měl být prvním elementem v souboru app.config.  
  
2. V rámci `configSections` elementu, vytvořit `section` elementu.  
  
3. V `section` prvku, přidejte atribut s názvem `name` a přiřadit jí hodnotu rovnou `microsoft.visualstudio.testtools`. Přidat jiný atribut `type` a přiřaďte ho stejnou hodnotu `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
   `section` Prvek by měl vypadat nějak takto:  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
>  Název sestavení musí odpovídat sestavení Microsoft Visual Studio .NET Framework, kterou používáte. Pokud používáte Visual Studio .NET Framework 3.5, nastavte 9.0.0.0 verzi. Pokud používáte Visual Studio .NET Framework 2.0, nastavte 8.0.0.0 verzi.  
  
## <a name="define-connection-strings"></a>Definujte připojovací řetězce  
 Připojovací řetězce definují určité informace o poskytovateli pro přístup ke zdrojům dat. Připojovací řetězce, které jsou definované v konfiguračních souborech poskytují informace poskytovatele opakovaně použitelné dat v aplikaci. V této části vytvoříte dva připojovací řetězce, které se použijí podle zdroje dat, které jsou definovány v části vlastní konfigurace.  
  
#### <a name="to-define-connection-strings"></a>K definování připojovacích řetězců  
  
1.  Po `configSections` elementu, vytvořit `connectionStrings` elementu.  
  
2.  V rámci `connectionStrings` elementu, pak vytvoříte další dva `add` elementy.  
  
3.  V prvním `add` elementu, vytvořte následující atributy a hodnoty pro připojení k databázi aplikace Microsoft Access:  
  
|Atribut|Hodnoty|  
|---------------|------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 Ve druhém `add` elementu, vytvořte následující atributy a hodnoty pro připojení k Microsoft Excelové tabulce:  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 `connectionStrings` Prvek by měl vypadat nějak takto:  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## <a name="define-data-sources"></a>Definování zdrojů dat  
 Zdroje dat obsahuje čtyři atributy, které se používají modulem test k načtení dat ze zdroje dat.  
  
- `name` definuje identitu používanou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> k určení, která data zdroje používat.  
  
- `connectionString` Určuje připojovací řetězec vytvořený v předchozím oddílu definovat připojovací řetězce.  
  
- `dataTableName` Určuje tabulky nebo listu, obsahující data, která mají v testu používáte.  
  
- `dataAccessMethod` Definuje techniku pro přístup k hodnotám dat ve zdroji dat.  
  
  V této části se nadefinujeme dva zdroje dat pro použití v testu jednotek.  
  
#### <a name="to-define-data-sources"></a>K definování zdroje dat  
  
1.  Po `connectionStrings` elementu, vytvořit `microsoft.visualstudio.testtools` elementu. Tato část byl vytvořen v definovat vlastní konfigurační oddíl.  
  
2.  V rámci `microsoft.visualstudio.testtools` elementu, vytvořit `dataSources` elementu.  
  
3.  V rámci `dataSources` elementu, pak vytvoříte další dva `add` elementy.  
  
4.  V prvním `add` elementu, vytvořte následující atributy a hodnoty pro zdroj dat Microsoft Access:  
  
|Atribut|Hodnoty|  
|---------------|------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 Ve druhém `add` elementu, vytvořte následující atributy a hodnoty pro zdroj dat aplikace Microsoft Excel:  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 `microsoft.visualstudio.testtools` Prvek by měl vypadat nějak takto:  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 Poslední app.config soubor by měl vypadat nějak takto:  
  
```  
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
  
## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Vytvoření testování částí pomocí zdroje dat, které jsou definovány v souboru app.config  
 Teď, když je definována soubor app.config, vytvoříte Jednotkový test, který používá data umístěná v zdroje dat, které jsou definovány v souboru app.config. V této části provedeme následující:  
  
-   Vytvoření zdroje dat nalezen v souboru app.config.  
  
-   Zdroje dat ve dvou testovací metody, které porovnat hodnoty u každého zdroje dat použijte.  
  
#### <a name="to-create-a-microsoft-access-data-source"></a>Chcete-li vytvořit zdroj dat Microsoft Access  
  
1.  Vytvoření databáze Microsoft Access s názvem `testdatasource.accdb`.  
  
2.  Vytvořte tabulku s názvem `MyDataTable` v `testdatasource.accdb`.  
  
3.  Vytvořte dvě pole v `MyDataTable` s názvem `Arg1` a `Arg2` pomocí `Number` datového typu.  
  
4.  Přidat pět entity, které `MyDataTable` s použitím následujících hodnot pro `Arg1` a `Arg2`v uvedeném pořadí: (10,50), (3,2), (6,0) (0,8) a (12312,1000).  
  
5.  Uložte a zavřete databáze.  
  
6.  Změňte připojovací řetězec tak, aby odkazoval na umístění databáze. Změňte hodnotu vlastnosti `Data Source` tak, aby odrážely umístění databáze.  
  
#### <a name="to-create-a-microsoft-excel-data-source"></a>Chcete-li vytvořit zdroj dat aplikace Microsoft Excel  
  
1.  Vytvoření tabulky Microsoft Excel s názvem `data.xlsx`.  
  
2.  Vytvořit tabulku s názvem `Sheet1` Pokud již neexistuje v `data.xlsx`.  
  
3.  Vytvořte dvě záhlaví sloupců a pojmenujte je `Val1` a `Val2` v `Sheet1`.  
  
4.  Přidat pět entity, které `Sheet1` s použitím následujících hodnot pro `Val1` a `Val2`v uvedeném pořadí: (1,1), (2,2) (3,3) (4,4) a (5,0).  
  
5.  Uložte a zavřete tabulky.  
  
6.  Změňte připojovací řetězec tak, aby odkazoval na umístění tabulky. Změňte hodnotu vlastnosti `dbq` tak, aby odrážely umístění tabulky.  
  
#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Vytvoření testu jednotky pomocí souboru app.config zdroje dat  
  
1.  Testování částí přidejte do projektu testů.  
  
     Další informace najdete v tématu [vytváření a spouštění testů jednotek pro existující kód](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173).  
  
2.  Nahraďte obsah automaticky generovaný sady testování částí s následujícím kódem:  
  
    ```  
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
  
3.  Prozkoumejte atributů DataSource. Všimněte si, že názvy nastavení ze souboru app.config.  
  
4.  Sestavte řešení a spuštění testů MyTestMethod a MyTestMethod2.  
  
> [!IMPORTANT]
>  Nasaďte položky jako zdroje dat, takže jsou přístupné pro test v adresáři nasazení.  
  
## <a name="see-also"></a>Viz také  
 [Testování částí kódu](../test/unit-test-your-code.md)   
 [Vytváření a spouštění testů jednotek pro existující kód](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Testování aplikace](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Postupy: Testy částí řízené daty](../test/how-to-create-a-data-driven-unit-test.md)



