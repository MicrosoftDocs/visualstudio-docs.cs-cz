---
title: Vytvoření datově řízeného programového testu UI | Dokumentace Microsoftu
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
- coded UI tests, data-driven
ms.assetid: 5838f02d-001f-49ce-adce-c9ea1afaec2f
caps.latest.revision: 58
ms.author: gewarren
manager: douge
ms.openlocfilehash: d3674d6ccbda89a2a3ee1de551587ba034ba51c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932621"
---
# <a name="creating-a-data-driven-coded-ui-test"></a>Vytvoření datově řízeného programového testu UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K testování různých podmínek, můžete spustit testy několikrát s různými hodnotami parametrů. S daty kódované UI testy jsou pohodlný způsob, jak to provést. Můžete definovat hodnoty parametrů ve zdroji dat a každý řádek ve zdroji dat je iteraci programový test uživatelského rozhraní. Celkový výsledek testu budou založeny na výsledek pro všechny iterace. Například pokud jedna iteraci testu nezdaří, celkový výsledek testu je selhání.  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
## <a name="create-a-data-driven-coded-ui-test"></a>Vytvoření datově řízeného programového testu UI  
 Tato ukázka vytvoří programový test uživatelského rozhraní, která běží na Windows Kalkulačka aplikace. Sečte dvě čísla a používá kontrolní výraz k ověření, že součet je správný. V dalším kroku kontrolního výrazu a hodnoty parametrů pro dvě čísla jsou kódované stane s daty a uložené v souboru hodnot oddělených čárkami (CSV).  
  
#### <a name="step-1---create-a-coded-ui-test"></a>Krok 1: vytvoření programového testu uživatelského rozhraní  
  
1.  Vytvoření projektu.  
  
     ![Vytvořit projekt programového testu UI](../test/media/cuit-datadriven.png "CUIT_dataDriven_")  
  
2.  Zvolte pro záznam akce.  
  
     ![Zvolte pro záznam akce](../test/media/cuit-datadriven-generatecodedialog.png "CUIT_dataDriven_GenerateCodeDialog")  
  
3.  Otevřete aplikaci kalkulačky a spusťte záznam testu.  
  
     ![Záznam akcí](../test/media/cuit-datadriven-cuitbuilder.png "CUIT_dataDriven_CUITBuilder")  
  
