---
title: Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7190a7f698868642c58d1de2ff801e328859b9db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851809"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Váš ovládací prvek může být snáze testován, Pokud implementujete podporu pro rozhraní programového testování uživatelského rozhraní. Zvýšení úrovně podpory můžete přidat přírůstkově. Můžete začít podporou záznamu a přehrávání a ověření vlastností. Můžete vytvořit na to, aby mohl Tvůrce programového testu uživatelského rozhraní rozpoznat vlastní vlastnosti ovládacího prvku a poskytnout vlastní třídy pro přístup k těmto vlastnostem z generovaného kódu. Můžete také pomáhat Tvůrce programového testu UI zachytávání akcí způsobem, který je blíže záměru zaznamenané akce.

 **V tomto tématu:**

1. [Podpora záznamů a přehrávání a ověřování vlastností implementací přístupnosti](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)

2. [Podpora ověřování vlastních vlastností implementací zprostředkovatele vlastností](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)

3. [Podpora generování kódu implementací třídy pro přístup k vlastním vlastnostem](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)

4. [Akce podporující záměry podpory implementací filtru akcí](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)

   ![UI&#95;úplné](../test/media/cuit-full.png "CUIT_Full")

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a><a name="recordandplayback"></a> Podpora záznamů a přehrávání a ověřování vlastností implementací přístupnosti
 Tvůrce programového testu uživatelského rozhraní zachycuje informace o ovládacích prvcích, ke kterým dojde během záznamu, a pak vygeneruje kód pro přehrání této relace. Pokud váš ovládací prvek nepodporuje přístupnost, bude Tvůrce programového testu uživatelského rozhraní zachytit akce (například kliknutí myší) pomocí souřadnic obrazovky. Po přehrání testu vygeneruje generovaný kód tyto kliknutí myší na stejné souřadnice obrazovky. Pokud se ovládací prvek zobrazí na jiném místě na obrazovce při přehrání testu, vygenerovaný kód selže při provádění této akce s vaším ovládacím prvkem. To může mít za následek selhání, pokud se test přehrává v různých konfiguracích obrazovky, v různých prostředích nebo po změnách v rozložení uživatelského rozhraní.

 ![UI&#95;RecordNoSupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")

 Pokud implementujete přístupnost, bude však Tvůrce programového testu UI používat k zachycení informací o vašem ovládacím prvku při záznamu testu a vygenerování kódu. Poté, když spustíte test, vygenerovaný kód přehraje tyto události proti vašemu ovládacímu prvku, i v případě, že je někde jinde v uživatelském rozhraní. Autoři testů budou také moci vytvářet výrazy s použitím základních vlastností vašeho ovládacího prvku.

 ![Záznam&#95;UI](../test/media/cuit-record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Podpora záznamu a přehrávání, ověřování vlastností a navigace ovládacího prvku Windows Forms
 Implementujte přístupnost pro váš ovládací prvek, jak je uvedeno v následujícím postupu, a podrobně vysvětleno v <xref:System.Windows.Forms.AccessibleObject> .

 ![UI&#95;k dispozici](../test/media/cuit-accessible.png "CUIT_Accessible")

1. Implementujte třídu, která je odvozena z <xref:System.Windows.Forms.Control.ControlAccessibleObject> a přepište <xref:System.Windows.Forms.Control.AccessibilityObject%2A> vlastnost, která vrátí objekt vaší třídy.

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

2. Přepište <xref:System.Windows.Forms.AccessibleObject.Role%2A> <xref:System.Windows.Forms.AccessibleObject.State%2A> <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> vlastnosti a metody přístupného objektu.

3. Implementujte další objekt přístupnosti pro podřízený ovládací prvek a přepište vlastnost podřízeného ovládacího prvku <xref:System.Windows.Forms.Control.AccessibilityObject%2A> tak, aby vracela objekt přístupnosti.

4. Přepište <xref:System.Windows.Forms.AccessibleObject.Bounds%2A> <xref:System.Windows.Forms.AccessibleObject.Name%2A> vlastnosti,, <xref:System.Windows.Forms.AccessibleObject.Parent%2A> ,,, a a <xref:System.Windows.Forms.AccessibleObject.Role%2A> <xref:System.Windows.Forms.AccessibleObject.State%2A> <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> <xref:System.Windows.Forms.AccessibleObject.Select%2A> metody objektu usnadnění podřízeného ovládacího prvku.

> [!NOTE]
> Toto téma začíná ukázkou přístupnosti v rámci <xref:System.Windows.Forms.AccessibleObject> tohoto postupu a následně na něj ve zbývajících postupech vytvoří. Pokud chcete vytvořit funkční verzi ukázky přístupnosti, vytvořte konzolovou aplikaci a potom nahraďte kód v Program.cs ukázkovým kódem. Budete muset přidat odkazy na přístupnost, System. Drawing a System. Windows. Forms. Měli byste změnit **typy spolupráce pro vložení** pro přístupnost na **false** , aby se vyloučilo upozornění sestavení. Typ výstupu projektu můžete změnit na z **konzolové aplikace** na **aplikaci systému Windows** , aby se okno konzoly nezobrazovalo při spuštění aplikace.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a><a name="customproprties"></a> Podpora ověřování vlastních vlastností implementací zprostředkovatele vlastností
 Jakmile implementujete základní podporu pro záznam a přehrávání a vlastnost ověřování, můžete nastavit vlastní vlastnosti ovládacího prvku pro programové testy uživatelského rozhraní implementací <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> modulu plug-in. Následující procedura například vytvoří poskytovatele vlastností, který umožňuje programovým testům uživatelského rozhraní získat přístup k vlastnosti State pro podřízené ovládací prvky CurveLegend ovládacího prvku graf.

 ![UI&#95;CustomProps](../test/media/cuit-customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>Podpora ověřování vlastních vlastností
 ![UI&#95;props](../test/media/cuit-props.png "CUIT_Props")

1. Přepište vlastnost přístupného objektu legendy křivky <xref:System.Windows.Forms.AccessibleObject.Description%2A> tak, aby předávala hodnoty vlastností v řetězci popisu, oddělené od hlavního popisu (a druhá při implementaci více vlastností) středníkem (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add “;” and the state value to the end
                // of the curve legend’s description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

2. Vytvořte balíček rozšíření uživatelského rozhraní pro váš ovládací prvek tak, že vytvoříte projekt knihovny tříd a přidáte odkazy na přístupnost, Microsoft. VisualStudio. TestTools. UITesting, Microsoft. VisualStudio. TestTools. UITest. Common a Microsoft. VisualStudio. TestTools. extension. Změňte **typy spolupráce pro vložení** pro přístupnost na **false**.

3. Přidejte třídu poskytovatele vlastností, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> .

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

4. Implementací názvů vlastností a popisovačů vlastností do vytvořte zprostředkovatele vlastností <xref:System.Collections.Generic.Dictionary%602> .

    ```csharp
    // Define a map of property descriptors for CurveLegend
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap
    {
        get
        {
            if (curveLegendPropertiesMap == null)
            {
                UITestPropertyAttributes read =
                    UITestPropertyAttributes.Readable |
                    UITestPropertyAttributes.DoNotGenerateProperties;
                curveLegendPropertiesMap =
                    new Dictionary<string, UITestPropertyDescriptor>
                        (StringComparer.OrdinalIgnoreCase);
                curveLegendPropertiesMap.Add("State",
                    new UITestPropertyDescriptor(typeof(string), read));
            }
            return curveLegendPropertiesMap;
        }
    }

    // return the property descriptor
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)
    {
        return CurveLegendPropertiesMap[propertyName];
    }

    // return the property names
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))
        {
            // the keys of the property map are the collection of property names
            return CurveLegendPropertiesMap.Keys;
        }

        // this is not my control
        throw new NotSupportedException();
    }

    // Get the property value by parsing the accessible description
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)
    {
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))
        {
            object[] native = uiTestControl.NativeElement as object[];
            IAccessible acc = native[0] as IAccessible;

            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });
            return descriptionTokens[1];
        }

        // this is not my control
        throw new NotSupportedException();
    }
    ```

5. Přepsání <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> k označení toho, že vaše sestavení poskytuje podporu pro konkrétní ovládací prvek a jeho podřízené prvky.

    ```csharp
    public override int GetControlSupportLevel(UITestControl uiTestControl)
    {
        // For MSAA, check the control type
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",
            StringComparison.OrdinalIgnoreCase) &&
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))
        {
            return (int)ControlSupport.ControlSpecificSupport;
        }

        // This is not my control, so return NoSupport
        return (int)ControlSupport.NoSupport;
    }
    ```

6. Přepište zbývající abstraktní metody <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName> .

    ```csharp
    public override string[] GetPredefinedSearchProperties(Type specializedClass)
    {
        throw new NotImplementedException();
    }

    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)
    {
        throw new NotImplementedException();
    }

    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)
    {
        throw new NotImplementedException();
    }

    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)
    {
        throw new NotImplementedException();
    }

    ```

7. Přidejte třídu balíčku rozšíření, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> .

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        internal class ChartControlExtensionPackage : UITestExtensionPackage
        {
        }
    }
    ```

8. Definujte `UITestExtensionPackage` atribut pro sestavení.

    ```csharp
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
                    "ChartControlExtensionPackage",
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]
    namespace ChartControlExtensionPackage
    {
       …
    ```

9. V rámci třídy balíčku rozšíření přepište, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> aby vracel třídu poskytovatele vlastností, když je vyžádán poskytovatel vlastností.

    ```csharp
    internal class ChartControlExtensionPackage : UITestExtensionPackage
    {
        public override object GetService(Type serviceType)
        {
            if (serviceType == typeof(UITestPropertyProvider))
            {
                if (propertyProvider == null)
                {
                    propertyProvider = new ChartControlPropertyProvider();
                }
                return propertyProvider;
            }
            return null;
        }

        private UITestPropertyProvider propertyProvider = null;
    }
    ```

10. Přepište zbývající abstraktní metody a vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> .

    ```csharp

    public override void Dispose() { }

    public override string PackageDescription
    {
        get { return "Supports coded UI testing of ChartControl"; }
    }

    public override string PackageName
    {
        get { return "ChartControl Test Extension"; }
    }

    public override string PackageVendor
    {
        get { return "Microsoft (sample)"; }
    }

    public override Version PackageVersion
    {
        get { return new Version(1, 0); }
    }

    public override Version VSVersion
    {
        get { return new Version(10, 0); }
    }
    ```

11. Sestavte binární soubory a zkopírujte je do **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.

> [!NOTE]
> Tento balíček rozšíření bude použit pro všechny ovládací prvky, které jsou typu "text". Pokud testujete více ovládacích prvků stejného typu, budete je muset testovat samostatně a spravovat, které balíčky rozšíření budou nasazeny při záznamu testů.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a><a name="codegeneration"></a> Podpora generování kódu implementací třídy pro přístup k vlastním vlastnostem
 Když Tvůrce programového testu uživatelského rozhraní generuje kód ze záznamu relace, používá <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> třídu pro přístup k ovládacím prvkům.

```csharp

      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());
```

 Pokud jste implementovali poskytovatele vlastností k poskytnutí přístupu k vlastním vlastnostem ovládacího prvku, můžete přidat specializovanou třídu, která se používá pro přístup k těmto vlastnostem, aby byl generovaný kód zjednodušený.

```csharp

      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);
```

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Přidání specializované třídy pro přístup k ovládacímu prvku
 ![UI&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")

1. Implementujte třídu, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> a přidejte typ ovládacího prvku do kolekce vlastností vyhledávání v konstruktoru.

    ```csharp
    public class CurveLegend:WinControl
    {
       public CurveLegend(UITestControl c) : base(c)
       {
          // The curve legend control is a “text” type of control
          SearchProperties.Add(
             UITestControl.PropertyNames.ControlType, "Text");
       }
    }
    ```

2. Implementujte vlastní vlastnosti ovládacího prvku jako vlastnosti třídy.

    ```csharp
    public virtual string State
    {
        get
        {
            return (string)GetProperty("State");
        }
    }
    ```

3. Přepište metodu poskytovatele vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> tak, aby vracela typ nové třídy pro podřízené ovládací prvky legendy křivky.

    ```csharp
    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
       if (uiTestControl.ControlType.NameEquals("Text"))
       {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
          return typeof(CurveLegend);
       }

       // this is not a curve legend control
       return null;
    }
    ```

4. Přepište metodu poskytovatele vlastností <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> , aby vracela typ nové metody ' PropertyNames ' třídy.

    ```csharp
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Text"))
        {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
            return typeof(CurveLegend.PropertyNames);
        }

        // this is not a curve legend control
        return null;
    }
    ```

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a><a name="intentawareactions"></a> Akce podporující záměry podpory implementací filtru akcí
 Když aplikace Visual Studio zaznamená test, zachytí každou událost myši a klávesnice. V některých případech však může být záměr akce ztracen v řadě událostí myši a klávesnice. Například pokud váš ovládací prvek podporuje automatické dokončování, stejná sada událostí myši a klávesnice může mít za následek jinou hodnotu, když je test přehrán v jiném prostředí. Můžete přidat modul plug-in filtru akcí, který nahradí řadu událostí klávesnice a myši jedinou akcí. Tímto způsobem můžete nahradit řadu událostí myši a klávesnice výsledkem výběru hodnoty jedinou akcí, která nastaví hodnotu. Provádí ochranu programových testů uživatelského rozhraní z rozdílů v automatickém dokončování z jednoho prostředí do druhého.

### <a name="to-support-intent-aware-actions"></a>Pro podporu akcí s podporou záměrů
 ![UI&#95;akce](../test/media/cuit-actions.png "CUIT_Actions")

1. Implementujte třídu filtru akcí, která je odvozena z [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))a přepíše vlastnosti [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) a [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

    ```csharp
    internal class MyActionFilter : UITestActionFilter
    {
       // If the user actions we are aggregating exceeds the time allowed,
       // this filter is not applied. (The timeout is configured when the
       // test is run.)
       public override bool ApplyTimeout
       {
          get { return true; }
       }

       // Gets the category of this filter. Categories of filters
       // are applied in priority order.
       public override UITestActionFilterCategory Category
       {
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }
       }

       public override bool Enabled
       {
          get { return true; }
       }

       public override UITestActionFilterType FilterType
       {
          // This action filter operates on a single action
          get { return UITestActionFilterType.Unary; }
       }

       // Gets the name of the group to which this filter belongs.
       // A group can be enabled/disabled using configuration file.
       public override string Group
       {
          get { return "ChartControlActionFilters"; }
       }

       // Gets the name of this filter.
       public override string Name
       {
          get { return "Convert Double-Click to Single-Click"; }
       }
    ```

2. Přepsat `UITestActionFilter.ProcessRule` . Tento příklad nahrazuje akci dvakrát kliknout jediným kliknutím.

    ```csharp
    public override bool ProcessRule(IUITestActionStack actionStack)
    {
        if (actionStack.Count > 0)
        {
            MouseAction lastAction = actionStack.Peek() as MouseAction;
            if (lastAction != null)
            {
                if (lastAction.UIElement.ControlTypeName.Equals(
                     ControlType.Text.ToString(),
                     StringComparison.OrdinalIgnoreCase))
                {
                    if(lastAction.ActionType == MouseActionType.DoubleClick)
                    {
                        // Convert to single click
                        lastAction.ActionType = MouseActionType.Click;
                    }
                }
            }
        }
        // Do not stop aggregation
        return false;
    }
    ```

3. Přidejte filtr akce do <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> metody balíčku rozšíření.

    ```csharp
    public override object GetService(Type serviceType)
    {
       if (serviceType == typeof(UITestPropertyProvider))
       {
          if (propertyProvider == null)
          {
             propertyProvider = new PropertyProvider();
          }
          return propertyProvider;
       }
       else if (serviceType == typeof(UITestActionFilter))
       {
          if (actionFilter == null)
          {
             actionFilter = new RadGridViewActionFilter();
          }
          return actionFilter;
       }
       return null;
    }
    ```

4. Sestavení binárních souborů a jejich zkopírování do%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

> [!NOTE]
> Filtr akcí nezávisí na implementaci přístupnosti nebo na poskytovateli vlastností.

## <a name="debug-your-property-provider-or-action-filter"></a>Ladění poskytovatele vlastností nebo filtru akcí
 Váš zprostředkovatel vlastností a filtr akcí jsou implementovány v balíčku rozšíření, který je načten a spuštěn pomocí Tvůrce programového testu uživatelského rozhraní v procesu odděleném od vaší aplikace.

#### <a name="to-debug-your-property-provider-or-action-filter"></a>Ladění poskytovatele vlastností nebo filtru akcí

1. Sestavení ladicí verze balíčku rozšíření zkopírování souborů. dll a PDB do nástroje%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

2. Spusťte aplikaci (není v ladicím programu).

3. Spusťte Tvůrce programového testu uživatelského rozhraní.

     `codedUITestBuilder.exe  /standalone`

4. Připojte ladicí program k procesu codedUITestBuilder.

5. Nastavte zarážky v kódu.

6. V Tvůrci programového testu uživatelského rozhraní Vytvořte výrazy, které budou uplatňovat poskytovatele vlastností, a zaznamenejte akce pro uplatnění filtrů akcí.

## <a name="external-resources"></a>Externí zdroje

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.AccessibleObject>
- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
