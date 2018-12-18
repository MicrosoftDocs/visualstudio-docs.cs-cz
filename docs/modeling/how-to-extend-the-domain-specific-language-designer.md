---
title: 'Postupy: Rozšíření návrháře jazyka specifického pro doménu'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6a2388619dea31696fe4416032cc12cd1fe5b372
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860365"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Postupy: Rozšíření návrháře jazyka specifického pro doménu

Můžete provést rozšíření návrháře, který použijete k úpravám definic DSL. Typy rozšíření, které můžete provést zahrnují přidání příkazy nabídek, přidání obslužné rutiny pro přetažení a dvakrát klikněte na panel gesta a pravidla, která se spustí při změně konkrétních typů hodnot nebo vztahy. Rozšíření můžete zabalit jako Visual Studio integrace rozšíření (VSIX) a distribuovat ostatním uživatelům.

Ukázkový kód a další informace o této funkci najdete v tématu Visual Studio [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

## <a name="set-up-the-solution"></a>Nastavení řešení

Nastavení, která obsahuje kód vaše rozšíření projektu a projekt VSIX, který exportuje projektu. Řešení může obsahovat jiné projekty, které jsou začleněny do stejného VSIX.

### <a name="to-create-a-dsl-designer-extension-solution"></a>K vytvoření řešení rozšíření návrháře DSL

1.  Vytvoření nového projektu pomocí šablony projektu knihovny tříd. V **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#** a v prostřední okna klikněte na **knihovny tříd**.

     Tento projekt bude obsahovat kódu rozšíření.

2.  Vytvoření nového projektu pomocí šablony projektu VSIX. V **nový projekt** dialogového okna rozbalte **Visual C#**, klikněte na tlačítko **rozšiřitelnost**a potom v prostředním okně vyberte **projekt VSIX**.

     Vyberte **přidat do řešení**.

     Source.extension.vsixmanifest se otevře v editoru manifestu VSIX.

3.  Nad pole obsahu, klikněte na tlačítko **přidat obsah**.

4.  V **přidat obsah** dialogové okno, nastavte **vyberte typ obsahu** k **Komponenta MEF**a nastavte **projektu** do projektu knihovny tříd.

5.  Klikněte na tlačítko **vybrat vydání** a ujistěte se, že **Visual Studio Enterprise** je zaškrtnuté políčko.

6.  Ujistěte se, že projekt VSIX je projekt při spuštění řešení.

7.  V projektu knihovny tříd přidejte odkazy na následující sestavení:

     Microsoft.VisualStudio.CoreUtility

     Microsoft.VisualStudio.Modeling.Sdk.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     System.Windows.Forms

## <a name="test-and-deployment"></a>Testování a nasazení

Chcete-li testovat žádný rozšíření v tomto tématu, sestavte a spusťte řešení. Otevře se experimentální instanci sady Visual Studio. V tomto případě otevřete řešení DSL. DslDefinition diagram upravte. Můžete zobrazit chování rozšíření.

Pokud chcete nasadit rozšíření do hlavní sady Visual Studio a na jiné počítače, postupujte takto:

1.  V projektu VSIX v přihrádce najít instalační soubor VSIX\\*\*\\\*.VSIX

2.  Zkopírujte tento soubor do cílového počítače a v Průzkumníku Windows (nebo Průzkumníka souborů), poklepejte na něj.

     Správce rozšíření sady Visual Studio otevře potvrďte, že je nainstalovaná rozšíření.

Toto rozšíření odinstalovat, postupujte podle těchto kroků:

1.  V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **Správce rozšíření**.

2.  Vyberte požadované rozšíření a odstranit ji.

## <a name="add-a-shortcut-menu-command"></a>Přidat příkaz místní nabídky

Chcete-li příkaz místní nabídky, se zobrazí na povrchu návrháře DSL nebo v okně Průzkumník DSL, zápis připomínající následující třídy.

Musí implementovat třídu `ICommandExtension` a musí mít atribut `DslDefinitionModelCommandExtension`.

```csharp
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

## <a name="handle-mouse-gestures"></a>Zpracování gesta myší

Kód je podobný kód příkazu nabídky.

```csharp
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

## <a name="respond-to-value-changes"></a>Reakce na změny hodnoty

Tato obslužná rutina musí modelu domény mohly fungovat správně. Zajišťuje jednoduché doménový model.

```csharp
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

Následující kód implementuje jednoduchého modelu. Vytvořte nový identifikátor GUID nahraďte zástupný symbol.

```csharp
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