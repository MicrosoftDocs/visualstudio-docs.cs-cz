---
title: 'Postupy: Rozšíření návrháře jazyka specifického pro doménu'
description: Zjistěte, jak můžete v návrháři vytvořit rozšíření, která používáte k úpravám definic jazyka specifického pro doménu (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9354e3b846f48a79aa5cdd0f39a159bd007cdd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387214"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Postupy: Rozšíření návrháře jazyka specifického pro doménu

Můžete vytvořit rozšíření pro návrháře, která slouží k úpravám definic DSL. Mezi typy rozšíření, které můžete vytvořit, patří přidání příkazů nabídky, přidání obslužných rutin pro gesta přetažení a dvojitého kliknutí a pravidla, která se spustí při změně konkrétních typů hodnot nebo relací. Rozšíření lze zabalovat jako rozšíření Visual Studio integrace (VSIX) a distribuovat ostatním uživatelům.

Ukázkový kód a další informace o této funkci najdete v tématu Visual Studio [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

## <a name="set-up-the-solution"></a>Nastavení řešení

Nastavte projekt, který obsahuje kód vašeho rozšíření, a projekt VSIX, který exportuje projekt. Vaše řešení může obsahovat další projekty, které jsou začleněné do stejného VSIX.

### <a name="to-create-a-dsl-designer-extension-solution"></a>Vytvoření řešení rozšíření návrháře DSL

1. Vytvořte nový projekt pomocí **šablony projektu Knihovna** tříd. Tento projekt bude obsahovat kód vašich rozšíření.

2. Vytvořte nový projekt **projektu VSIX.**

     Vyberte **Přidat do řešení.**

     *Source.extension.vsixmanifest* se otevře v editoru manifestu VSIX.

3. Nad polem Obsah klikněte na **Přidat obsah.**

4. V dialogovém okně **Přidat** obsah nastavte Vybrat typ obsahu  na **Součást MEF** **a** projekt nastavte na projekt knihovny tříd.

5. Klikněte **na Vybrat edice** a ujistěte se, **Visual Studio Enterprise** je zaškrtnuté.

6. Ujistěte se, že projekt VSIX je spouštěný projekt řešení.

7. V projektu knihovny tříd přidejte odkazy na následující sestavení:

     Microsoft.VisualStudio.CoreUtility

     Microsoft.VisualStudio.Modeling.Sdk.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.drawing

     System.drawing.design

     System.windows.forms

## <a name="test-and-deployment"></a>Testování a nasazení

Pokud chcete otestovat jakékoli rozšíření v tomto tématu, sestavte a spusťte řešení. Otevře se experimentální Visual Studio aplikace. V tomto případě otevřete řešení DSL. Upravte diagram DslDefinition. Chování rozšíření je vidět.

Pokud chcete nasadit rozšíření do hlavního Visual Studio a do jiných počítačů, postupujte takto:

1. Vyhledejte instalační soubor VSIX v projektu VSIX v souboru bin \\ * \\ \* .vsix.

2. Zkopírujte tento soubor do cílového počítače a potom Průzkumník Windows (nebo Průzkumník souborů) poklikejte na něj.

     Otevře Visual Studio Správce rozšíření a potvrdí, že je rozšíření nainstalované.

Pokud chcete rozšíření odinstalovat, postupujte takto:

1. V Visual Studio klikněte v **nabídce Nástroje** na **Správce rozšíření**.

2. Vyberte rozšíření a odstraňte ho.

## <a name="add-a-shortcut-menu-command"></a>Přidání příkazu místní nabídky

Pokud chcete, aby se příkaz místní nabídky objevil na ploše návrháře DSL nebo v okně průzkumníka DSL, napište třídu podobající se následujícímu.

Třída musí implementovat a `ICommandExtension` musí mít atribut `DslDefinitionModelCommandExtension` .

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

## <a name="handle-mouse-gestures"></a>Zpracování gest myši

Kód se podobá kódu příkazu nabídky.

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

## <a name="respond-to-value-changes"></a>Reakce na změny hodnot

Tato obslužná rutina potřebuje doménový model, aby správně fungovala. Poskytujeme jednoduchý doménový model.

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

Následující kód implementuje jednoduchý model. Vytvořte nový identifikátor GUID, který nahradí zástupný symbol.

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