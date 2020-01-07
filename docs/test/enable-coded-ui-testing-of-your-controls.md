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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589614"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky

Implementujte podporu pro rozhraní programového testování uživatelského rozhraní, abyste měli svůj ovládací prvek větší testovatelné. Zvýšení úrovně podpory můžete přidat přírůstkově. Začněte podporou záznamu a přehrávání a ověření vlastností. Pak Sestavte to tak, aby povoloval Tvůrce programového testu uživatelského rozhraní pro rozpoznávání vlastních vlastností ovládacího prvku. Poskytněte vlastní třídy pro přístup k těmto vlastnostem z generovaného kódu. Můžete také pomáhat Tvůrce programového testu UI zachytávání akcí způsobem, který je blíže záměru zaznamenané akce.

![UI&#95;plná](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Podpora záznamů a přehrávání a ověřování vlastností implementací přístupnosti

Tvůrce programového testu uživatelského rozhraní zachycuje informace o ovládacích prvcích, ke kterým dojde během záznamu, a pak vygeneruje kód pro přehrání této relace. Pokud váš ovládací prvek nepodporuje přístupnost, program Tvůrce programového testu UI zachytí akce (například kliknutí myší) pomocí souřadnic obrazovky. Po přehrání testu vygeneruje generovaný kód akce na stejných souřadnicích obrazovky. Pokud se ovládací prvek zobrazí na jiném místě na obrazovce při přehrání testu, vygenerovaný kód selže při provádění akce. Neimplementací přístupnosti pro váš ovládací prvek se může zobrazit chyba testu, pokud se test přehrává v různých konfiguracích obrazovky, v různých prostředích nebo při změně rozložení uživatelského rozhraní.

![UI&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

Pokud implementujete přístupnost, Tvůrce programového testu uživatelského rozhraní používá tuto funkci k zachycení informací o vašem ovládacím prvku při záznamu testu. Poté, když spustíte test, vygenerovaný kód přehraje tyto události proti vašemu ovládacímu prvku, i v případě, že je někde jinde v uživatelském rozhraní. Autoři testů mohou také vytvořit výrazy s použitím základních vlastností ovládacího prvku.

![Záznam&#95;UI](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Podpora záznamu a přehrávání, ověřování vlastností a navigace pro ovládací prvek model Windows Forms
Implementujte přístupnost pro váš ovládací prvek, jak je uvedeno v následujícím postupu, a podrobně vysvětleno v <xref:System.Windows.Forms.AccessibleObject>.

![UI&#95;přístupný](../test/media/cuit_accessible.png)

1. Implementujte třídu, která je odvozena z <xref:System.Windows.Forms.Control.ControlAccessibleObject>a přepište vlastnost <xref:System.Windows.Forms.Control.AccessibilityObject%2A>, která vrátí objekt vaší třídy.

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

2. Přepište <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> a <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> vlastnosti a metody přístupového objektu.

3. Implementujte další objekt usnadnění pro podřízený ovládací prvek a přepište vlastnost <xref:System.Windows.Forms.Control.AccessibilityObject%2A> podřízeného ovládacího prvku tak, aby vracela objekt usnadnění.

4. Přepište <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>a <xref:System.Windows.Forms.AccessibleObject.Select%2A>ch vlastností a metod objektu přístupnosti podřízeného ovládacího prvku.

> [!NOTE]
> V tomto tématu se začíná ukázka přístupnosti v <xref:System.Windows.Forms.AccessibleObject>a potom se v této ukázce vytvoří ve zbývajících postupech. Pokud chcete vytvořit funkční verzi ukázky přístupnosti, vytvořte konzolovou aplikaci a potom nahraďte kód v *program.cs* ukázkovým kódem. Přidejte odkazy na přístupnost, System. Drawing a System. Windows. Forms. Chcete-li odstranit upozornění sestavení, změňte **typy spolupráce pro vložení** pro přístupnost na **false** . Výstupní typ projektu lze změnit z **konzolové aplikace** na **aplikaci systému Windows** , aby se okno konzoly nezobrazovalo při spuštění aplikace.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Podpora ověřování vlastních vlastností implementací zprostředkovatele vlastností

Po implementaci základní podpory pro záznam a přehrávání a ověřování vlastností můžete nastavit vlastní vlastnosti ovládacího prvku k dispozici pro programové testy uživatelského rozhraní implementací modulu plug-in <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>. Následující procedura například vytvoří poskytovatele vlastností, který umožňuje programovým testům uživatelského rozhraní získat přístup k vlastnosti State pro podřízené ovládací prvky CurveLegend ovládacího prvku grafu:

![UI&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Podpora ověřování vlastních vlastností

![UI&#95;props](../test/media/cuit_props.png)

1. Přepište vlastnost <xref:System.Windows.Forms.AccessibleObject.Description%2A> objektu přístupné legendy křivky tak, aby v řetězci popisu předávala hodnoty vlastností. Více hodnot oddělte středníkem (;).

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

1. Vytvořte balíček rozšíření pro test uživatelského rozhraní pro váš ovládací prvek vytvořením projektu knihovny tříd. Přidejte odkazy na přístupnost, Microsoft. VisualStudio. TestTools. UITesting, Microsoft. VisualStudio. TestTools. UITest. Common a Microsoft. VisualStudio. TestTools. extension. Změňte **typy spolupráce pro vložení** pro přístupnost na **false**.

1. Přidejte třídu poskytovatele vlastností, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

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

1. Implementací názvů vlastností a popisovačů vlastností do <xref:System.Collections.Generic.Dictionary%602>implementovat zprostředkovatele vlastností.

1. Přepište <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> pro indikaci, že vaše sestavení poskytuje podporu pro ovládací prvek a jeho podřízené prvky.

1. Přepsat zbývající abstraktní metody <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Přidejte třídu balíčku rozšíření, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Definujte atribut `UITestExtensionPackage` pro sestavení.

1. V rámci třídy balíčku rozšíření přepište <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> a vraťte třídu poskytovatele vlastností, když je požadován zprostředkovatel vlastností.

1. Přepište zbývající abstraktní metody a vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Sestavte binární soubory a zkopírujte je do *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Tento balíček rozšíření se použije na libovolný ovládací prvek, který je typu "text". Pokud testujete více ovládacích prvků stejného typu, otestujte je samostatně, abyste mohli spravovat, které balíčky rozšíření budou nasazeny při záznamu testů.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Podpora generování kódu implementací třídy pro přístup k vlastním vlastnostem

Když Tvůrce programového testu uživatelského rozhraní generuje kód ze záznamu relace, používá třídu <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> pro přístup k ovládacím prvkům.

Pokud jste implementovali poskytovatele vlastností k poskytnutí přístupu k vlastním vlastnostem ovládacího prvku, můžete přidat specializovanou třídu, která se používá pro přístup k těmto vlastnostem. Přidání specializované třídy zjednodušuje vygenerovaný kód.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Přidání specializované třídy pro přístup k ovládacímu prvku

![UI&#95;CodeGen](../test/media/cuit_codegen.png)

1. Implementujte třídu, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> a přidejte typ ovládacího prvku do kolekce vlastností vyhledávání v konstruktoru.

1. Implementujte vlastní vlastnosti ovládacího prvku jako vlastnosti třídy.

1. Přepište metodu <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> poskytovatele vlastností, aby vracela typ nové třídy pro podřízené ovládací prvky legendy křivky.

1. Přepište metodu <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> poskytovatele vlastností, aby vracela typ nové metody ' PropertyNames ' třídy.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Akce podporující záměry podpory implementací filtru akcí

Když aplikace Visual Studio zaznamená test, zachytí každou událost myši a klávesnice. V některých případech však může být záměr akce ztracen v řadě událostí myši a klávesnice. Například pokud váš ovládací prvek podporuje automatické dokončování, stejná sada událostí myši a klávesnice může mít za následek jinou hodnotu, když je test přehrán v jiném prostředí. Můžete přidat modul plug-in filtru akcí, který nahradí řadu událostí klávesnice a myši jedinou akcí. Tímto způsobem můžete nahradit řadu událostí myši a klávesnice, které vyberou hodnotu jedinou akcí, která nastaví hodnotu. Provádí ochranu programových testů uživatelského rozhraní z rozdílů v automatickém dokončování z jednoho prostředí do druhého.

### <a name="to-support-intent-aware-actions"></a>Pro podporu akcí s podporou záměrů

![Akce&#95;UI](../test/media/cuit_actions.png)

1. Implementujte třídu filtru akcí, která je odvozena z [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))a přepíše vlastnosti [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) a [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

1. Přepsat [ProcessRule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110)). Tento příklad nahrazuje akci dvakrát kliknout pomocí akce jediného kliknutí.

1. Přidejte filtr akce do metody <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> balíčku rozšíření.

1. Sestavte binární soubory a zkopírujte je do *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Filtr akcí nezávisí na implementaci přístupnosti nebo na poskytovateli vlastností.

## <a name="debug-your-property-provider-or-action-filter"></a>Ladění poskytovatele vlastností nebo filtru akcí

Váš zprostředkovatel vlastností a filtr akcí jsou implementovány v balíčku rozšíření. Nástroj test Builder spustí balíček rozšíření v samostatném procesu z aplikace.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Ladění poskytovatele vlastností nebo filtru akcí

1. Sestavení ladicí verze balíčku pro rozšíření zkopírujte soubory *. dll* a *. pdb* do *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2. Spusťte aplikaci (není v ladicím programu).

3. Spusťte Tvůrce programového testu uživatelského rozhraní.

     `codedUITestBuilder.exe  /standalone`

4. Připojte ladicí program k procesu codedUITestBuilder.

5. Nastavte zarážky v kódu.

6. V Tvůrci programového testu uživatelského rozhraní Vytvořte výrazy, které budou uplatňovat poskytovatele vlastností, a zaznamenejte akce pro uplatnění filtrů akcí.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.AccessibleObject>
- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
