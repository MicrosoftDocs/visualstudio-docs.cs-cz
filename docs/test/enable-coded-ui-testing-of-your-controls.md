---
title: Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b9f9256407f854e5e7eefbca0cdd767679b9c88c
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895948"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky

Implementaci podpory programových testů UI framework provádět více možností intenzivního testování ovládacího prvku. Zvýšení úrovně podpory můžete přidat postupně. Začněte tím, že podpora záznam a přehrávání a vlastnosti ověřování. Následně vytvářejte a povolit Tvůrce programového testu uživatelského rozhraní pro rozpoznávání vlastností vlastního ovládacího prvku. Zadejte vlastní třídy pro přístup k těmto vlastnostem generovaného kódu. Může také pomoct programového uživatelského rozhraní testu Tvůrce zachycení akce způsobem, který je blíž k příslušnému záměru akce, které je zaznamenáváno.

![CUIT&#95;úplné](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Podpora ověření záznam a přehrávání a vlastnost implementací usnadnění přístupu

Tvůrce programového testu uživatelského rozhraní shromažďuje informace o ovládacích prvcích, že během nahrávání dojde a potom generuje kód do přehrát tuto relaci. Pokud váš ovládací prvek nepodporuje přístupnost, Tvůrce programového testu uživatelského rozhraní zaznamenané akce (jako je kliknutí myší) pomocí souřadnice obrazovky. Při přehrávání testu generovaný kód vydá akcí ve stejné souřadnice obrazovky. Pokud váš ovládací prvek se zobrazí na jiném místě na obrazovce při přehrávání testu, se nezdaří generovaného kódu k provedení akce. Usnadnění pro ovládací prvek není implementací, může se zobrazit selhání testu, pokud test přehrávání na jinou obrazovku konfigurace v různých prostředích, nebo když se změní rozložení uživatelského rozhraní.

 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

 Pokud se rozhodnete implementovat přístupnost, Tvůrce programového testu uživatelského rozhraní, která používá k zaznamenání informací o ovládacího prvku při nahrávání testu. Pak při spuštění testu je vygenerovaný kód bude znovu přehrát tyto události pro ovládací prvek, i v případě, že je někde jinde v uživatelském rozhraní. Můžete také vytvořit test autoři nepodmíněné výrazy pomocí základní vlastnosti ovládacího prvku.

 ![CUIT&#95;záznamu](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Pro podporu záznam a přehrávání a ověření vlastností navigace pro ovládací prvek Windows Forms
 Implementace usnadnění pro ovládací prvek, jak je uvedeno v následujícím postupu a podrobně popsaný v části <xref:System.Windows.Forms.AccessibleObject>.

 ![CUIT&#95;přístupné](../test/media/cuit_accessible.png)

1.  Implementace, která je odvozena z třídy <xref:System.Windows.Forms.Control.ControlAccessibleObject>a přepsat <xref:System.Windows.Forms.Control.AccessibilityObject%2A> vlastnost k vrácení objektu vaší třídy.

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

2.  Přepsat přístupný objekt <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> a <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> vlastnosti a metody.

3.  Implementovat jiný objekt usnadnění pro podřízený ovládací prvek a přepsat podřízený ovládací prvek <xref:System.Windows.Forms.Control.AccessibilityObject%2A> vlastnost vrátí objekt usnadnění.

4.  Přepsat <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, a <xref:System.Windows.Forms.AccessibleObject.Select%2A> vlastnosti a metody pro objekt usnadnění podřízený ovládací prvek.

> [!NOTE]
> Toto téma začíná ukázka usnadnění přístupu v <xref:System.Windows.Forms.AccessibleObject>a poté sestaví na této ukázce v zbývající postupy. Pokud chcete vytvořit pracovní verzi vzorku přístupnost, vytvořte konzolovou aplikaci a pak nahraďte kód v *Program.cs* se vzorovým kódem. Přidáte odkazy na dostupnost, System.Drawing a System.Windows.Forms. Změnit **Embed Interop Types** pro usnadnění přístupu k **False** k vyloučení upozornění sestavení. Můžete změnit typ výstupu projektu z **konzolovou aplikaci** k **aplikace Windows** tak, aby se nezobrazí okno konzoly při spuštění aplikace.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Implementace vlastnosti zprostředkovatele podpory ověření vlastních vlastností

Po implementaci základní podporu pro záznam a přehrávání a vlastnost ověření můžete zpřístupnit vlastní vlastnosti ovládacího prvku pro programové testy UI implementací <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> modulu plug-in. Například následující postup vytvoří vlastnost poskytovatele, který umožňuje programové testy uživatelského rozhraní pro přístup k vlastnosti stavu ovládacího prvku grafu CurveLegend podřízených ovládacích prvků:

 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Pro podporu ověřování vlastní vlastnost

![CUIT&#95;Props](../test/media/cuit_props.png)

1. Přepsat křivky legendy přístupné objektu <xref:System.Windows.Forms.AccessibleObject.Description%2A> vlastnost a zajistěte tak předání hodnoty bohaté vlastností řetězce popisu. Více hodnoty oddělte středníkem (;).

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

1. Vytvořte balíček rozšíření test uživatelského rozhraní pro ovládací prvek tak, že vytvoříte projekt knihovny tříd. Přidáte odkazy na dostupnost, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common a Microsoft.VisualStudio.TestTools.Extension. Změnit **vložit typy spolupráce** pro usnadnění přístupu k **False**.

1. Přidejte třídu poskytovatele vlastnost, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

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

1. Implementace zprostředkovatele vlastnost tak, že názvy vlastností a popisovače vlastnosti v <xref:System.Collections.Generic.Dictionary%602>.

1. Přepsat <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> k označení, že vaše sestavení poskytuje podporu specifické pro ovládací prvek pro ovládací prvek a jeho podřízené položky.

1. Přepsat zbývající abstraktní metody <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Přidejte třídu balíček rozšíření, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Definovat `UITestExtensionPackage` atribut pro sestavení.

1. Ve třídě balíčku rozšíření přepsat <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> vrácené třída vlastnost zprostředkovatele v případě, že je požadována vlastnost zprostředkovatele.

1. Přepsání zbývající abstraktní metody a vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Sestavit binární soubory a zkopírujte je do *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Tento balíček rozšíření platí pro libovolný ovládací prvek, který je typu "Text". Pokud testujete více ovládacích prvků stejného typu, otestujete je samostatně tak můžete spravovat, které balíčky rozšíření se nasazují po zaznamenání testů.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Nepodporuje generování kódu díky implementaci třídy pro přístup k vlastní vlastnosti

Tvůrce programového testu uživatelského rozhraní generuje kód ze záznamu relace, používá <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> tříd pro vaše ovládací prvky přístupu.

Pokud jste implementovali vlastnost zprostředkovatele pro poskytnutí přístupu k vlastnosti vlastního ovládacího prvku, můžete přidat specializované třídy, který se používá pro přístup k těmto vlastnostem. Přidání specializované třídy zjednodušuje generovaného kódu.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Chcete-li přidat specializované třídy pro přístup k ovládacího prvku

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png)

1. Implementace, která je odvozena z třídy <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> a přidejte typ ovládacího prvku do kolekce vlastností vyhledávání v konstruktoru.

1. Implementace vlastních vlastností ovládacího prvku jako vlastnosti třídy.

1. Přepsání poskytovatele vlastnost <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metody na návratový typ novou třídu pro křivku podřízené ovládací prvky legendy.

1. Přepsání poskytovatele vlastnost <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metody na návratový typ metody PropertyNames novou třídu.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Podpora akce podporující záměr implementací filtru akce

 Když Visual Studio zaznamenává testu, zachytí každou událost myši a klávesnice. V některých případech však můžete záměr akce ztraceno v řadu událostí myši a klávesnice. Například pokud váš ovládací prvek podporuje automatické dokončování, stejnou sadu událostí myši a klávesnice může vést k jinou hodnotu při testu je přehrávání v jiném prostředí. Můžete přidat filtr akce modulu plug-in, který nahrazuje řadu událostí klávesnice a myši pomocí jedné akce. Tímto způsobem můžete nahradit řadu událostí myši a klávesnice, které vyberte hodnotu pomocí jedné akce, která nastaví hodnotu. Programové testy UI způsobem, který chrání před rozdíly v automatickém dokončování z jednoho prostředí do druhého.

### <a name="to-support-intent-aware-actions"></a>Pro podporu akce podporující záměr

![CUIT&#95;akce](../test/media/cuit_actions.png)

1. Implementovat třídu filtru akce, která je odvozena od <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, přepisování vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> a <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.

1. Přepsat <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. Tento příklad nahradí akce dvakrát klikněte na akci jedním kliknutím.

1. Přidat filtr akce <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> – metoda rozšíření balíčku.

1. Sestavit binární soubory a zkopírujte je do *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Filtr akce není závislý na implementaci usnadnění nebo zprostředkovatel vlastností.

## <a name="debug-your-property-provider-or-action-filter"></a>Ladit vlastnosti zprostředkovatele nebo akce filtru

Vlastnost filtru poskytovatele a akce jsou implementované v balíčku rozšíření. Tvůrce testu spustí balíček rozšíření v samostatném procesu ze své aplikace.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Chcete-li ladit vlastnosti zprostředkovatele nebo akce filtru

1.  Sestavení ladicí verze kopii balíčku rozšíření *.dll* a *PDB* soubory *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2.  Spusťte aplikaci (ne v ladicím programu).

3.  Spusťte Tvůrce programového testu uživatelského rozhraní.

     `codedUITestBuilder.exe  /standalone`

4.  Připojte ladicí program k procesu codedUITestBuilder.

5.  Nastavte zarážky v kódu.

6.  Vytvořte v Tvůrce programového testu uživatelského rozhraní, nepodmíněné výrazy pro výkon poskytovatele vlastnost a zaznamenejte akce vykonávat filtry akce.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.AccessibleObject>
- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)