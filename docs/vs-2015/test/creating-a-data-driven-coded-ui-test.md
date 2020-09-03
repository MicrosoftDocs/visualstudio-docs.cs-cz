---
title: Vytvoření programového testu uživatelského rozhraní řízeného daty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
ms.assetid: 5838f02d-001f-49ce-adce-c9ea1afaec2f
caps.latest.revision: 58
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1db35e1eb98ad23a4414a48389092a3b05485527
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851855"
---
# <a name="creating-a-data-driven-coded-ui-test"></a>Vytvoření datově řízeného programového testu UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li testovat různé podmínky, můžete testy spustit několikrát s různými hodnotami parametrů. To je pohodlný způsob, jak to udělat pomocí datových testů řízených daty. Hodnoty parametrů definujete ve zdroji dat a každý řádek ve zdroji dat je iterací kódovaného testu uživatelského rozhraní. Celkový výsledek testu bude založen na výsledku pro všechny iterace. Například pokud jedna iterace testu selže, celkový výsledek testu je selhání.

 **Požadavky**

- Visual Studio Enterprise

## <a name="create-a-data-driven-coded-ui-test"></a>Vytvořit datově řízený programový test uživatelského rozhraní
 Tato ukázka vytvoří programový test uživatelského rozhraní, který je spuštěn v aplikaci kalkulačky Windows. Přidá dvě čísla dohromady a pomocí kontrolního výrazu ověří, zda je součet správný. Dále je kontrolní výraz a hodnoty parametrů pro dvě čísla kódovány tak, aby se staly řízenými daty a uloženy v souboru hodnot oddělených čárkami (. csv).

#### <a name="step-1---create-a-coded-ui-test"></a>Krok 1 – vytvoření kódovaného testu uživatelského rozhraní

1. Vytvořte projekt.

     ![Vytvoření projektu programového testu uživatelského rozhraní](../test/media/cuit-datadriven.png "CUIT_dataDriven_")

2. Vyberte, chcete-li zaznamenávat akce.

     ![Vyberte, chcete-li zaznamenávat akce](../test/media/cuit-datadriven-generatecodedialog.png "CUIT_dataDriven_GenerateCodeDialog")

3. Otevřete aplikaci kalkulačky a začněte nahrávat test.

     ![Zaznamenat akce](../test/media/cuit-datadriven-cuitbuilder.png "CUIT_dataDriven_CUITBuilder")

