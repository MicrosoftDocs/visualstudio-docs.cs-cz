---
title: Anatomie programového testu UI
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7100c6bb5c1dfb4c7d336ec110cf532f1f998d4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591200"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomie kódovaného testu ui

Při vytváření programového testu ui v projektu test kódovaného ui, jsou přidány několik souborů do řešení. Tento článek obsahuje informace o souborech.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Obsah kódovaného testu ui

Při vytváření test umítaného uživatelského **rozhraní, programové** uživatelské rozhraní Test Builder vytvoří mapu testovacího uživatelského rozhraní a také testovací metody, parametry a kontrolní výrazy pro všechny testy. Také vytvoří soubor třídy pro každý test.

|File|Obsah|Upravitelné?|
|-|-|-|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Oddíl Prohlášení](#UIMapDesignerFile)<br /><br /> [Třída UIMap](#UIMapClass) (částečná, automaticky generovaná)<br /><br /> [Metody](#UIMapMethods)<br /><br /> [Vlastnosti](#UIMapProperties)|Ne|
|[UIMap.cs](#UIMapCS)|[Třída UIMap](#UIMapCS) (částečná)|Ano|
|[CodedUITest1.cs](#CodedUITestCS)|[Třída CodedUITest1](#CodedUITestCS)<br /><br /> [Metody](#CodedUITestMethods)<br /><br /> [Vlastnosti](#CodedUITestProperties)|Ano|
|[UIMap.uitest](#UIMapuitest)|Mapování XML v rozhraní pro test.|Ne|

### <a name="uimapdesignercs"></a><a name="UIMapDesignerFile"></a>UIMap.Designer.cs
Tento soubor obsahuje kód, který je automaticky vytvořen **tvůrcem testovaného ui při** vytvoření testu. Tento soubor je znovu vytvořen při každé změně testu, takže se nejedná o soubor, ve kterém můžete přidat nebo upravit kód.

#### <a name="declarations-section"></a>Oddíl Prohlášení
Tato část obsahuje následující deklarace pro uzp.

```csharp
using System;
using System.CodeDom.Compiler;
using System.Collections.Generic;
using System.Drawing;
using System.Text.RegularExpressions;
using System.Windows.Input;
using Microsoft.VisualStudio.TestTools.UITest.Extension;
using Microsoft.VisualStudio.TestTools.UITesting;
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;
using MouseButtons = System.Windows.Forms.MouseButtons;
```

Obor <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> názvů je součástí uživatelského rozhraní systému Windows. U uživatelského uživatelského uživatelského prostoru <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>webové stránky by byl obor názvů ; v uživatelském prostředí Programu Windows Presentation <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>Foundation by byl obor názvů .

#### <a name="uimap-class"></a><a name="UIMapClass"></a>Třída UIMap
Další část souboru je [třída UIMap.](/previous-versions/dd580454(v=vs.140))

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Kód třídy začíná <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> atributem, který je použit pro třídu, která je deklarována jako částečná třída. Všimněte si, že atribut je také použit a všechny třídy v tomto souboru. Druhý soubor, který může obsahovat více kódu pro tuto třídu je *UIMap.cs*, který je popsán později.

Generovaná `UIMap` třída obsahuje kód pro každou metodu, která byla zadána při zaznamenání testu.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

Tato část [Třídy UIMap](/previous-versions/dd580454(v=vs.140)) také obsahuje generovaný kód pro každou vlastnost, která je vyžadována metodami.

```csharp
public virtual LaunchCalculatorParams LaunchCalculatorParams
public virtual AddItemsParams AddItemsParams
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues
public virtual CalculateItemsParams CalculateItemsParams
public virtual VerifyMathAppTotalExpectedValues
    VerifyMathAppTotalExpectedValues
public UIStartMenuWindow UIStartMenuWindow
public UIRunWindow UIRunWindow
public UICalculatorWindow UICalculatorWindow
public UIStartWindow UIStartWindow
public UIMathApplicationWindow UIMathApplicationWindow
```

##### <a name="uimap-methods"></a><a name="UIMapMethods"></a>Metody UIMap
Každá metoda má strukturu, `AddItems()` která se podobá metodě. To je podrobněji vysvětleno pod kódem, který je prezentován společně s konce řádků pro zvýšení jasnosti.

```csharp
/// <summary>
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.
/// </summary>
public void AddItems()
{
    #region Variable Declarations
    WinControl uICalculatorDialog =
        this.UICalculatorWindow.UICalculatorDialog;
    WinEdit uIItemEdit =
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;
    #endregion

    // Type '{NumPad7}' in 'Calculator' Dialog
    Keyboard.SendKeys(uICalculatorDialog,
        this.AddItemsParams.UICalculatorDialogSendKeys,
        ModifierKeys.None);

    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    Keyboard.SendKeys(uIItemEdit,
        this.AddItemsParams.UIItemEditSendKeys,
        ModifierKeys.None);
}
```

Souhrnný komentář pro každou definici metody říká, která třída má být pro hodnoty parametrů pro tuto metodu použít. V tomto případě je `AddItemsParams` třída, která je definována dále v *souboru UIMap.cs* a která `AddItemsParams` je také typ hodnoty, která je vrácena vlastností.

V horní části kódu metody `Variable Declarations` je oblast, která definuje místní proměnné pro objekty ui, které jsou používány metodou.

V této `UIItemWindow` metodě `UIItemEdit` jsou oba a vlastnosti, které jsou přístupné pomocí `UICalculatorWindow` třídy, která je definována dále v *souboru UIMap.cs.*

Další jsou řádky, které odesílají text z klávesnice `AddItemsParams` do aplikace Kalkulačka pomocí vlastností objektu.

Metoda `VerifyTotal()` má podobnou strukturu a obsahuje následující kód kontrolního výrazu:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Název textového pole je uveden jako neznámý, protože vývojář aplikace Kalkulačka systému Windows neposkytl veřejně dostupný název ovládacího prvku. Metoda <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> se nezdaří, pokud skutečná hodnota není rovna očekávané hodnotě, což by způsobilo selhání testu. Všimněte si také, že očekávaná hodnota obsahuje desetinnou čárku, za kterou následuje mezera. Pokud budete někdy muset změnit funkce tohoto konkrétního testu, musíte povolit tuto desetinnou čárku a prostor.

##### <a name="uimap-properties"></a><a name="UIMapProperties"></a>Vlastnosti UIMap
Kód pro každou vlastnost je také standardní v celé třídě. Následující kód pro `AddItemsParams` vlastnost se `AddItems()` používá v metodě.

```csharp
public virtual AddItemsParams AddItemsParams
{
    get
    {
        if ((this.mAddItemsParams == null))
        {
            this.mAddItemsParams = new AddItemsParams();
        }
        return this.mAddItemsParams;
    }
}
```

Všimněte si, že vlastnost používá `mAddItemsParams` soukromou místní proměnnou, která je pojmenována pro uložení hodnoty před tím, než ji vrátí. Název vlastnosti a název třídy pro objekt, který vrátí, jsou stejné. Třída je definována dále v *souboru UIMap.cs.*

Každá třída, která je vrácena vlastností, je strukturována podobně. Třída je `AddItemsParams` následující:

```csharp
/// <summary>
/// Parameters to be passed into 'AddItems'
/// </summary>
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public class AddItemsParams
{
    #region Fields
    /// <summary>
    /// Type '{NumPad7}' in 'Calculator' Dialog
    /// </summary>
    public string UICalculatorDialogSendKeys = "{NumPad7}";

    /// <summary>
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    /// </summary>
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";
    #endregion
}
```

Stejně jako u všech tříd v souboru *UIMap.cs,* tato třída začíná <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. V této malé `Fields` třídě je oblast, která definuje řetězce použít <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> jako parametry `UIMap.AddItems()` pro metodu, která se používá v metodě, která byla popsána dříve. Můžete napsat kód nahradit hodnoty v těchto polích řetězce před metodou, ve které se používají tyto parametry se nazývá volá.

### <a name="uimapcs"></a><a name="UIMapCS"></a>UIMap.cs
Ve výchozím nastavení obsahuje `UIMap` tento soubor částečnou třídu, která nemá žádné metody nebo vlastnosti.

#### <a name="uimap-class"></a>Třída UIMap
Toto je místo, kde můžete vytvořit vlastní kód pro rozšíření funkce [Třídy UIMap.](/previous-versions/dd580454(v=vs.140)) Kód, který vytvoříte v tomto souboru není přepsán **a coded UI Test Builder** při každé změně testu.

Všechny části [UIMap](/previous-versions/dd580454(v=vs.140)) můžete použít metody a vlastnosti z jakékoli jiné části [Třídy UIMap.](/previous-versions/dd580454(v=vs.140))

### <a name="codeduitest1cs"></a><a name="CodedUITestCS"></a>CodedUITest1.cs
Tento soubor je generován **Programové UI Test Builder**, ale není znovu vytvořen při každé změně testu, takže můžete upravit kód v tomto souboru. Název souboru je generován z názvu, který jste zadali pro test při jeho vytvoření.

#### <a name="codeduitest1-class"></a>Třída CodedUITest1

Ve výchozím nastavení obsahuje tento soubor definici pouze pro jednu třídu.

```csharp
[CodedUITest]
public class CodedUITest1
```

[CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) je automaticky použita na třídu, která umožňuje testování rozhraní rozpoznat jako rozšíření testování. Všimněte si také, že se nejedná o částečnou třídu. V tomto souboru je obsažen veškerý kód třídy.

##### <a name="codeduitest1-properties"></a><a name="CodedUITestProperties"></a>Vlastnosti CodedUITest1

Třída obsahuje dvě výchozí vlastnosti, které jsou umístěny v dolní části souboru. Neupravujte je.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="codeduitest1-methods"></a><a name="CodedUITestMethods"></a>Metody CodedUITest1
Ve výchozím nastavení obsahuje třída pouze jednu metodu.

```csharp
public void CodedUITestMethod1()
```

Tato metoda `UIMap` volá každou metodu, kterou jste zadali při zaznamenání testu, který je popsán v části [třídy UIMap](#UIMapClass).

Oblast s názvem `Additional test attributes`, pokud není komentář, obsahuje dvě volitelné metody.

```csharp
// Use TestInitialize to run code before running each test
[TestInitialize()]
public void MyTestInitialize()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.LaunchCalculator();
}

// Use TestCleanup to run code after each test has run
[TestCleanup()]
public void MyTestCleanup()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.CloseCalculator();
}
```

Metoda `MyTestInitialize()` má <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> použít na něj, který říká testování rozhraní volat tuto metodu před jakékoli jiné zkušební metody. Podobně `MyTestCleanup()` metoda má <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> použít na něj, který říká testování rozhraní volat tuto metodu po všechny ostatní zkušební metody byly volány. Použití těchto metod je volitelné. Pro tento test `UIMap.LaunchCalculator()` může být `MyTestInitialize()` metoda `UIMap.CloseCalculator()` volána z `MyTestCleanup()` a metoda `CodedUITest1Method1()`může být volána z namísto z .

Pokud přidáte další metody do této třídy pomocí [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)), testování rozhraní volá každou metodu jako součást testu.

### <a name="uimapuitest"></a><a name="UIMapuitest"></a>UIMap.uitest
Jedná se o soubor XML, který představuje strukturu kódovaného záznamu testu uI a všech jeho částí. Patří mezi ně akce a třídy kromě metody a vlastnosti těchto tříd. Soubor [UIMap.Designer.cs](#UIMapDesignerFile) obsahuje kód, který je generován Tvůrce matného rozhraní pro reprodukci struktury testu a poskytuje připojení k rozhraní testování.

Soubor *UIMap.uitest* nelze přímo upravovat. Můžete však použít Coded UI Builder upravit test, který automaticky upraví soubor *UIMap.uitest* a [*soubor UIMap.Designer.cs.*](#UIMapDesignerFile)

## <a name="see-also"></a>Viz také

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [Atribut CodedUITest](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytváření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md)
- [Doporučené postupy pro kódované testy rozhraní](../test/best-practices-for-coded-ui-tests.md)
- [Testování velké aplikace s více mapami ui](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
