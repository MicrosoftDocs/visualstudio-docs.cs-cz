---
title: Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: feb7785678be4b6f2c26bbcff93bf7d3e6632116
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589614"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Povolení programového testování ovládacích prvků v rozhraní

Implementujte podporu pro kódované rozhraní testování rozhraní, aby se vaše řízení více testovatelné. Můžete přidat zvýšení úrovně podpory postupně. Začněte podporou záznamu a přehrávání a ověřování vlastností. Potom stavět na tom, aby kódované tvůrce testů ui rozpoznat vlastní vlastnosti ovládacího prvku. Poskytněte vlastní třídy pro přístup k těmto vlastnostem z generovaného kódu. Můžete také pomoci kódované ui tvůrce testů zachytit akce způsobem, který je blíže k záměru akce zaznamenané.

![CUIT&#95;plný](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Podpora záznamu a přehrávání a ověřování vlastností implementací usnadnění

Programový tvůrce testů ui zachycuje informace o ovládacích prvcích, se kterými se setká během nahrávání, a poté vygeneruje kód pro přehrání této relace. Pokud ovládací prvek nepodporuje usnadnění přístupu, pak programovaný tvůrce testů ui zachytí akce (jako kliknutí myší) pomocí souřadnic obrazovky. Při přehrávání testu vygenerovaný kód vydá akce ve stejných souřadnicích obrazovky. Pokud se ovládací prvek zobrazí na jiném místě na obrazovce při přehrávání testu, vygenerovaný kód se nezdaří provést akci. Tím, že neimplementuje usnadnění přístupu pro váš ovládací prvek, může se zobrazit selhání testu, pokud je test přehrán v různých konfiguracích obrazovky, v různých prostředích nebo při změně rozložení uživatelského rozhraní.

![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

Pokud implementujete usnadnění přístupu, programový tvůrce testování ui používá k zachycení informací o ovládacím prvku při zaznamenávání testu. Potom při spuštění testu, vygenerovaný kód bude přehrát tyto události proti ovládacímu prvku, i když je někde jinde v uživatelském rozhraní. Autoři testu můžete také vytvořit nepodmíněných výrazů pomocí základní vlastnosti ovládacího prvku.

![&#95;záznam CUIT](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Podpora záznamu a přehrávání, ověření vlastností a navigace pro ovládací prvek Windows Forms
Implementujte usnadnění přístupu pro ovládací prvek, jak je <xref:System.Windows.Forms.AccessibleObject>popsáno v následujícím postupu a podrobně vysvětleno v .

![CUIT&#95;přístupné](../test/media/cuit_accessible.png)

1. Implementujte třídu, <xref:System.Windows.Forms.Control.ControlAccessibleObject>která je odvozena od , a přepsat <xref:System.Windows.Forms.Control.AccessibilityObject%2A> vlastnost vrátit objekt vaší třídy.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2. Přepište <xref:System.Windows.Forms.AccessibleObject.Role%2A>vlastnosti <xref:System.Windows.Forms.AccessibleObject.State%2A> <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> a <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> metody přístupného objektu .

3. Implementujte jiný objekt usnadnění pro podřízený ovládací <xref:System.Windows.Forms.Control.AccessibilityObject%2A> prvek a přepište vlastnost podřízeného ovládacího prvku, abyste vrátili objekt usnadnění přístupu.

4. Přepište <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>vlastnosti <xref:System.Windows.Forms.AccessibleObject.Parent%2A> <xref:System.Windows.Forms.AccessibleObject.Role%2A> <xref:System.Windows.Forms.AccessibleObject.State%2A> <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>a <xref:System.Windows.Forms.AccessibleObject.Select%2A> metody přístupnosti podřízeného ovládacího prvku . <xref:System.Windows.Forms.AccessibleObject.Name%2A>

> [!NOTE]
> Toto téma začíná ukázkou usnadnění v aplikaci <xref:System.Windows.Forms.AccessibleObject>a potom na tomto vzorku vychází ve zbývajících postupech. Pokud chcete vytvořit pracovní verzi ukázky usnadnění přístupu, vytvořte konzolovou aplikaci a potom nahraďte kód v *Program.cs* ukázkovým kódem. Přidejte odkazy na usnadnění přístupnosti, System.Drawing a System.Windows.Forms. Změňte **vložit interop typy** pro usnadnění na **nepravda,** aby se odstranilo upozornění sestavení. Typ výstupu projektu můžete změnit z **konzolové aplikace** na **aplikaci systému Windows** tak, aby se při spuštění aplikace nezobrazilo okno konzoly.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Podpora ověření vlastních vlastností implementací poskytovatele vlastnosti

Po implementaci základní podpory pro záznam a přehrávání a ověření vlastností můžete zpřístupnit vlastní vlastnosti ovládacího <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> prvku pro kódované testy ui pomocí modulu plug-in. Například následující postup vytvoří zprostředkovatele vlastností, který umožňuje programové testy ui pro přístup k State vlastnost podřízené ovládací prvky ovládací prvky CurveLegend ovládacíprvky ovládací prvky ovládací prvky ovládací prvky CurveLegend ovládacíprvky ovládací prvky:

![CUIT&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Podpora ověření vlastních vlastností

![CUIT&#95;rekvizity](../test/media/cuit_props.png)

1. Přepište <xref:System.Windows.Forms.AccessibleObject.Description%2A> vlastnost objektu přístupného legendě křivky a předáte hodnoty bohatých vlastností v řetězci popisu. Oddělte více hodnot středníky (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add ";" and the state value to the end
                // of the curve legend's description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

1. Vytvořte balíček rozšíření testovacího prostředí pro váš ovládací prvek vytvořením projektu knihovny tříd. Přidejte odkazy na usnadnění přístupu, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common a Microsoft.VisualStudio.TestTools.Extension. Změňte **typy vložit interop** pro usnadnění **přístupu**na false .

1. Přidejte třídu zprostředkovatele vlastností, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

1. Implementujte zprostředkovatele vlastností umístěním názvů vlastností <xref:System.Collections.Generic.Dictionary%602>a popisovačů vlastností do .

1. Přepište <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> označuje, že vaše sestavení poskytuje podporu specifické pro ovládací prvek a jeho podřízené.

1. Přepsat zbývající abstraktní metody<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Přidejte třídu balíčku rozšíření, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>která je odvozena od aplikace .

1. Definujte `UITestExtensionPackage` atribut pro sestavení.

1. Ve třídě balíčku rozšíření <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> přepište vrátit třídu zprostředkovatele vlastnosti, když je požadován poskytovatel vlastnosti.

1. Přepište zbývající abstraktní metody a <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>vlastnosti .

1. Vytvořte binární soubory a zkopírujte je do *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Tento balíček rozšíření je použita pro všechny ovládací prvek, který je typu "Text". Pokud testujete více ovládacích prvků stejného typu, otestujte je samostatně, abyste mohli spravovat, které balíčky rozšíření jsou nasazeny při záznamu testů.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Podpora generování kódu implementací třídy pro přístup k vlastním vlastnostem

Když programový tvůrce testů ui generuje kód ze záznamu <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> relace, používá třídu pro přístup k ovládacím prvkům.

Pokud jste implementovali poskytovatele vlastností, který poskytuje přístup k vlastním vlastnostem ovládacího prvku, můžete přidat specializovanou třídu, která se používá pro přístup k těmto vlastnostem. Přidání specializované třídy zjednodušuje generovaný kód.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Přidání specializované třídy pro přístup k ovládacímu prvku

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png)

1. Implementujte třídu, která <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> je odvozena od a přidejte typ ovládacího prvku do kolekce vlastností hledání v konstruktoru.

1. Implementujte vlastní vlastnosti ovládacího prvku jako vlastnosti třídy.

1. Přepsat <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metodu poskytovatele vlastnosti vrátit typ nové třídy pro podřízené ovládací prvky legendy křivky.

1. Přepište <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metodu poskytovatele vlastnosti a vraťte typ metody PropertyNames nové třídy.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Podpora akcí podporujících záměr implementací filtru akcí

Když Visual Studio zaznamená test, zachytí každou událost myši a klávesnice. V některých případech však záměr akce může být ztracena v sérii událostí myši a klávesnice. Například pokud ovládací prvek podporuje automatické dokončování, stejná sada událostí myši a klávesnice může mít za následek jinou hodnotu při přehrávání testu v jiném prostředí. Můžete přidat modul plug-in filtru akcí, který nahradí řadu událostí klávesnice a myši jedinou akcí. Tímto způsobem můžete nahradit řadu událostí myši a klávesnice, které vyberou hodnotu jedinou akcí, která nastaví hodnotu. To chrání kódované testy rozhraní před rozdíly v automatickém dokončování z jednoho prostředí do druhého.

### <a name="to-support-intent-aware-actions"></a>Podpora akcí podporujících záměr

![cuit&#95;akce](../test/media/cuit_actions.png)

1. Implementujte třídu filtru akce, která je odvozena z [uITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)), přepsání vlastností [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) a [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

1. Přepsat [processrule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110)). Zde příklad nahradí akci poklepání akcí jedním kliknutím.

1. Přidejte filtr akcí <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> do metody balíčku rozšíření.

1. Vytvořte binární soubory a zkopírujte je do *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Filtr akce nezávisí na implementaci usnadnění nebo na poskytovateli vlastností.

## <a name="debug-your-property-provider-or-action-filter"></a>Ladění poskytovatele vlastnosti nebo filtru akcí

Váš poskytovatel vlastnosti a filtr akcí jsou implementovány v balíčku rozšíření. Tvůrce testů spustí balíček rozšíření v samostatném procesu z vaší aplikace.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Ladění poskytovatele vlastnosti nebo filtru akcí

1. Vytvořte ladicí verzi balíčku rozšíření zkopírovat soubory *DLL* a *PDB* do *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2. Spusťte aplikaci (ne v ladicím programu).

3. Spusťte tvůrce kódovaného testu ui.

     `codedUITestBuilder.exe  /standalone`

4. Připojte ladicí program k procesu codedUITestBuilder.

5. Nastavte zarážky v kódu.

6. V programovém tvůrce testů ui vytvořte nepodmíněných výrazů pro uplatnění poskytovatele vlastnosti a zaznamenejte akce k výkonu filtrů akcí.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.AccessibleObject>
- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