4. Přidejte 1 plus 2, pozastavte záznam a vygenerujte testovací metodu. Později nahradíme hodnoty tohoto uživatelského vstupu hodnotami z datového souboru.

     ![Generovat testovací metodu](../test/media/cuit-datadriven-cuitbuildergencode.png "CUIT_dataDriven_CUITBuilderGenCode")

     Zavřete nástroj test Builder. Metoda je přidána do testu:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();

    }
    ```

5. Použijte `AddNumbers()` metodu k ověření, zda je test spuštěn. Umístěte kurzor do výše uvedené metody testu, otevřete kontextovou nabídku a vyberte možnost **Spustit testy**. (Klávesová zkratka: CTRL + R, T).

     Výsledek testu, který ukazuje, zda byl test úspěšný nebo neúspěšný, se zobrazí v okně Průzkumník testů. Chcete-li otevřít okno Průzkumník testů, v nabídce **test** zvolte možnost **okna** a pak zvolte možnost **Průzkumník testů**.

6. Vzhledem k tomu, že zdroj dat je možné použít také pro hodnoty parametru kontrolního výrazu, které jsou používány testem k ověření očekávaných hodnot – přidáváme kontrolní výraz pro ověření, že součet dvou čísel je správný. Umístěte kurzor do zkušební metody zobrazené výše, otevřete kontextovou nabídku a zvolte příkaz **generovat kód pro programový test uživatelského rozhraní**a pak **použijte Tvůrce programového testu uživatelského rozhraní**.

     Namapujte ovládací prvek text v kalkulačce, který zobrazuje součet.

     ![Mapování ovládacího prvku text uživatelského rozhraní](../test/media/cuit-datadriven-addassertion.png "CUIT_dataDriven_AddAssertion")

7. Přidejte kontrolní výraz, který ověří, že hodnota součtu je správná. Zvolte vlastnost **zobrazenýtext** , která má hodnotu **3** a pak zvolte **Přidat kontrolní výraz**. Použijte **AreEqual** komparátor a ověřte, zda je hodnota porovnání **3**.

     ![Konfigurace kontrolního výrazu](../test/media/cuit-datadriven-builderaddassertion2.png "CUIT_dataDriven_BuilderAddAssertion2")

8. Po nakonfigurování kontrolního výrazu znovu vygenerujte kód z tvůrce. Tím se vytvoří nová metoda pro ověření.

     ![Generování metody kontrolního výrazu](../test/media/cuit-datadriven-assertiongencode.png "CUIT_dataDriven_AssertionGenCode")

     Vzhledem k tomu `ValidateSum` , že metoda ověřuje výsledky `AddNumbers` metody, přesuňte ji do dolní části bloku kódu.

    ```csharp
    public void CodedUITestMethod1()
    {

        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();

    }
    ```

9. Ověřte, zda se test spouští pomocí `ValidateSum()` metody. Umístěte kurzor do výše uvedené metody testu, otevřete kontextovou nabídku a vyberte možnost **Spustit testy**. (Klávesová zkratka: CTRL + R, T).

     V tomto okamžiku jsou všechny hodnoty parametrů definovány ve svých metodách jako konstanty. Teď vytvoříme datovou sadu, která bude mít na test řízená data.

#### <a name="step-2---create-a-data-set"></a>Krok 2 – Vytvoření sady dat

1. Přidejte textový soubor do projektu dataDrivenSample s názvem `data.csv` .

     ![Přidat do projektu soubor hodnot oddělených čárkou](../test/media/cuit-datadriven-addcsvfile.png "CUIT_dataDriven_AddCSVFile")

2. Naplňte soubor. csv následujícími daty:

    |Num1|Num2|Součet|
    |----------|----------|---------|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Po přidání dat by se měl soubor zobrazit jako následující:

     ![Naplňte. Soubor CSV s daty](../test/media/cuit-datadriven-adddatatocsvfile.png "CUIT_dataDriven_AddDataToCSVFile")

3. Je důležité uložit soubor. csv pomocí správného kódování. V nabídce **soubor** vyberte možnost **Upřesnit možnosti uložení** a jako kódování vyberte **Unicode (UTF-8 bez signatur) – codepage 65001** .

4. Soubor. CSV musí být zkopírován do výstupního adresáře nebo nelze spustit test. Ke zkopírování použijte okno Vlastnosti.

     ![Nasaďte. Soubor CSV](../test/media/cuit-datadriven-deploycsvfile.png "CUIT_dataDriven_DeployCSVFile")

     Teď, když máme datovou sadu vytvořenou, můžeme navazovat data na test.

#### <a name="step-3--add-data-source-binding"></a>Krok 3 – přidání vazby zdroje dat

1. Chcete-li vytvořit vazby na zdroj dat, přidejte `DataSource` atribut v rámci existujícího `[TestMethod]` atributu, který je bezprostředně nad zkušební metodou.

    ```
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {

        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();

    }

    ```

     Zdroj dat je nyní k dispozici pro použití v rámci této testovací metody.

    > [!TIP]
    > Příklady použití jiných typů zdrojů dat, jako jsou XML, SQL Express a Excel, najdete v části [ukázky atributů zdroje dat](#CreateDataDrivenCUIT_QA_DataSourceAttributes) v tématu Q & A.

2. Spusťte test.

     Všimněte si, že test běží po třech iteracích. Důvodem je skutečnost, že zdroj dat, který byl svázán, obsahuje tři řádky dat. Nicméně také všimnete, že test stále používá hodnoty parametrů konstant a přidává 1 + 2 se součtem 3 pokaždé.

     Dále nakonfigurujeme test tak, aby používal hodnoty v souboru zdroje dat.

#### <a name="step-4--use-the-data-in-the-coded-ui-test"></a>Krok 4 – použití dat v programovém testu UI

1. Přidejte `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` na začátek souboru CodedUITest.cs:

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

2. Přidejte `TestContext.DataRow[]` do `CodedUITestMethod1()` metody, která bude uplatňovat hodnoty ze zdroje dat. Hodnoty zdrojů dat přepíšou konstanty přiřazené k ovládacím prvkům UIMap pomocí ovládacích prvků `SearchProperties` :

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

     Chcete-li zjistit, které vlastnosti vyhledávání mají data do kódu, použijte Editor programového testu UI.

    - Otevřete soubor UIMap. UITest.

         ![Otevřít Editor programového testu UI](../test/media/cuit-datadriven-opentesteditor.png "CUIT_dataDriven_OpenTestEditor")

    - Vyberte akci uživatelského rozhraní a sledujte odpovídající mapování ovládacího prvku uživatelského rozhraní. Všimněte si, jak mapování odpovídá kódu, například `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button` .

         ![Použití editoru programového testu UI pro pomoc s kódem](../test/media/cuit-datadriven-testeditor.png "CUIT_dataDriven_TestEditor")

    - V okně Vlastnosti otevřete **Vlastnosti hledání**. Hodnota **název** vlastnosti hledání je to, co je v kódu manipulováno pomocí zdroje dat. Například `SearchProperties` přiřadíte hodnoty v prvním sloupci každého řádku dat: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();` . Pro tři iterace tento test změní hodnotu **název** vlastnosti hledání na 3, 5 a nakonec 6.

         ![Použití vlastností hledání k usnadnění při kódování](../test/media/cuit-datadriven-searchproperties.png "CUIT_dataDriven_SearchProperties")

