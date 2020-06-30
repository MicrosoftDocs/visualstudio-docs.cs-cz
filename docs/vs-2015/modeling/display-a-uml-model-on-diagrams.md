---
title: Zobrazení modelu UML v diagramech | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06a22161068dd7604fe7bb4153e322c0954b89d2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533015"
---
# <a name="display-a-uml-model-on-diagrams"></a>Zobrazení modelu UML v diagramech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V kódu programu pro rozšíření sady Visual Studio můžete řídit způsob zobrazení prvků modelu v diagramech. Chcete-li zjistit, které verze aplikace Visual Studio podporují modely UML, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

V tomto tématu:
- [Zobrazení prvku v diagramu](#Display)

- [Přístup k tvarům, které reprezentují element](#GetShapes)

- [Přesun a změna velikosti tvarů](#Moving)

- [Odebrání tvaru z diagramu](#Removing)

- [Otevírání a vytváření diagramů](#Opening)

- [Příklad: příkaz pro zarovnání obrazců](#AlignCommand)

## <a name="to-display-an-element-on-a-diagram"></a><a name="Display"></a>Zobrazení prvku v diagramu
 Při vytváření prvku, jako je například případ použití nebo akce, ho uživatel uvidí v Průzkumníku modelů UML, ale v diagramu se nemusí vždy automaticky zobrazovat. V některých případech je nutné napsat kód pro zobrazení. V následující tabulce jsou shrnuty alternativy.

|Typ elementu|Například|Chcete-li toto zobrazení zobrazit, váš kód musí|
|---------------------|-----------------|-------------------------------------|
|Třídění|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Vytvoření přidružených tvarů na zadaných diagramech. Pro jednotlivé klasifikátory můžete vytvořit libovolný počet tvarů.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Nastavte `parentShape` na `null` pro tvar na nejvyšší úrovni diagramu.<br /><br /> Zobrazení jednoho obrazce v jiném:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);`**Poznámka:**  Pokud provedete zobrazení uvnitř transakce **ILinkedUndo** , metoda někdy vrátí hodnotu No `IShape` . Ale tvar je správně vytvořen a je přístupný pomocí`IElement.Shapes().`|
|Podřízená položka třídění|Atribut, operace,<br /><br /> Součást, port|Automatický – není vyžadován žádný kód.<br /><br /> Zobrazuje se jako součást nadřazeného objektu.|
|Chování|Interakce (sekvence),<br /><br /> Aktivita|Navažte chování na příslušný diagram.<br /><br /> Každé chování může být vázáno na maximálně jeden diagram najednou.<br /><br /> Příklad:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|
|Podřízený objekt chování|Životnosti, zprávy, akce, uzly objektů|Automatický – není vyžadován žádný kód.<br /><br /> Je zobrazen, pokud je nadřazený objekt svázán s diagramem.|
|Relace|Asociace, generalizace, tok, závislost|Automatický – není vyžadován žádný kód.<br /><br /> Zobrazuje se na každém diagramu, na kterém jsou zobrazeny oba konce.|

## <a name="accessing-the-shapes-that-represent-an-element"></a><a name="GetShapes"></a>Přístup k tvarům, které reprezentují element
 Obrazec představující prvek patří do těchto typů:

 `IShape`

 `IShape<`*ElementType*`>`

 kde *ElementType* je typ prvku modelu, například `IClass` nebo `IUseCase` .

|Syntax|Popis|
|-|-|
|`anElement.Shapes ()`|Všechny `IShapes` , které představují tento prvek v otevřených diagramech.|
|`anElement.Shapes(aDiagram)`|Všechny `IShapes` , které reprezentují tento prvek na konkrétním diagramu.|
|`anIShape.GetElement()`|`IElement`Který tvar představuje. Normálně byste ji přetypování na podtřídu třídy IElement.|
|`anIShape.Diagram`|`IDiagram`, Který obsahuje tvar.|
|`anIShape.ParentShape`|Tvar, který obsahuje `anIShape` . Například obrazec portu je obsažen v obrazci součásti.|
|`anIShape.ChildShapes`|Tvary obsažené v `IShape` nebo `IDiagram` .|
|`anIShape.GetChildShapes<IUseCase>()`|Tvary obsažené v `IShape` nebo `IDiagram` , které reprezentují prvky zadaného typu, například `IUseCase` .|
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Přetypování obecné `IShape` na silně typované `IShape<IElement>` .|
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Přetypování tvaru z jednoho parametrizovaného typu obrazce na jiný.|

## <a name="moving-and-resizing-shapes"></a><a name="Moving"></a>Přesun a změna velikosti tvarů

|Syntax|Popis|
|-|-|
|`anIShape.Move(x, y, [width], [height])`|Přesune nebo změní velikost obrazce.|
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Aktivujte okno a posuňte diagram tak, aby byly všechny dané obrazce viditelné. Všechny obrazce musí být v diagramu. Pokud `zoomToFit` má hodnotu true, diagram bude v případě potřeby upravený tak, aby všechny obrazce byly viditelné.|

 Příklad naleznete v tématu [Definování příkazu zarovnání](#AlignCommand).

## <a name="to-remove-a-shape-from-a-diagram"></a><a name="Removing"></a>Odebrání tvaru z diagramu
 Můžete odstranit tvary některých typů elementu bez odstranění elementu.

|Element modelu|Odebrání obrazce|
|-------------------|-------------------------|
|Klasifikátor: třída, rozhraní, výčet, objekt actor, případ použití nebo komponenta|`shape.Delete();`|
|Chování: interakce nebo aktivita|Diagram můžete z projektu odstranit. Použijte `IDiagram.FileName` k získání cesty.<br /><br /> Tím se chování z modelu neodstraní.|
|Jakýkoli jiný tvar|Nelze explicitně odstranit jiné tvary z diagramu. Tvar bude automaticky zmizet, pokud je prvek odstraněn z modelu, nebo pokud je nadřazený tvar odebrán z diagramu.|

## <a name="opening-and-creating-diagrams"></a><a name="Opening"></a>Otevírání a vytváření diagramů

### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Přístup k aktuálnímu diagramu uživatele z rozšíření příkazu nebo gesta
 Deklarovat tuto importovanou vlastnost ve třídě:

 `[Import]`

 `IDiagramContext Context { get; set; }`

 V metodě získáte přístup k diagramu:

 `IClassDiagram classDiagram =`

 `Context.CurrentDiagram as IClassDiagram;`

> [!NOTE]
> Instance `IDiagram` (a její podtypy jako `IClassDiagram` ) je platná pouze v rámci příkazu, který zpracováváte. Nedoporučuje se uchovávat `IDiagram` objekt v proměnné, která zůstává v průběhu řízení vráceného uživateli.

 Další informace najdete v tématu [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

### <a name="to-obtain-a-list-of-open-diagrams"></a>Získání seznamu otevřených diagramů
 Seznam diagramů, které jsou aktuálně otevřeny v projektu:

```
Context.CurrentDiagram.ModelStore.Diagrams()
```

## <a name="to-access-the-diagrams-in-a-project"></a>Přístup k diagramům v projektu
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Rozhraní API je možné použít k otevření a vytvoření modelů a diagramů modelování.

 Všimněte si přetypování z `EnvDTE.ProjectItem` na `IDiagramContext` .

```

      using EnvDTE; // Visual Studio API
...
[Import]
public IServiceProvider ServiceProvider { get; set; }
...
// Get Visual Studio API
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;
// Get current Visual Studio project
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
// Open and process every diagram in the project.
foreach (ProjectItem item in project.ProjectItems)
{
  // Cast ProjectItem to IDiagramContext
  IDiagramContext context = item as IDiagramContext;
  if (context == null)
  {
     // This is not a diagram file.
     continue;
  }
  // Open the file and give the window the focus.
  if (!item.IsOpen)
  {
      item.Open().Activate();
  }
  // Get the diagram.
  IDiagram diagram = context.CurrentDiagram;
  // Deal with specific diagram types.
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;
  if (seqDiagram != null)
  { ... } } }
```

 Instance `IDiagram` a jejich podtypy nejsou platné po vrácení řízení do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Můžete také získat úložiště modelu z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu:

```

      Project project = ...;
IModelStore modelStore = (project as IModelingProject).Store;
```

## <a name="example-command-for-aligning-shapes"></a><a name="AlignCommand"></a>Příklad: příkaz pro zarovnání obrazců
 Následující kód implementuje příkaz nabídky, který zarovnává tvary na úhledný. Uživatel musí nejdřív umístit dva nebo více tvarů v přibližném zarovnání, a to buď vertikálně, nebo vodorovně. Pak můžete použít příkaz align k zarovnání svých Center.

 Aby byl příkaz dostupný, přidejte tento kód do projektu příkazu nabídky a potom nasaďte výsledné rozšíření pro vaše uživatele. Další informace najdete v tématu [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace AlignCommand
{
  // Implements a command to align shapes in a UML class diagram.
  // The user first selects shapes that are roughly aligned either vertically or horizontally.
  // This command will straighten them up.

  // Place this file in a menu command extension project.
  // See https://msdn.microsoft.com/library/ee329481.aspx

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension] // TODO: Add other diagram types if needed
  class CommandExtension : ICommandExtension
  {
    /// <summary>
    /// See https://msdn.microsoft.com/library/ee329481.aspx
    /// </summary>
    [Import]
    IDiagramContext context { get; set; }

    /// <summary>
    /// Transaction context.
    /// See https://msdn.microsoft.com/library/ee330926.aspx
    /// </summary>
    [Import]
    ILinkedUndoContext linkedUndo { get; set; }

    /// <summary>
    /// Called when the user selects the command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      Align(context.CurrentDiagram.SelectedShapes);
    }

    /// <summary>
    /// Called when the user right-clicks on the diagram.
    /// Determines whether the command is enabled.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;
      // Make it visible if there are shapes selected:
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);

      // Make it enabled if there are two or more shapes that are roughly in line:
      command.Enabled = currentSelection.Count() > 1
        && (HorizontalAlignCenter(currentSelection) > 0.0
        || VerticalAlignCenter(currentSelection) > 0.0);

    }

    /// <summary>
    /// Title of the menu command.
    /// </summary>
    public string Text
    {
      get { return "Align Shapes"; }
    }

    /// <summary>
    /// Find a horizontal line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)
    {
      double Y = -1.0;
      double top = 0.0, bottom = shapes.First().Bottom();
      foreach (IShape shape in shapes)
      {
        top = Math.Max(top, shape.Top());
        bottom = Math.Min(bottom, shape.Bottom());
      }
      if (bottom > top) Y = (bottom + top) / 2.0;
      return Y;
    }

    /// <summary>
    /// Find a vertical line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)
    {
      double X = -1.0;
      double left = 0.0, right = shapes.First().Right();
      foreach (IShape shape in shapes)
      {
        left = Math.Max(left, shape.Left());
        right = Math.Min(right, shape.Right());
      }
      if (right > left) X = (right + left) / 2.0;
      return X;
    }

    /// <summary>
    /// Line up those shapes that are roughly aligned.
    /// </summary>
    /// <param name="shapes"></param>
    private void Align(IEnumerable<IShape> shapes)
    {
      if (shapes.Count() > 1)
      {
        // The shapes must all overlap either horizontally or vertically.
        // Find a horizontal line that is covered by all the shapes:
        double Y = HorizontalAlignCenter(shapes);
        if (Y > 0.0) // Negative if they don't overlap.
        {
          // Adjust all the shape positions in one transaction:
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
          {
            foreach (IShape shape in shapes)
            {
              shape.AlignYCenter(Y);
            }
            t.Commit();
          }
        }
        else
        {
          // Find a vertical line that is covered by all the shapes:
          double X = VerticalAlignCenter(shapes);
          if (X > 0.0) // Negative if they don't overlap.
          {
            // Adjust all the shape positions in one transaction:
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
            {
              foreach (IShape shape in shapes)
              {
                shape.AlignXCenter(X);
              }
              t.Commit();
            }
          }
        }
      }
    }
  }

  /// <summary>
  /// Convenience extensions for IShape.
  /// </summary>
  public static class IShapeExtension
  {
    public static double Bottom(this IShape shape)
    {
      return shape.YPosition + shape.Height;
    }

    public static double Top(this IShape shape)
    {
      return shape.YPosition;
    }

    public static double Left(this IShape shape)
    {
      return shape.XPosition;
    }

    public static double Right(this IShape shape)
    {
      return shape.XPosition + shape.Width;
    }

    public static void AlignYCenter(this IShape shape, double Y)
    {
      shape.Move(shape.XPosition, Y - shape.YCenter());
    }

    public static void AlignXCenter(this IShape shape, double X)
    {
      shape.Move(X - shape.XCenter(), shape.YPosition);
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double YCenter(this IShape shape)
    {
        return shape.Height / 2.0;
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double XCenter(this IShape shape)
    {
        return shape.Width / 2.0;
    }
  }
}

```

## <a name="see-also"></a>Viz také
 [Rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [Navigace v modelu UML](../modeling/navigate-the-uml-model.md)
 