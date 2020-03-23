---
title: Kurz testu ui řízeného daty
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ada1f297bbb30fbe636042c87aae42849c1b6b7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595355"
---
# <a name="create-a-data-driven-coded-ui-test"></a>Vytvoření kódu ui řízeného daty

Chcete-li otestovat různé podmínky, můžete spustit testy vícekrát s různými hodnotami parametrů. Data řízené kódované testy ui jsou pohodlný způsob, jak to provést. Ve zdroji dat definujete hodnoty parametrů a každý řádek ve zdroji dat je iteraci kódovaného testu ui. Celkový výsledek testu bude založen na výsledku pro všechny iterace. Například pokud jeden test iterace selže, celkový výsledek testu je selhání.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise
- Kódovaná testovací komponenta ui

## <a name="create-a-test-project"></a>Vytvoření testovacího projektu

Tato ukázka vytvoří kódovaný test ui, který běží v aplikaci Kalkulačka systému Windows. Přidá dvě čísla dohromady a používá kontrolní výraz k ověření, že součet je správný. Dále jsou kontrolní výraz a hodnoty parametrů pro dvě čísla kódovány tak, aby se staly řízenými daty a uloženy v souboru odděleného čárkami (*.csv*).

### <a name="step-1---create-a-coded-ui-test"></a>Krok 1 – vytvoření programového testu ui