3. Uložte řešení.

#### <a name="step-5--run-the-data-driven-test"></a>Krok 5 – spuštění testu řízeného daty

1. Ověřte, zda je test nyní založen na datech pomocí opětovného spuštění testu.

    Měli byste vidět testovací běh prostřednictvím tří iterací pomocí hodnot v souboru. csv. Ověřování by mělo fungovat taky a test by měl být v Průzkumníku testů zobrazený jako úspěšný.

   **Doprovodné materiály**

   Další informace naleznete v tématu [testování pro průběžné doručování pomocí sady Visual studio 2012 – Kapitola 2: testování částí: testování vnitřních](https://msdn.microsoft.com/library/jj159340.aspx) a [testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 5: automatizace systémových testů](https://msdn.microsoft.com/library/jj159335.aspx)

## <a name="q--a"></a>Otázky a odpovědi

### <a name="what-are-the-data-source-attributes-for-other-data-source-types-such-as-sql-express-or-xml"></a><a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a> Jaké jsou atributy zdroje dat pro jiné typy zdrojů dat, jako je například SQL Express nebo XML?
 Pomocí ukázkových řetězců zdroje dat v následující tabulce můžete zkopírovat je do kódu a provést potřebné vlastní nastavení.

 **Typy a atributy zdroje dat**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Testovací případ v Team Foundation Server

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-can-i-use-data-driven-tests-on-my-windows-phone-app"></a>Otázka: mohu na aplikaci Windows Phone použít testy řízené daty?
 **Odpověď:** Ano. Programové testy UI založené na datech pro Windows Phone jsou definovány pomocí atributu DataRow v testovací metodě. V následujícím příkladu x a y používají hodnoty 1 a 2 pro první iteraci a-1 a-2 pro druhou iteraci testu.

```
[DataRow(1, 2, DisplayName = "Add positive numbers")]
[DataRow(-1, -2, DisplayName = "Add negative numbers")]
[TestMethod]
public void DataDrivingDemo_MyTestMethod(int x, int y)

```

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Otázka: Proč nemůžu změnit kód v souboru UIMap. Designer?
 **A:** Všechny změny kódu, které provedete v souboru UIMapDesigner.cs, budou přepsány pokaždé, když generujete kód pomocí Tvůrce programového testu uživatelského rozhraní UIMap. V této ukázce a ve většině případů změny kódu potřebné k povolení testu použít zdroj dat lze provést v souboru zdrojového kódu testu (tj. CodedUITest1.cs).

 Pokud je třeba změnit zaznamenanou metodu, musíte ji zkopírovat do souboru UIMap.cs a přejmenovat ji. Soubor UIMap.cs lze použít k přepsání metod a vlastností v souboru UIMapDesigner.cs. Je třeba odebrat odkaz na původní metodu v kódovaném souboru UITest.cs a nahradit ji názvem přejmenované metody.

## <a name="see-also"></a>Viz také

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytváření programových testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Doporučené postupy pro programové testy UI](../test/best-practices-for-coded-ui-tests.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
