---
title: Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: gewarren
manager: douge
ms.openlocfilehash: e5ab2ca3e0f7d8f7006177f89c6850ce9882681a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848537"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ovládací prvek lze snadněji testovat, pokud se rozhodnete implementovat podporu pro testovací rozhraní programového uživatelského rozhraní. Zvýšení úrovně podpory můžete přidat postupně. Můžete začít díky podpoře záznam a přehrávání a vlastnosti ověřování. Můžete stavět na, které umožní rozpoznat vlastností vlastního ovládacího prvku Tvůrce programového testu uživatelského rozhraní a zadat vlastní třídy pro přístup k těmto vlastnostem generovaného kódu. Může také pomoct programového uživatelského rozhraní testu Tvůrce zachycení akce způsobem, který je blíž k příslušnému záměru akce, které je zaznamenáváno.  
  
 **V tomto tématu:**  
  
1. [Podpora záznam a přehrávání a ověření vlastností implementací usnadnění přístupu](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2. [Implementace vlastnosti zprostředkovatele podpory vlastní vlastnosti ověření](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3. [Nepodporuje generování kódu díky implementaci třídy pro přístup k vlastní vlastnosti](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4. [Podpora akce podporující záměr implementací filtru akce](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
   ![CUIT&#95;Full](../test/media/cuit-full.png "CUIT_Full")  
  
##  <a name="recordandplayback"></a> Podpora záznam a přehrávání a ověření vlastností implementací usnadnění přístupu  
 Tvůrce programového testu uživatelského rozhraní shromažďuje informace o ovládacích prvcích, že během nahrávání dojde a potom generuje kód do přehrát tuto relaci. Pokud váš ovládací prvek nepodporuje přístupnost, Tvůrce programového testu uživatelského rozhraní zaznamená akce (jako je kliknutí myší) pomocí souřadnice obrazovky. Při přehrávání testu vygenerovaný kód bude vydávat těchto kliknutí myší v stejné souřadnice obrazovky. Pokud váš ovládací prvek se zobrazí na jiném místě na obrazovce při přehrávání testu, se nezdaří generovaného kódu k provedení této akce ovládacího prvku. To může způsobit selhání Pokud test přehrávání na jinou obrazovku konfigurace, v různých prostředích, nebo po byly provedeny změny rozložení uživatelského rozhraní.  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")  
  
 Pokud se rozhodnete implementovat usnadnění přístupu, ale tvůrce programového testu uživatelského rozhraní bude používat, který vám poskytne informace o ovládacího prvku, když zaznamenává testu a generuje kód. Pak při spuštění testu je vygenerovaný kód bude znovu přehrát tyto události pro ovládací prvek, i v případě, že je někde jinde v uživatelském rozhraní. Autoři testu bude také možné vytvořit nepodmíněné výrazy pomocí základní vlastnosti ovládacího prvku.  
  
 ![CUIT&#95;Record](../test/media/cuit-record.png "CUIT_Record")  
  
### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Pro podporu záznam a přehrávání a ověření vlastností navigace pro ovládací prvek Windows forms  
 Implementace usnadnění pro ovládací prvek, jak je uvedeno v následujícím postupu a podrobně popsaný v části <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT&#95;přístupné](../test/media/cuit-accessible.png "CUIT_Accessible")  
  
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
  
3.  Implementovat jiný objekt usnadnění pro podřízený ovládací prvek a přepsat podřízený ovládací prvek <xref:System.Windows.Forms.Control.AccessibilityObject%2A> vlastnost vrátí tento objekt usnadnění přístupu.  
  
4.  Přepsat <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, a <xref:System.Windows.Forms.AccessibleObject.Select%2A> vlastnosti a metody pro objekt usnadnění podřízený ovládací prvek.  
  
> [!NOTE]
>  Toto téma začíná ukázka usnadnění přístupu v <xref:System.Windows.Forms.AccessibleObject> v tomto postupu a pak sestavení zabývat v další postupy. Pokud chcete vytvořit pracovní verzi vzorku přístupnost, vytvořte konzolovou aplikaci a pak nahraďte kód v souboru Program.cs se vzorovým kódem. Bude potřeba přidat odkazy na dostupnost, System.Drawing a System.Windows.Forms. Měli byste změnit **Embed Interop Types** pro usnadnění přístupu k **False** k vyloučení upozornění sestavení. Můžete změnit typ výstupu projektu do z **konzolovou aplikaci** k **aplikace Windows** tak, aby se nezobrazí okno konzoly při spuštění aplikace.  
  
##  <a name="customproprties"></a> Implementace vlastnosti zprostředkovatele podpory vlastní vlastnosti ověření  
 Jakmile implementujete základní podporu pro záznam a přehrávání a vlastnost ověření, můžete zpřístupnit vlastní vlastnosti ovládacího prvku pro programové testy UI implementací <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> modulu plug-in. Například následující postup vytvoří vlastnost poskytovatele, který umožňuje programové testy uživatelského rozhraní pro přístup k vlastnosti stavu ovládacího prvku grafu CurveLegend podřízených ovládacích prvků.  
  
 ![CUIT&#95;CustomProps](../test/media/cuit-customprops.png "CUIT_CustomProps")  
  
### <a name="to-support-custom-property-validation"></a>Pro podporu ověřování vlastní vlastnost  
 ![CUIT&#95;Props](../test/media/cuit-props.png "CUIT_Props")  
  
1.  Přepsat křivky legendy přístupné objektu <xref:System.Windows.Forms.AccessibleObject.Description%2A> vlastnost a zajistěte tak předání hodnoty bohaté vlastností řetězce popisu oddělená od hlavní popis (a mezi sebou při implementaci více vlastností) oddělte středníkem (;).  
  
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
  
2.  Vytvořte balíček rozšíření test uživatelského rozhraní pro ovládací prvek tak, že vytvoříte projekt knihovny tříd a přidejte odkazy na usnadnění přístupu, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common, a Microsoft.VisualStudio.TestTools.Extension. Změnit **vložit typy spolupráce** pro usnadnění přístupu k **False**.  
  
3.  Přidejte třídu poskytovatele vlastnost, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  
  
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
  
4.  Implementace zprostředkovatele vlastnost tak, že názvy vlastností a popisovače vlastnosti v <xref:System.Collections.Generic.Dictionary%602>.  
  
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
  
5.  Přepsat <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> k označení, že vaše sestavení poskytuje podporu specifické pro ovládací prvek pro ovládací prvek a jeho podřízené položky.  
  
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
  
6.  Přepsat zbývající abstraktní metody <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.  
  
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
  
7.  Přidejte třídu balíček rozšíření, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
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
  
8.  Definovat `UITestExtensionPackage` atribut pro sestavení.  
  
    ```csharp  
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
                    "ChartControlExtensionPackage",  
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]  
    namespace ChartControlExtensionPackage  
    {  
       …  
    ```  
  
9. Ve třídě balíčku rozšíření přepsat <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> vrácené třída vlastnost zprostředkovatele v případě, že je požadována vlastnost zprostředkovatele.  
  
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
  
10. Přepsání zbývající abstraktní metody a vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
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
  
11. Sestavit binární soubory a zkopírujte je do **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.  
  
> [!NOTE]
>  Tento balíček rozšíření uplatní na libovolný ovládací prvek, který je typu "Text". Pokud testujete více ovládacích prvků stejného typu, musíte je samostatně otestujete a spravovat, které balíčky rozšíření se nasazují po zaznamenání testů.  
  
##  <a name="codegeneration"></a> Nepodporuje generování kódu díky implementaci třídy pro přístup k vlastní vlastnosti  
 Tvůrce programového testu uživatelského rozhraní generuje kód ze záznamu relace, používá <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> tříd pro vaše ovládací prvky přístupu.  
  
```csharp  
  
      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;  
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());  
```  
  
 Pokud jste implementovali vlastnost zprostředkovatele pro poskytnutí přístupu k vlastnosti vlastního ovládacího prvku, můžete přidat specializované třídy, který se používá pro přístup k těmto vlastnostem tak, že generovaný kód zjednodušen.  
  
```csharp  
  
      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;  
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);  
```  
  
### <a name="to-add-a-specialized-class-to-access-your-control"></a>Chcete-li přidat specializované třídy pro přístup k ovládacího prvku  
 ![CUIT&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")  
  
1.  Implementace, která je odvozena z třídy <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> a přidejte typ ovládacího prvku do kolekce vlastností vyhledávání v konstruktoru.  
  
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
  
2.  Implementace vlastních vlastností ovládacího prvku jako vlastnosti třídy.  
  
    ```csharp  
    public virtual string State  
    {  
        get  
        {  
            return (string)GetProperty("State");  
        }  
    }  
    ```  
  
3.  Přepsání poskytovatele vlastnost <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metody na návratový typ novou třídu pro křivku podřízené ovládací prvky legendy.  
  
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
  
4.  Přepsání poskytovatele vlastnost <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metody na návratový typ metody PropertyNames novou třídu.  
  
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
  
##  <a name="intentawareactions"></a> Podpora akce podporující záměr implementací filtru akce  
 Když Visual Studio zaznamenává testu, zachytí každou událost myši a klávesnice. V některých případech však můžete záměr akce ztraceno v řadu událostí myši a klávesnice. Například pokud váš ovládací prvek podporuje automatické dokončování, stejnou sadu událostí myši a klávesnice může vést k jinou hodnotu při testu je přehrávání v jiném prostředí. Můžete přidat filtr akce modulu plug-in, který nahrazuje řadu událostí klávesnice a myši pomocí jedné akce. Tímto způsobem můžete nahradit série události myši a klávesnice, což vede k výběru hodnoty pomocí jedné akce, která nastaví hodnotu. Programové testy UI způsobem, který chrání před rozdíly v automatickém dokončování z jednoho prostředí do druhého.  
  
### <a name="to-support-intent-aware-actions"></a>Pro podporu akce podporující záměr  
 ![CUIT&#95;akce](../test/media/cuit-actions.png "CUIT_Actions")  
  
1.  Implementovat třídu filtru akce, která je odvozena od <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, přepisování vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> a <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.  
  
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
  
2.  Přepsat <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. V příkladu zde realpces dvakrát klikněte na akci s jedním kliknutím na akci.  
  
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
  
3.  Přidat filtr akce <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> – metoda rozšíření balíčku.  
  
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
  
4.  Sestavit binární soubory a zkopírujte je do %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.  
  
> [!NOTE]
>  Filtr akce není závislý na implementaci usnadnění nebo zprostředkovatel vlastností.  
  
## <a name="debug-your-property-provider-or-action-filter"></a>Ladění zprostředkovatele vlastnost nebo filtr akce  
 Filtr vlastnosti zprostředkovatele a akce jsou implementované v rozšíření balíčku, který je načten a spustit pomocí Tvůrce programového testu uživatelského rozhraní v procesu nezávisle na aplikaci.  
  
#### <a name="to-debug-your-property-provider-or-action-filter"></a>Chcete-li ladit vlastnosti zprostředkovatele nebo akce filtru  
  
1.  Sestavení ladicí verze kopii balíčku rozšíření knihovny DLL a soubory PDB %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.  
  
2.  Spusťte aplikaci (ne v ladicím programu).  
  
3.  Spusťte Tvůrce programového testu uživatelského rozhraní.  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  Připojte ladicí program k procesu codedUITestBuilder.  
  
5.  Nastavte zarážky v kódu.  
  
6.  Vytvořte v Tvůrce programového testu uživatelského rozhraní, nepodmíněné výrazy pro výkon poskytovatele vlastnost a zaznamenejte akce vykonávat filtry akce.  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="guidance"></a>Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)



