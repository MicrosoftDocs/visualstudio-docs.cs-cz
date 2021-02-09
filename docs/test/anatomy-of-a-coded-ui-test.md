---
title: Anatomie programového testu UI
description: Přečtěte si o souborech, které jsou přidány do řešení programového testu UI při vytváření programového testu uživatelského rozhraní.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65b55c79dd39b5e8393d22542a2334d84b191293
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933073"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomie kódovaného testu uživatelského rozhraní

Při vytváření programového testu uživatelského rozhraní v projektu programového testu uživatelského rozhraní se do řešení přidá několik souborů. Tento článek poskytuje informace o souborech.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Obsah kódovaného testu uživatelského rozhraní

Když vytvoříte programový test UI, Tvůrce programového **testu uživatelského** rozhraní vytvoří mapu testovaného uživatelského rozhraní a také testovací metody, parametry a kontrolní výrazy pro všechny testy. Také vytvoří soubor třídy pro každý test.

|Soubor|Obsah|Možno?|
|-|-|-|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Oddíl deklarací](#UIMapDesignerFile)<br /><br /> [UIMap – třída](#UIMapClass) (částečně, automaticky generovaná)<br /><br /> [Metody](#UIMapMethods)<br /><br /> [Vlastnosti](#UIMapProperties)|Ne|
|[UIMap.cs](#UIMapCS)|[UIMap – třída](#UIMapCS) (částečný)|Ano|
|[CodedUITest1.cs](#CodedUITestCS)|[CodedUITest1 – třída](#CodedUITestCS)<br /><br /> [Metody](#CodedUITestMethods)<br /><br /> [Vlastnosti](#CodedUITestProperties)|Ano|
|[UIMap. UITest](#UIMapuitest)|Mapa XML uživatelského rozhraní pro test.|Ne|

### <a name="uimapdesignercs"></a><a name="UIMapDesignerFile"></a> UIMap.Designer.cs
Tento soubor obsahuje kód, který je automaticky vytvořen **tvůrcem programového testu UI** při vytvoření testu. Tento soubor se znovu vytvoří pokaždé, když se změní test, takže se nejedná o soubor, ve kterém můžete přidat nebo upravit kód.

#### <a name="declarations-section"></a>Oddíl deklarací
Tato část obsahuje následující deklarace pro uživatelské rozhraní systému Windows.

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

<xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>Obor názvů je zahrnutý v uživatelském rozhraní systému Windows (UI). V uživatelském rozhraní webové stránky by byl obor názvů <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls> . pro Windows Presentation Foundation uživatelské rozhraní by byl obor názvů <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls> .

#### <a name="uimap-class"></a><a name="UIMapClass"></a> UIMap – třída
Další část souboru je třída [UIMap](/previous-versions/dd580454(v=vs.140)) .

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Kód třídy začíná <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> atributem, který je použit pro třídu, která je deklarována jako částečná třída. Všimněte si, že atribut je také použit pro každou třídu v tomto souboru. Druhý soubor, který může obsahovat více kódu pro tuto třídu, je *UIMap.cs*, který je popsán později.

Vygenerovaná `UIMap` Třída obsahuje kód pro každou metodu, která byla zadána při záznamu testu.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

Tato část třídy [UIMap](/previous-versions/dd580454(v=vs.140)) také obsahuje generovaný kód pro každou vlastnost, která je vyžadována metodami.

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

##### <a name="uimap-methods"></a><a name="UIMapMethods"></a> Metody UIMap
Každá metoda má strukturu, která se podobá `AddItems()` metodě. To je vysvětleno podrobněji v kódu, který je zobrazen společně s zalomením řádku pro přidání srozumitelnosti.

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

Souhrnný komentář pro každou definici metody určuje, která třída má být použita pro hodnoty parametrů dané metody. V tomto případě je to `AddItemsParams` třída, která je definována později v souboru *UIMap.cs* a což je také typ hodnoty, který je vrácen `AddItemsParams` vlastností.

V horní části kódu metody je `Variable Declarations` oblast, která definuje místní proměnné pro objekty uživatelského rozhraní, které jsou používány metodou.

V této metodě `UIItemWindow` a `UIItemEdit` jsou vlastnosti, které jsou k dispozici pomocí `UICalculatorWindow` třídy, která je definována později v souboru *UIMap.cs* .

Dále jsou řádky, které odesílají text z klávesnice do aplikace kalkulačky pomocí vlastností `AddItemsParams` objektu.

`VerifyTotal()`Metoda má podobnou strukturu a obsahuje následující kód kontrolního výrazu:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Název textového pole je uveden jako neznámý, protože vývojář aplikace kalkulačky systému Windows neposkytl veřejně dostupný název ovládacího prvku. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>Metoda selže, pokud skutečná hodnota není rovna očekávané hodnotě, což by způsobilo selhání testu. Všimněte si také, že očekávaná hodnota obsahuje desetinnou čárku, po které následuje mezera. Pokud někdy budete muset změnit funkčnost tohoto konkrétního testu, je nutné pro tuto desetinnou čárku a místo použít.

##### <a name="uimap-properties"></a><a name="UIMapProperties"></a> Vlastnosti UIMap
Kód pro každou vlastnost je také standardně v celé třídě. `AddItemsParams`V metodě je použit následující kód pro vlastnost `AddItems()` .

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

Všimněte si, že vlastnost používá privátní místní proměnnou, která je pojmenována `mAddItemsParams` pro uchování hodnoty, než ji vrátí. Název vlastnosti a název třídy objektu, který vrací, jsou stejné. Třída je definována později v souboru *UIMap.cs* .

Každá třída, která je vrácena vlastností, je strukturována podobně. Následuje `AddItemsParams` Třída:

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

Stejně jako u všech tříd v souboru *UIMap.cs* začíná Tato třída s <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . V této malé třídě je `Fields` oblast definující řetězce, které se mají použít jako parametry pro <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> metodu, která je použita v `UIMap.AddItems()` metodě, která byla popsána výše. Můžete napsat kód, který nahradí hodnoty v těchto polích řetězců předtím, než je volána metoda, ve které jsou tyto parametry použity.

### <a name="uimapcs"></a><a name="UIMapCS"></a> UIMap.cs
Ve výchozím nastavení tento soubor obsahuje částečnou `UIMap` třídu, která nemá žádné metody nebo vlastnosti.

#### <a name="uimap-class"></a>UIMap – třída
Zde můžete vytvořit vlastní kód pro rozšiřování funkcí třídy [UIMap](/previous-versions/dd580454(v=vs.140)) . Kód, který vytvoříte v tomto souboru, není přepsán **tvůrcem programového testu UI** pokaždé, když je test změněn.

Všechny části [UIMap](/previous-versions/dd580454(v=vs.140)) mohou používat metody a vlastnosti z jakékoli jiné části třídy [UIMap](/previous-versions/dd580454(v=vs.140)) .

### <a name="codeduitest1cs"></a><a name="CodedUITestCS"></a> CodedUITest1.cs
Tento soubor je vygenerován **tvůrcem programového testu uživatelského rozhraní**, ale není znovu vytvořen pokaždé, když je test změněn, takže můžete upravit kód v tomto souboru. Název souboru je vygenerován z názvu, který jste zadali pro test při jeho vytvoření.

#### <a name="codeduitest1-class"></a>CodedUITest1 – třída

Ve výchozím nastavení tento soubor obsahuje definici pouze pro jednu třídu.

```csharp
[CodedUITest]
public class CodedUITest1
```

[CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) se automaticky aplikuje na třídu, která umožňuje testovacímu rozhraní rozpoznat ho jako testovací rozšíření. Všimněte si také, že se nejedná o částečnou třídu. V tomto souboru je obsažený všechen kód třídy.

##### <a name="codeduitest1-properties"></a><a name="CodedUITestProperties"></a> Vlastnosti CodedUITest1

Třída obsahuje dvě výchozí vlastnosti, které jsou umístěny ve spodní části souboru. Neupravujte je.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="codeduitest1-methods"></a><a name="CodedUITestMethods"></a> Metody CodedUITest1
Ve výchozím nastavení třída obsahuje pouze jednu metodu.

```csharp
public void CodedUITestMethod1()
```

Tato metoda volá každou `UIMap` metodu, kterou jste zadali při nahrávání testu, který je popsán v části [třídy UIMap](#UIMapClass).

Oblast, která je `Additional test attributes` Poznáma s názvem (Pokud se jedná o odkomentovat), obsahuje dvě volitelné metody.

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

`MyTestInitialize()`Metoda je <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> aplikována na tuto metodu, která instruuje testovací rozhraní pro volání této metody před všemi ostatními testovacími metodami. Podobně platí, že `MyTestCleanup()` Metoda je <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> aplikována na metodu, která instruuje testovací rozhraní, aby volalo tuto metodu po volání všech ostatních testovacích metod. Použití těchto metod je volitelné. Pro tento test `UIMap.LaunchCalculator()` může být metoda volána z `MyTestInitialize()` a `UIMap.CloseCalculator()` metodu lze volat z `MyTestCleanup()` místo z `CodedUITest1Method1()` .

Pokud do této třídy přidáte více metod pomocí [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)), testovací rozhraní volá každou metodu jako součást testu.

### <a name="uimapuitest"></a><a name="UIMapuitest"></a> UIMap. UITest
Jedná se o soubor XML, který představuje strukturu záznamu kódovaného testu uživatelského rozhraní a všechny jeho části. Mezi ně patří akce a třídy kromě metod a vlastností těchto tříd. Soubor [UIMap.Designer.cs](#UIMapDesignerFile) obsahuje kód, který je generován tvůrcem programového uživatelského rozhraní pro reprodukování struktury testu a poskytuje připojení k testovacímu rozhraní.

Soubor *UIMap. UITest* není přímo upravitelný. Můžete však použít program Tvůrce programového uživatelského rozhraní k úpravě testu, který automaticky upraví soubor *UIMap. UITest* a soubor [*UIMap.Designer.cs*](#UIMapDesignerFile) .

## <a name="see-also"></a>Viz také

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytváření programových testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Osvědčené postupy pro programové testy uživatelského rozhraní](../test/best-practices-for-coded-ui-tests.md)
- [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