1. Vytvořte projekt.

    ![Vytvoření programového testovacího projektu ui](../test/media/cuit_datadriven_.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **Programového testovacího projektu uživatelského nastavení,** je třeba [nainstalovat kódovku testovací součást uživatelského impodařilose](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Zvolte, zda chcete **akce zaznamenat**.

    ![Zvolte záznam akcí](../test/media/cuit_datadriven_generatecodedialog.png)

3. Otevřete aplikaci kalkulačky a začněte nahrávat test.

    ![Záznam akcí](../test/media/cuit_datadriven_cuitbuilder.png)

4. Přidejte 1 plus 2, pozastavte rekordér a vygenerujte testovací metodu. Později nahradíme hodnoty tohoto uživatelského vstupu hodnotami z datového souboru.

    ![Generovat zkušební metodu](../test/media/cuit_datadriven_cuitbuildergencode.png)

    Zavřete tvůrce testů. Metoda se přidá do testu:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       // To generate code for this test, select "Generate Code for Coded UI Test"
       // from the shortcut menu and select one of the menu items.
       this.UIMap.AddNumbers();
   }
   ```

5. Pomocí `AddNumbers()` metody ověřte, zda jsou testy spuštěny. Umístěte kurzor do výše uvedené zkušební metody, otevřete nabídku pravým tlačítkem myši a zvolte **Spustit testy**. (Klávesová zkratka: **Ctrl**+**R**,**T**).

    Výsledek testu, který ukazuje, zda test prošel nebo se nezdařilo se zobrazí v okně **Průzkumníktestů.** Chcete-li otevřít okno Průzkumníka testů, z nabídky **Test** zvolte **Windows** a pak zvolte **Průzkumník a test**.

6. Vzhledem k tomu, že zdroj dat lze také použít pro hodnoty parametrů kontrolního výrazu – které test používá k ověření očekávaných hodnot – přidejme kontrolní výraz k ověření, zda je součet dvou čísel správný. Umístěte kurzor do výše uvedené zkušební metody, otevřete nabídku po kliknutí pravým tlačítkem myši a zvolte **Generovat kód pro programový test ui**a **pak použijte Programový tvůrce testů ui**.

    Namapujte textový ovládací prvek v kalkulačce, která zobrazuje součet.

    ![Mapování textového ovládacího prvku rozhraní](../test/media/cuit_datadriven_addassertion.png)

7. Přidejte kontrolní výraz, který ověřuje, zda je hodnota součtu správná. Zvolte vlastnost **DisplayText** s hodnotou **3** a pak zvolte **Přidat kontrolní výraz**. Použijte **areequal** komparátor a ověřte, zda je srovnávací hodnota **3**.

    ![Konfigurace kontrolního výrazu](../test/media/cuit_datadriven_builderaddassertion2.png)

8. Po konfiguraci kontrolního výrazu znovu vygenerujte kód z tvůrce. Tím se vytvoří nová metoda pro ověření.

    ![Generovat metodu assertion](../test/media/cuit_datadriven_assertiongencode.png)

    Vzhledem `ValidateSum` k tomu, že `AddNumbers` metoda ověřuje výsledky metody, přesuňte ji na konec bloku kódu.

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSum();
   }
   ```

9. Ověřte, zda test `ValidateSum()` běží pomocí metody. Umístěte kurzor do výše uvedené zkušební metody, otevřete nabídku pravým tlačítkem myši a zvolte **Spustit testy**. (Klávesová zkratka: **Ctrl**+**R**,**T**).

     V tomto okamžiku jsou všechny hodnoty parametrů definovány ve svých metodách jako konstanty. Dále vytvoříme sadu dat, aby naše testovací data byla řízena daty.

### <a name="step-2---create-a-data-set"></a>Krok 2 – Vytvoření datové sady

1. Přidejte textový soubor do projektu dataDrivenSample s názvem *data.csv*.

     ![Přidání souboru sektohodnocenou hodnotou čárky do projektu](../test/media/cuit_datadriven_addcsvfile.png)

2. Naplňte soubor *.csv* následujícími daty:

    |Číslo 1|Číslo 2|Součet|
    |-|-|-|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Po přidání dat by měl soubor vypadat takto:

     ![Naplnění souboru .csv daty](../test/media/cuit_datadriven_adddatatocsvfile.png)

3. Je důležité uložit soubor *.csv* pomocí správného kódování. V nabídce **Soubor** zvolte **Upřesnit možnosti uložení** a jako kódování zvolte **Unicode (UTF-8 bez podpisu) – Codepage 65001.**

4. Soubor *.csv* musí být zkopírován do výstupního adresáře nebo test nelze spustit. Zkopírujte okno **Vlastnosti.**

     ![Nasazení souboru CSV](../test/media/cuit_datadriven_deploycsvfile.png)

     Teď, když jsme vytvořili sadu dat, pojďme svázat data s testem.

### <a name="step-3---add-data-source-binding"></a>Krok 3 – přidání vazby zdroje dat

1. Chcete-li vytvořit vazbu `DataSource` zdroj dat, přidejte atribut v rámci existující `[TestMethod]` atribut, který je bezprostředně nad zkušební metody.

    ```csharp
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();
    }
    ```

     Zdroj dat je nyní k dispozici pro použití v této testovací metodě.

    > [!TIP]
    > Ukázky [atributů zdroje dat](#CreateDataDrivenCUIT_QA_DataSourceAttributes) v části Q & A najdete ukázky použití jiných typů zdrojů dat, jako je XML, SQL Express a Excel.

2. Spusťte test.

     Všimněte si, že test probíhá prostřednictvím tří iterací. Důvodem je, že zdroj dat, který byl vázán obsahuje tři řádky dat. Však také zjistíte, že test je stále používá hodnoty konstantní parametr a přidává 1 + 2 se součtem 3 pokaždé.

     Dále nakonfigurujeme test tak, aby používal hodnoty v souboru zdroje dat.

### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>Krok 4 – použití dat v programovém testu ui

1. Přidat `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` do horní části *CodedUITest.cs* souboru:

    ```csharp
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

2. Přidejte `TestContext.DataRow[]` `CodedUITestMethod1()` metodu, která bude používat hodnoty ze zdroje dat. Hodnoty zdroje dat přepíší konstanty přiřazené ovládacím prvkům UIMap pomocí ovládacích prvků `SearchProperties`:

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();
       this.UIMap.UICalculatorWindow.UIItemWindow2.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSumExpectedValues.UIItem3TextDisplayText = TestContext.DataRow["Sum"].ToString();
       this.UIMap.ValidateSum();
    }
    ```

     Chcete-li zjistit, které vyhledávací vlastnosti kódovat data, použijte Editor test kódovaného ui.

    - Otevřete soubor *UIMap.uitest.*

         ![Otevření Programového editoru testů ui](../test/media/cuit_datadriven_opentesteditor.png)

    - Zvolte akci ui a dodržujte odpovídající mapování ovládacího prvku ui. Všimněte si, jak mapování odpovídá kódu, `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`například .

         ![Použití Editoru testů programového rozhraní pro usnadnění používání kódu](../test/media/cuit_datadriven_testeditor.png)

    - V okně **Vlastnosti** otevřete **možnost Hledat vlastnosti**. Vlastnosti hledání **Název** je to, co je manipulováno v kódu pomocí zdroje dat. Například jsou `SearchProperties` přiřazeny hodnoty v prvním sloupci každého `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`řádku dat: . Pro tři iterace tento test změní **název** hodnotu pro vlastnost hledání na 3, pak 5 a nakonec 6.

         ![Použití vlastností vyhledávání k usnadnění kódování](../test/media/cuit_datadriven_searchproperties.png)

3. Uložte řešení.

### <a name="step-5---run-the-data-driven-test"></a>Krok 5 – Spuštění testu řízeného daty

Ověřte, zda je test nyní založen na datech spuštěním testu znovu.

Měli byste vidět test spustit přes tři iterace pomocí hodnot v souboru *.csv.* Ověření by mělo fungovat také a test by měl zobrazit jako předané v Průzkumníku testů.

## <a name="q--a"></a>Otázky a odpovědi

### <a name="what-are-the-data-source-attributes-for-other-data-source-types-such-as-sql-express-or-xml"></a><a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a>Jaké jsou atributy zdroje dat pro jiné typy zdrojů dat, například SQL Express nebo XML?

**A:** Ukázkové řetězce zdrojů dat v následující tabulce můžete použít tak, že je zkopírujete do kódu a naděláte potřebná vlastní nastavení.

**Typy a atributy zdroje dat**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Testovací případ na serveru Team Foundation

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Otázka: Proč nelze upravit kód v souboru UIMap.Designer?

**A:** Všechny změny kódu, které provedete v *UIMapDesigner.cs* souboru, budou přepsány při každém generování kódu pomocí Tvůrce testů ui - coded ui. V této ukázce a ve většině případů změny kódu potřebné k povolení testu použít zdroj dat lze provést do souboru zdrojového kódu testu (to *znamená, že CodedUITest1.cs*).

Pokud je nutné upravit nahranou metodu, musíte ji zkopírovat do *UIMap.cs* souboru a přejmenovat. Soubor *UIMap.cs* lze použít k přepsání metod a vlastností v *souboru UIMapDesigner.cs.* Je nutné odebrat odkaz na původní metodu v souboru Coded *UITest.cs* a nahradit jej názvem název metody.

## <a name="see-also"></a>Viz také

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md)
- [Doporučené postupy pro kódované testy rozhraní](../test/best-practices-for-coded-ui-tests.md)
- [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