4.  Přidat 1 a 2, pozastavit záznam a generovat zkušební metody. Později budete nahradíme hodnoty tento uživatelský vstup s hodnotami z datového souboru.  
  
     ![Testovací metoda Genetate](../test/media/cuit-datadriven-cuitbuildergencode.png "CUIT_dataDriven_CUITBuilderGenCode")  
  
     Zavřete Tvůrce testu. Metoda je přidána do testu:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
  
    }  
    ```  
  
5.  Použití `AddNumbers()` metodu k ověření, že test běží. Umístěte kurzor na slovo v testovací metodě uvedené výše, otevřete kontextovou nabídku a zvolte **spustit testy**. (Klávesová zkratka: Ctrl + R, T).  
  
     V okně Průzkumníka testů se zobrazí výsledek testu, který ukazuje-li test úspěšný nebo neúspěšný. Otevření okna Průzkumníka testů z **testovací** nabídce zvolte **Windows** a klikněte na tlačítko **Průzkumník testů**.  
  
6.  Vzhledem k tomu, že zdroje dat lze také hodnoty parametrů kontrolní výraz – které jsou používány test ověření očekávané hodnoty – můžeme přidat kontrolní výraz se ověřit správnost součet dvou čísel. Umístěte kurzor na slovo v testovací metodě uvedené výše, otevřete kontextovou nabídku a zvolte **generovat kód pro programový Test uživatelského rozhraní**a potom **použití Tvůrce programového testu UI**.  
  
     Mapování ovládacího prvku text v kalkulačce zobrazující součet.  
  
     ![Mapování ovládacího prvku uživatelského rozhraní text](../test/media/cuit-datadriven-addassertion.png "CUIT_dataDriven_AddAssertion")  
  
7.  Přidáte kontrolní výraz, který ověří správnost hodnotu Součet. Zvolte **ZobrazenýText** vlastnost, která má hodnotu **3** a klikněte na tlačítko **přidat kontrolní výraz**. Použití **AreEqual** Komparátor a ověřte, zda je hodnota porovnání **3**.  
  
     ![Konfigurovat výraz](../test/media/cuit-datadriven-builderaddassertion2.png "CUIT_dataDriven_BuilderAddAssertion2")  
  
8.  Po dokončení konfigurace kontrolního výrazu, generování kódu z Tvůrce znovu. Tím se vytvoří novou metodu pro ověření.  
  
     ![Vytvořit metodu kontrolního výrazu](../test/media/cuit-datadriven-assertiongencode.png "CUIT_dataDriven_AssertionGenCode")  
  
     Protože `ValidateSum` metoda ověří výsledky `AddNumbers` metoda, jej přesunout na konec bloku kódu.  
  
    ```csharp  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
    ```  
  
9. Ověřte, že test běží za použití `ValidateSum()` metody. Umístěte kurzor na slovo v testovací metodě uvedené výše, otevřete kontextovou nabídku a zvolte **spustit testy**. (Klávesnice zkratka: Ctrl + R, T).  
  
     V tomto okamžiku všechny hodnoty parametrů jsou definovány v jejich metod jako konstanty. V dalším kroku vytvoříte datové sady, aby naše testovací řízené daty.  
  
#### <a name="step-2---create-a-data-set"></a>Krok 2: vytvoření datové sady  
  
1.  Přidání textového souboru s názvem projektu dataDrivenSample `data.csv`.  
  
     ![Přidejte do projektu soubor hodnota oddělených čárkami](../test/media/cuit-datadriven-addcsvfile.png "CUIT_dataDriven_AddCSVFile")  
  
2.  Naplnění souboru .csv s následujícími údaji:  
  
    |Num1|Num2|Součet|  
    |----------|----------|---------|  
    |3|4|7|  
    |5|6|11|  
    |6|8|14|  
  
     Po přidání data, soubor by měl vypadat takto:  
  
     ![Naplnění. Soubor CSV s daty](../test/media/cuit-datadriven-adddatatocsvfile.png "CUIT_dataDriven_AddDataToCSVFile")  
  
3.  Je důležité k uložení souboru CSV pomocí správné kódování. Na **souboru** nabídce zvolte **pokročilé nastavení uložení** a zvolte **kódování Unicode (UTF-8 bez podpisu) – znaková stránka 65001** jako kódování.  
  
4.  Soubor .csv musí být zkopírován do výstupního adresáře nebo testu nelze spustit. Použijte okno Vlastnosti ho zkopírovat.  
  
     ![Nasazení. Soubor CSV](../test/media/cuit-datadriven-deploycsvfile.png "CUIT_dataDriven_DeployCSVFile")  
  
     Když teď máme sadu dat vytvořili, Pojďme vytvořit vazbu mezi dat do testu.  
  
#### <a name="step-3--add-data-source-binding"></a>Krok 3 – Přidání datového zdroje vazby  
  
1.  K vytvoření vazby zdroje dat, přidejte `DataSource` atribut do existujícího `[TestMethod]` atribut, který je hned nad testovací metody.  
  
    ```  
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
  
    ```  
  
     Zdroj dat je teď k dispozici pro použití v této zkušební metodě.  
  
    > [!TIP]
    >  Zobrazit [ukázky atribut zdroje dat](#CreateDataDrivenCUIT_QA_DataSourceAttributes) v Q & části ukázky použití jiných typů zdrojů dat, jako jsou XML, SQL Express a Excel.  
  
2.  Spusťte test.  
  
     Všimněte si, že test běží až tři iterace. Je to proto tří řádků dat obsahuje zdroj dat, která byla vázána. Ale také si povšimněte, že test se pořád používá hodnoty parametrů konstantní a přidává 1 + 2 s součet 3 pokaždé, když.  
  
     V dalším kroku testu, aby použil hodnoty v souboru zdroje dat nakonfigurujeme.  
  
#### <a name="step-4--use-the-data-in-the-coded-ui-test"></a>Krok 4 – použití dat v programovém testu uživatelského rozhraní  
  
1.  Přidat `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` do horní části souboru CodedUITest.cs:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text.RegularExpressions;  
    using System.Windows.Input;  
    using System.Windows.Forms;  
    using System.Drawing;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
    ```  
  
