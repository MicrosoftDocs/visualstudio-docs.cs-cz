---
title: Zobrazení modelu UML v diagramech | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd30d626d6500f7bf904350133ea33f2b2a25ac5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757312"
---
# <a name="display-a-uml-model-on-diagrams"></a>Zobrazení modelu UML v diagramech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V programovém kódu pro rozšíření pro Visual Studio můžete řídit způsob zobrazení prvků modelu v diagramech. Pokud chcete zobrazit, které verze sady Visual Studio podporují modelech UML, naleznete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 V tomto tématu:  
 -   [K zobrazení elementu v diagramu](#Display)  
  
-   [Přístup k obrazce, které reprezentují element](#GetShapes)  
  
-   [Přesunutí a změna velikosti obrazce](#Moving)  
  
-   [Odebrání tvaru z diagramu](#Removing)  
  
-   [Otevření a vytváření diagramů](#Opening)  
  
-   [Příklad: Příkaz pro zarovnání tvarů](#AlignCommand)  
  
##  <a name="Display"></a> K zobrazení elementu v diagramu  
 Při vytváření elementu například případ použití nebo akci uživatel můžete zobrazit v Průzkumníku modelů UML, ale zřejmě není vždy automaticky v diagramu. V některých případech musíte napsat kód pro jeho zobrazení. Následující tabulka shrnuje alternativ.  
  
|Typ prvku|Příklad|Chcete-li zobrazit tuto aplikaci, musí váš kód|  
|---------------------|-----------------|-------------------------------------|  
|Třídění|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Vytvoření přidružené tvary v diagramech zadané. Můžete vytvořit libovolný počet obrazce pro každý třídění.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Nastavte `parentShape` k `null` obrazce na nejvyšší úrovni diagramu.<br /><br /> Chcete-li zobrazit jeden prvek uvnitř jiného:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **Poznámka:** provést zobrazení uvnitř **ILinkedUndo** transakce, někdy vrátí metoda ne `IShape`. Ale tvar správně vytvořeny a je přístupný pomocí `IElement.Shapes().`|  
|Podřízené třídění|Atribut, operace,<br /><br /> Část, Port|Automaticky – bez potřeby jakéhokoli kódu.<br /><br /> Zobrazí se v rámci nadřazeného elementu.|  
|Chování|Interakce (pořadí)<br /><br /> Aktivita|Chování vazby odpovídající diagramu.<br /><br /> Každý chování můžete najednou vázaný na maximálně jeden diagram.<br /><br /> Příklad:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|  
|Podřízené chování|Životností, zpráv, akce, uzly objektu|Automaticky – bez potřeby jakéhokoli kódu.<br /><br /> Pokud nadřazená je vázán na diagramu se zobrazí.|  
|Relace|Asociace, generalizace, tok, závislost|Automaticky – bez potřeby jakéhokoli kódu.<br /><br /> Zobrazí se na každý diagram, ve kterém se zobrazí oba konce.|  
  
##  <a name="GetShapes"></a> Přístup k obrazce, které reprezentují element  
 Obrazec, který reprezentuje element patří do typů:  
  
 `IShape`  
  
 `IShape<` *ElementType* `>`  
  
 kde *ElementType* , jako je typ prvku modelu `IClass` nebo `IUseCase`.  
  
|||  
|-|-|  
|`anElement.Shapes ()`|Všechny `IShapes` představující tento prvek v diagramech otevřít.|  
|`anElement.Shapes(aDiagram)`|Všechny `IShapes` , které představují tohoto elementu v diagramu konkrétní.|  
|`anIShape.GetElement()`|`IElement` , Který tvar představuje. By obvykle přetypujte ji na podtřídu třídy IElement.|  
|`anIShape.Diagram`|`IDiagram` Tvar, který obsahuje.|  
|`anIShape.ParentShape`|Obrazec, který obsahuje `anIShape`. Například tvar portu je součástí tvar součásti.|  
|`anIShape.ChildShapes`|Tvary, které jsou obsaženy v rámci `IShape` nebo `IDiagram`.|  
|`anIShape.GetChildShapes<IUseCase>()`|Tvary obsažené v rámci `IShape` nebo `IDiagram` , které představují prvků zadaného typu, jako například `IUseCase`.|  
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Přetypování obecný `IShape` k silného typu `IShape<IElement>`.|  
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Přetypování typu jeden tvar parametrizované obrazec.|  
  
##  <a name="Moving"></a> Přesunutí a změna velikosti obrazce  
  
|||  
|-|-|  
|`anIShape.Move(x, y, [width], [height])`|Přesunout nebo změnit velikost tvaru.|  
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Aktivovat okno a přejděte do diagramu tak, že daný tvary jsou viditelné. Tvary musí být v diagramu. Pokud `zoomToFit` má hodnotu true, diagram bude možné škálovat v případě potřeby tak, aby všechny tvary jsou viditelné.|  
  
 Příklad najdete v tématu [definování příkazu k zarovnání](#AlignCommand).  
  
##  <a name="Removing"></a> Odebrání tvaru z diagramu  
 Tvary některé typy prvků můžete odstranit bez odstranění prvku.  
  
|Prvek modelu|Odebrání tvaru|  
|-------------------|-------------------------|  
|Třídění: třída, rozhraní, výčtu, objektu actor, případu použití nebo komponenty|`shape.Delete();`|  
|Chování: aktivitu nebo interakci|Diagram lze odstranit z projektu. Použití `IDiagram.FileName` k získání cesty.<br /><br /> Toto chování neodstraní z modelu.|  
|Žádný obrazec|Jiné tvary nelze explicitně odstranit z diagramu. Tvar automaticky zavře, pokud prvek je odstraněn z modelu, nebo pokud je nadřazený obrazec odstraněn z diagramu.|  
  
##  <a name="Opening"></a> Otevření a vytváření diagramů  
  
### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Pro přístup k aktuálnímu diagramu uživatele z rozšíření příkazu nebo gesta  
 Deklarujte tento importovanou vlastnost ve třídě:  
  
 `[Import]`  
  
 `IDiagramContext Context { get; set; }`  
  
 V metodě přístup k diagramu:  
  
 `IClassDiagram classDiagram =`  
  
 `Context.CurrentDiagram as IClassDiagram;`  
  
> [!NOTE]
>  Instance `IDiagram` (a jejich podtypy jako `IClassDiagram`) je platné pouze uvnitř příkazu se zpracovávají. Nedoporučuje se zachovat `IDiagram` objekt v proměnné, který bude zachován, když ovládací prvek se vrátí uživateli.  
  
 Další informace najdete v tématu [definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="to-obtain-a-list-of-open-diagrams"></a>Získat seznam otevřít diagramů  
 Seznam diagramy, které jsou právě otevřeny v projektu:  
  
```  
Context.CurrentDiagram.ModelStore.Diagrams()  
```  
  
## <a name="to-access-the-diagrams-in-a-project"></a>Pro přístup k diagramy v projektu  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Rozhraní API můžete použít pro otevírání a tvorbu projekty modelování a diagramy.  
  
 Všimněte si, že přetypování z typu `EnvDTE.ProjectItem` k `IDiagramContext`.  
  
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
  
 Instance `IDiagram` a jejich podtypy nejsou platné po návratu do ovládacího prvku na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Můžete také získat úložiště z modelu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu:  
  
```  
  
      Project project = ...;  
IModelStore modelStore = (project as IModelingProject).Store;  
```  
  
##  <a name="AlignCommand"></a> Příklad: Příkaz pro zarovnání tvarů  
 Následující kód implementuje příkaz nabídky, který elegantně zarovná obrazce. Uživatel musí nejprve umístěte dva nebo více obrazců v přibližné zarovnání, vertikálně nebo horizontálně. Potom příkaz Zarovnat slouží k zarovnání jejich centra.  
  
 Zpřístupnění příkazu, tento kód vložte do projekt příkazu nabídky a pak nasadit výsledné rozšíření pro vaše uživatele. Další informace najdete v tématu [definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
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
  // See http://msdn.microsoft.com/library/ee329481.aspx  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension] // TODO: Add other diagram types if needed  
  class CommandExtension : ICommandExtension  
  {  
    /// <summary>  
    /// See http://msdn.microsoft.com/library/ee329481.aspx  
    /// </summary>  
    [Import]  
    IDiagramContext context { get; set; }  
  
    /// <summary>  
    /// Transaction context.  
    /// See http://msdn.microsoft.com/library/ee330926.aspx  
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
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Procházení modelu UML](../modeling/navigate-the-uml-model.md)   
 [Ukázka: Zarovnání tvarů v diagramu příkazu nabídky](http://go.microsoft.com/fwlink/?LinkId=213809)   
 [Ukázka: Vytvoření prvky, tvary a stereotypy](http://go.microsoft.com/fwlink/?LinkId=213811)



