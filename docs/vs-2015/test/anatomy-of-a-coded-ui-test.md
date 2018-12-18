---
title: Anatomie programového testu UI | Dokumentace Microsoftu
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
- coded UI tests
ms.assetid: 9c5d82fc-3fb7-4bb1-a9ac-ac1fa3a4b500
caps.latest.revision: 25
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7595a967a6dae091da6c5a7613a27c602cc1381e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202745"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomie programového testu UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když vytvoříte programový Test uživatelského rozhraní v projektu programového testu UI, několik souborů se přidají do vašeho řešení. V tomto tématu použijeme příklad programový Test uživatelského rozhraní a prozkoumejte tyto soubory.  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
## <a name="contents-of-a-coded-ui-test"></a>Obsah programového testu UI  
 Když vytvoříte programový Test uživatelského rozhraní, **Tvůrce programového testu UI** vytvoří mapu uživatelského rozhraní v rámci testu a také testovací metody, parametry a kontrolní výrazy pro všechny testy. Také vytvoří soubor třídy pro každý test.  
  
|Soubor|Obsah|Upravitelné?|  
|----------|--------------|---------------|  
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Část deklarace](#UIMapDesignerFile)<br /><br /> [Třídy UIMap](#UIMapClass) (částečné, automaticky vygenerovaný)<br /><br /> [Metody](#UIMapMethods)<br /><br /> [Vlastnosti](#UIMapProperties)|Ne|  
|[UIMap.cs](#UIMapCS)|[Třídy UIMap](#UIMapCS) (částečné)|Ano|  
|[CodedUITest1.cs](#CodedUITestCS)|[Třída CodedUITest1](#CodedUITestCS)<br /><br /> [Metody](#CodedUITestMethods)<br /><br /> [Vlastnosti](#CodedUITestProperties)|Ano|  
|[UIMap.uitest](#UIMapuitest)|Mapování XML pro test uživatelského rozhraní.|Ne|  
  
###  <a name="UIMapDesignerFile"></a> UIMap.Designer.cs  
 Tento soubor obsahuje kód, který je automaticky vytvořen aplikací **Tvůrce programového testu UI** při vytvoření testu. Tento soubor znovu vytvoří pokaždé, když test změní, takže se nejedná o soubor, ve kterém můžete přidat nebo upravit kód.  
  
#### <a name="declarations-section"></a>Část deklarace  
 Tato část obsahuje následující deklarace pro uživatelské rozhraní Windows.  
  
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
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> Obor názvů je zahrnuté pro Windows uživatelského rozhraní (UI). Pro webovou stránku uživatelského rozhraní, obor názvů by <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>; pro uživatelské rozhraní Windows Presentation Foundation, obor názvů by <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.  
  
####  <a name="UIMapClass"></a> Třídy UIMap  
 V následující části najdete ho <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> třídy.  
  
```  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public partial class UIMap  
```  
  
 Kód třídy začíná <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> , která je použita na třídu, která je deklarována jako částečná třída. Můžete si všimnout, že atribut je použit také každá třída v tomto souboru. Druhý soubor, který může obsahovat další kód pro tuto třídu není `UIMap.cs`, která je popsána dále.  
  
 Vygenerovaný `UIMap` třída obsahuje kód pro jednotlivé metody, které bylo zadané při zaznamenávání testu.  
  
```  
public void LaunchCalculator()  
public void AddItems()  
public void VerifyTotal()  
public void CleanUp()  
```  
  
 Tato část <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> třída také zahrnuje kód generovaný pro každou vlastnost, který vyžaduje metody.  
  
```  
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
  
#####  <a name="UIMapMethods"></a> Metody třídy UIMap  
 Každá z metod má strukturu, která vypadá podobně jako `AddItems()` metody. To je vysvětleno podrobněji v části kódu, které jsou uvedeny společně s zalomení pro přehlednost přidat.  
  
```  
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
  
 Souhrn komentář pro každou definici metody říká třídy zadání hodnot parametrů pro danou metodu. V takovém případě je `AddItemsParams` třída, která je definována později v `UIMap.cs` souboru a která je také hodnotový typ, který je vrácený `AddItemsParams` vlastnost.  
  
 V horní části metody je kód `Variable Declarations` oblast, která definuje místní proměnné pro uživatelské rozhraní objektů, které budou použity metodou.  
  
 V této metodě obě `UIItemWindow` a `UIItemEdit` jsou vlastnosti, které jsou přístupné pomocí `UICalculatorWindow` třída, která je definována později v `UIMap.cs` souboru.  
  
 Dále jsou řádky, které odesílají text z klávesnice aplikace Kalkulačka pomocí vlastnosti `AddItemsParams` objektu.  
  
 `VerifyTotal()` Metoda má velmi podobné struktury a obsahuje následující kód kontrolní výraz.  
  
```  
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '  
Assert.AreEqual(  
    this.VerifyTotalExpectedValues.UIItemEditText,   
    uIItemEdit.Text);  
```  
  
 Název textového pole je uveden jako neznámý, protože vývojář aplikace Windows Kalkulačka neposkytl název veřejně k dispozici pro ovládací prvek. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> Metoda selže při skutečná hodnota nerovná s očekávanou hodnotou, což by způsobilo selhání testu. Všimněte si také, že obsahuje očekávaná hodnota desetinná čárka, za kterým následuje mezera. Pokud je třeba upravit funkce nasazovaných tento konkrétní test, musíte také povolit pro tuto desetinné čárky a místo.  
  
#####  <a name="UIMapProperties"></a> Vlastnosti třídy UIMap  
 Kód pro každou vlastnost je také velmi standard v rámci třídy. Následující kód `AddItemsParams` vlastnost se používá v `AddItems()` metody.  
  
```  
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
  
 Všimněte si, že vlastnost používá privátní místní proměnnou s názvem `mAddItemsParams` pro uchování hodnoty před jeho vrácením. Název vlastnosti a název třídy pro objekt, který vrátí jsou stejné. Je třída definovaná v později `UIMap.cs` souboru.  
  
 Každá třída, která je vrácena pomocí vlastnosti strukturovaná podobně. Tady je `AddItemsParams` třídy.  
  
```  
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
  
 Stejně jako u všech tříd v `UIMap.cs` soubor, tato třída začíná <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. V této třídě malé je `Fields` oblast, která definuje řetězce, který se použije jako parametry <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> metodu, která se používá v `UIMap.AddItems()` metody, který byl popsán výše. Můžete napsat kód k nahrazení hodnoty v těchto polích řetězce před voláním metody, ve kterém se používají tyto parametry.  
  
###  <a name="UIMapCS"></a> UIMap.cs  
 Ve výchozím nastavení, tento soubor obsahuje částečné `UIMap` třídu, která nemá žádné metody a vlastnosti.  
  
#### <a name="uimap-class"></a>Třídy UIMap  
 To je, kde můžete vytvořit vlastní kód pro rozšíření funkcí <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> třídy. Nebude znovu vygenerovat kód, který vytvoříte v tomto souboru **Tvůrce programového testu UI** pokaždé, když se upraví testu.  
  
 Všechny části <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> můžete použít metody a vlastnosti z jakékoliv jiné části <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> třídy.  
  
###  <a name="CodedUITestCS"></a> CodedUITest1.cs  
 Tento soubor vygenerovala sada **Tvůrce programového testu UI**, ale nevytvoří znovu pokaždé, když se upraví testu, takže můžete upravit kód v tomto souboru. Název souboru je vytvořen z názvu, který jste zadali pro test při jeho vytváření.  
  
#### <a name="codeduitest1-class"></a>Třída CodedUITest1  
 Ve výchozím nastavení tento soubor obsahuje definici pro pouze jednu třídu.  
  
```  
[CodedUITest]  
public class CodedUITest1  
```  
  
 T:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute se automaticky využije na třídu, která umožňuje testovací rozhraní rozpoznat jako testování rozšíření. Všimněte si také, že se nejedná o částečnou třídu. Všechny třídy kód je obsažen v tomto souboru.  
  
#####  <a name="CodedUITestProperties"></a> Vlastnosti CodedUITest1  
 Třída obsahuje dvě výchozí vlastnosti, které jsou umístěné v dolní části souboru. Nesmí být upraven.  
  
```  
/// <summary>  
/// Gets or sets the test context which provides  
/// information about and functionality for the current test run.  
///</summary>  
public TestContext TestContext  
public UIMap UIMap  
```  
  
#####  <a name="CodedUITestMethods"></a> CodedUITest1 metody  
 Ve výchozím nastavení třída obsahuje pouze jednu metodu.  
  
```  
public void CodedUITestMethod1()  
```  
  
 Tato metoda volá všechny `UIMap` metodu, která jste zadali, když jste si poznamenali test, který je popsaný v části na [třídy UIMap](#UIMapClass).  
  
 Oblast, která má název `Additional test attributes`, pokud komentář, obsahuje dvě metody, volitelné.  
  
```  
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
  
 `MyTestInitialize()` Metoda má <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> použit, který informuje testovací rozhraní mohli volat tuto metodu před všechny ostatní metody testu. Podobně `MyTestCleanup()` metoda má <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> použit, který dává pokyn testovací rozhraní mohli volat tuto metodu po všech dalších testovacích metod byly volány. Použití těchto metod je volitelné. Pro tento test `UIMap.LaunchCalculator()` metodu lze volat z `MyTestInitialize()` a `UIMap.CloseCalculator()` metodu lze volat z `MyTestCleanup()` namísto z `CodedUITest1Method1()`.  
  
 Pokud přidáte další metody do této třídy pomocí <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>, testovací rozhraní bude volat jednotlivé metody jako část testu.  
  
###  <a name="UIMapuitest"></a> UIMap.uitest  
 Toto je soubor XML, který představuje struktury programového uživatelského rozhraní testu záznam a všech jejích částí. Patří mezi ně akce a třídy kromě metod a vlastností z těchto tříd. [UIMap.Designer.cs](#UIMapDesignerFile) soubor obsahuje kód, který je vygenerován pomocí Tvůrce programového uživatelského rozhraní pro reprodukci struktura testu a poskytuje připojení pro testovací rozhraní.  
  
 `UIMap.uitest` Soubor se nedá přímo upravovat. Můžete však použít Tvůrce programového uživatelského rozhraní upravit test, který automaticky změní `UIMap.uitest` souboru a [UIMap.Designer.cs](#UIMapDesignerFile) souboru.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>   
 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>   
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Osvědčené postupy pro programové testy UI](../test/best-practices-for-coded-ui-tests.md)   
 [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