2.  Přidat `TestContext.DataRow[]` v `CodedUITestMethod1()` metodu, která použije hodnoty ze zdroje dat. Hodnoty zdroje dat přepsat konstanty přiřazené k ovládacím prvkům UIMap pomocí ovládacích prvků `SearchProperties`:  
  
    ```  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();this.UIMap.UICalculatorWindow.UIItemWindow21.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSumExpectedValues.UIItem2TextDisplayText = TestContext.DataRow["Sum"].ToString();  
        this.UIMap.ValidateSum();  
  
    }  
    ```  
  
     Chcete-li zjistit vlastnosti vyhledávání, které chcete data na kódu, použijte Editor programového testu uživatelského rozhraní.  
  
    -   Otevření souboru UIMap.uitest.  
  
         ![Otevřít editoru programového testu UI](../test/media/cuit-datadriven-opentesteditor.png "CUIT_dataDriven_OpenTestEditor")  
  
    -   Zvolte akce uživatelského rozhraní a sledovat odpovídající mapování ovládacích prvků uživatelského rozhraní. Všimněte si, jak mapování odpovídá kódu, například `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`.  
  
         ![Pomocí editoru programového testu uživatelského rozhraní pro účely pomoci s kódem](../test/media/cuit-datadriven-testeditor.png "CUIT_dataDriven_TestEditor")  
  
    -   V okně Vlastnosti otevřete **vlastnosti hledání**. Vlastnosti hledání **název** co je právě zpracováván v kódu pomocí zdroje dat je hodnota. Například `SearchProperties` jsou přiřazeny hodnoty v prvním sloupci každý řádek dat: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. Pro tři iterace, tento test změní **název** hodnotu pro vlastnost vyhledávání na 3, pak 5 a nakonec 6.  
  
         ![Pomocí vlastnosti hledání pomoci při psaní kódu](../test/media/cuit-datadriven-searchproperties.png "CUIT_dataDriven_SearchProperties")  
  
3.  Uložte řešení.  
  
#### <a name="step-5--run-the-data-driven-test"></a>Krok 5 – spustit test s daty  
  
1. Ověřte, že test nyní řízené daty opětovným spuštěním testu.  
  
    Měli byste vidět testovacího běhu až tři iterace pomocí hodnot v souboru .csv. Ověření by měl pracovat tak dobře, a zobrazit testu jako úspěšný v aplikaci Test Explorer.  
  
   **Pokyny**  
  
   Další informace najdete v tématu [testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188) a [testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 5: Automatizace systémových testů](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
## <a name="q--a"></a>Dotazy a odpovědi  
  
###  <a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a> Co jsou atributy zdroje dat pro další typy zdrojů dat, jako je například SQL Express nebo XML?  
 Ukázka řetězce zdrojů dat v následující tabulce můžete použít zkopírováním do vašeho kódu a provedením nezbytných úpravách.  
  
 **Typy zdrojů dat a atributy**  
  
-   SDÍLENÝ SVAZEK CLUSTERU  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`  
  
-   Excel  
  
     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`  
  
-   Testovací případ v Team Foundation Server  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`  
  
-   XML  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`  
  
-   SQL Express  
  
     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`  
  
### <a name="q-can-i-use-data-driven-tests-on-my-windows-phone-app"></a>Otázka: je datově řízené testy použít v aplikaci Windows Phone  
 **Odpověď:** Ano. S daty programové testy uživatelského rozhraní pro Windows Phone jsou definovány pomocí atributu DataRow v testovací metodě. V následujícím příkladu, x a y pomocí hodnoty 1 a 2 pro první iterace a -1 -2 pro druhý iteraci tohoto testu.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Otázka: Proč nelze upravit kód v souboru UIMap.Designer?  
 **Odpověď:** změny kódu v souboru UIMapDesigner.cs bude přepsán při každém vytvoření kódu pomocí UIMap – Tvůrce programového testu uživatelského rozhraní. V této ukázce a ve většině případů můžete provést změny kódu potřebná k povolení testu budou používat zdroj dat k souboru zdrojového kódu testu (CodedUITest1.cs).  
  
 Pokud je třeba změnit zaznamenanou metodu, musíte ji zkopírovat do souboru UIMap.cs a přejmenovat ji. Soubor UIMap.cs lze použít k přepsání metod a vlastností v souboru UIMapDesigner.cs. Je třeba odebrat odkaz na původní metodu v kódovaném souboru UITest.cs a nahradit ji názvem přejmenované metody.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Osvědčené postupy pro programové testy UI](../test/best-practices-for-coded-ui-tests.md)   
 [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



