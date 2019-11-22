---
title: 'Postupy: rozšiřování návrháře jazyka specifického pro doménu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 33a7f5a0f183030f9de021df328f8c5e50f5fd5a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300896"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Postupy: Rozšíření návrháře jazyka specifického pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit rozšíření pro návrháře, který použijete k úpravám definic DSL. Mezi typy rozšíření, které lze provést, patří přidávání příkazů nabídky, přidávání obslužných rutin pro gesta přetažení a pravidla, která jsou aktivována při změně konkrétního typu hodnot nebo relací. Rozšíření mohou být zabalena jako rozšíření integrace sady Visual Studio (VSIX) a distribuována jiným uživatelům.

 Vzorový kód a další informace o této funkci najdete na webu Visual Studio [vizualizace and MODELING SDK (VMSDK)](https://go.microsoft.com/fwlink/?LinkID=186128).

## <a name="setting-up-the-solution"></a>Nastavení řešení
 Nastavte projekt, který obsahuje kód vašeho rozšíření a projekt VSIX, který projekt exportuje. Vaše řešení může obsahovat další projekty, které jsou začleněny do stejného VSIX.

#### <a name="to-create-a-dsl-designer-extension-solution"></a>Vytvoření řešení rozšíření návrháře DSL

1. Vytvořte nový projekt pomocí šablony projektu Knihovna tříd. V dialogovém okně **Nový projekt** klikněte na položku **vizuál C#**  a potom v prostředním okně klikněte na **Knihovna tříd**.

     Tento projekt bude obsahovat kód vašich rozšíření.

2. Vytvořte nový projekt pomocí šablony projektu VSIX. V dialogovém okně **Nový projekt** rozbalte položku **vizuál C#** , klikněte na možnost **rozšiřitelnost**a potom v prostředním okně vyberte **projekt VSIX**.

     Vyberte možnost **Přidat do řešení**.

     Zdrojový. extension. vsixmanifest se otevře v editoru manifestu VSIX.

3. Nad polem obsah klikněte na **Přidat obsah**.

4. V dialogovém okně **Přidat obsah** nastavte **možnost vybrat typ obsahu** na **součást MEF**a nastavte **projekt** na projekt knihovny tříd.

5. Klikněte na **Vybrat edice** a ujistěte se, že je zaškrtnuté políčko **Visual Studio Enterprise** .

6. Ujistěte se, že projekt VSIX je spouštěným projektem řešení.

7. V projektu knihovny tříd přidejte odkazy na následující sestavení:

     Microsoft.VisualStudio.CoreUtility

     Microsoft.VisualStudio.Modeling.Sdk.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System. Drawing

     System. Drawing. Design

     System.Windows.Forms

## <a name="testing-and-deployment"></a>Testování a nasazení
 Chcete-li otestovat jakékoli rozšíření v tomto tématu, sestavte a spusťte řešení. Otevře se experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V této instanci otevřete řešení DSL. Úprava diagramu DslDefinition. Chování rozšíření lze zobrazit.

 Chcete-li nasadit rozšíření do hlavního [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]a do jiných počítačů, postupujte podle následujících kroků:

1. V projektu VSIX v přihrádce najít instalační soubor VSIX\\*\*\\\*.VSIX

2. Zkopírujte tento soubor do cílového počítače a potom v Průzkumníku Windows (nebo v Průzkumníku souborů) poklikejte na něj.

    Otevře se Správce rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] s potvrzením, že rozšíření bylo nainstalováno.

   K odinstalaci rozšíření použijte následující postup:

3. v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]v nabídce **nástroje** klikněte na **Správce rozšíření**.

4. Vyberte rozšíření a odstraňte ho.

## <a name="adding-a-shortcut-menu-command"></a>Přidání příkazu místní nabídky
 Chcete-li vytvořit příkaz místní nabídky na ploše návrháře DSL nebo v okně Průzkumníka DSL, napište třídu podobnou následující.

 Třída musí implementovat `ICommandExtension` a musí mít `DslDefinitionModelCommandExtension`atributu.

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handling-mouse-gestures"></a>Manipulace s gesty myši
 Kód je podobný kódu příkazu nabídky.

```
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="responding-to-value-changes"></a>Reakce na změny hodnot
 Tato obslužná rutina potřebuje model domény, aby fungovala správně. Poskytujeme jednoduchý model domény.

```
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

 Následující kód implementuje jednoduchý model. Vytvořte nový identifikátor GUID, který nahradí zástupný symbol.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```
