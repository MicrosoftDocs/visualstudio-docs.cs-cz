---
title: Přizpůsobení chování kopírování
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6839385e64503ce939d5244b116a9f24be786395
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904437"
---
# <a name="customizing-copy-behavior"></a>Přizpůsobení chování kopírování
V jazyce specifickém pro doménu (DSL) vytvořené pomocí Visual Studio Visualization and Modeling SDK je možné změnit, co se stane, když uživatel zkopíruje a vloží prvky.

## <a name="standard-copy-and-paste-behavior"></a>Standardní kopírování a vložení chování
 Chcete-li povolit, kopírování, nastavte **povolit kopírování vkládání** vlastnost **Editor** uzel v Průzkumník DSL.

 Ve výchozím nastavení když uživatel zkopíruje prvky do schránky, tyto prvky jsou zkopírovány také:

- Vloženého následníků vybraných elementů. (To znamená, elementy, které jsou cílem vkládání vztahy, které jsou zdrojem na zkopíruje prvky.)

- Propojení vztahů mezi zkopírované elementy.

  Toto pravidlo aplikuje rekurzivně zkopírované elementy a odkazy.

  ![Zkopírované a vložené prvky](../modeling/media/dslcopypastedefault.png)

  Serializovat a uložená v zkopírované elementy a odkazy <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), která je umístěna do schránky.

  Obrázek zkopírované elementy je také umístěná do schránky. To umožňuje uživateli vkládat do jiných aplikací, jako je Word.

  Uživatel můžete vložit zkopírované elementy na cíl, který může přijmout prvky podle definici DSL. V DSL generován ze šablony řešení komponenty, například uživatele můžete vložit portů do komponenty, ale ne do diagramu; a můžete vložit součásti do diagramu, ale ne na jiných komponent.

## <a name="customizing-copy-and-paste-behavior"></a>Úpravy, kopírování a vložení chování
 Další informace o přizpůsobení modelu pomocí kódu programu najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 **Povolit nebo zakázat kopírování, vyjmutí a vložení.**
V Průzkumníku DSL nastavte **povolit kopírování vkládání** vlastnost **Editor** uzlu.

 **Zkopírujte odkazy do stejného cíle.** Například máte pole zkopírovaný komentář propojenou stejného elementu předmět.
Nastavte **šíří kopírování** vlastnost roli, kterou chcete **šířit kopírování propojení pouze**. Další informace najdete v tématu [přizpůsobení chování kopírování odkaz](#customizeLinks).

 Zkopírujte propojené prvky. Například při kopírování nový prvek kopie zaškrtnutí polí, která propojené komentáře probíhají také.
Nastavte **šíří kopírování** vlastnost roli, kterou chcete **šířit Kopírovat odkaz a Aktér opačné role**. Další informace najdete v tématu [přizpůsobení chování kopírování odkaz](#customizeLinks).

 **Rychle duplicitní prvky zkopírováním a vložením.** Za normálních okolností je stále vybraná položka, kterou jste zkopírovali, a nelze vložit stejný typ prvku problém napravit.
Přidat direktiva sloučení elementů doménové třídy a nastavte ho na dopředné sloučení do nadřazené třídy. To bude mít stejný vliv na operace přetažení. Další informace najdete v tématu [přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md).

 \- nebo –

 Vyberte diagramu před vložením prvky, tak, že přepíšete `ClipboardCommandSet.ProcessOnPasteCommand()`. Přidejte tento kód do vlastního souboru v projektu DslPackage:

```csharp
namespace Company.MyDsl {
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
partial class MyDslClipboardCommandSet
{
  protected override void ProcessOnMenuPasteCommand()
  {
 // Deselect the current selection after copying:
 Diagram diagram = (this.CurrentModelingDocView as SingleDiagramDocView).Diagram;
    this.CurrentModelingDocView
     .SelectObjects(1, new object[] { diagram }, 0);
  }
} }
```

 **Vytvořte další odkazy, když uživatel vloží do vybraného cíle.** Například pole komentář vloženého na element, vytvoří se propojení mezi nimi.
Přidat direktivě sloučení do cílové doménové třídy a nastavit ji zpracovat tak, že přidáte odkazy sloučení. To bude mít stejný vliv na operace přetažení. Další informace najdete v tématu [přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md).

 \- nebo –

 Přepsat `ClipboardCommandSet.ProcessOnPasteCommand()` po volání metody základní vytvářet další odkazy.

 **Přizpůsobit formáty, ve kterých je možné zkopírovat prvky** do externí aplikace – například pro přidání ohraničení k formuláři rastrového obrázku.
Přepsat *MyDsl* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` DslPackage projektu.

 **Přizpůsobte, jak jsou elementy zkopírovány do schránky. pomocí příkazu Kopírovat, ale ne v operaci přetažení.**
Přepsat *MyDsl* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` DslPackage projektu.

 **Zachovat obrazce rozložení prostřednictvím kopírování a vložení.**
Když uživatel zkopíruje více tvarů, můžete zachovat jejich relativní umístění, když jsou vloženy. Tato technika je znázorněn příklad v [vmsdk následující položky: Ukázka okruhů](http://go.microsoft.com/fwlink/?LinkId=213879).

 Tohoto efektu dosáhnete tak, přidejte do zkopírovaný ElementGroupPrototype obrazců a konektorů. Nejvíce vhodnou metodu pro přepsání je ElementOperations.CreateElementGroupPrototype(). Chcete-li to provést, přidejte následující kód do projektu Dsl:

```csharp

public class MyElementOperations : DesignSurfaceElementOperations
{
  // Create an EGP to add to the clipboard.
  // Called when the elements to be copied have been
  // collected into an ElementGroup.
 protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
  {
 // Add the shapes and connectors:
 // Get the elements already in the group:
    ModelElement[] mels = elementGroup.ModelElements
        .Concat(elementGroup.ElementLinks) // Omit if the paste target is not the diagram.
        .ToArray();
 // Get their shapes:
    IEnumerable<PresentationElement> shapes =
       mels.SelectMany(mel =>
            PresentationViewsSubject.GetPresentation(mel));
    elementGroup.AddRange(shapes);

 return base.CreateElementGroupPrototype
           (elementGroup, elements, closureType);
  }

 public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
  { }
}

// Replace the standard ElementOperations
// singleton with your own:
partial class MyDslDiagram // EDIT NAME
{
 /// <summary>
 /// Singleton ElementOperations attached to this diagram.
 /// </summary>
 public override DesignSurfaceElementOperations ElementOperations
  {
 get
    {
 if (singleton == null)
      {
        singleton = new MyElementOperations(this.Store as IServiceProvider, this);
      }
 return singleton;
    }
  }
 private MyElementOperations singleton = null;
}
```

 **Vkládání obrazců do zvoleného umístění, jako je aktuální pozice kurzoru.**
Když uživatel zkopíruje více tvarů, můžete zachovat jejich relativní umístění, když jsou vloženy. Tato technika je znázorněn příklad v [vmsdk následující položky: Ukázka okruhů](http://go.microsoft.com/fwlink/?LinkId=213879).

 Tohoto efektu dosáhnete tak, přepsat `ClipboardCommandSet.ProcessOnMenuPasteCommand()` použije umístění konkrétní verzi `ElementOperations.Merge()`. Chcete-li to provést, přidejte následující kód v projektu DslPackage:

```csharp

partial class MyDslClipboardCommandSet // EDIT NAME
{
   /// <summary>
    /// This method assumes we only want to paste things onto the diagram
    /// - not onto anything contained in the diagram.
    /// The base method pastes in a free space on the diagram.
    /// But if the menu was used to invoke paste, we want to paste in the cursor position.
    /// </summary>
    protected override void ProcessOnMenuPasteCommand()
    {

  NestedShapesSampleDocView docView = this.CurrentModelingDocView as NestedShapesSampleDocView;

      // Retrieve data from clipboard:
      System.Windows.Forms.IDataObject data = System.Windows.Forms.Clipboard.GetDataObject();

      Diagram diagram = docView.CurrentDiagram;
      if (diagram == null) return;

      if (!docView.IsContextMenuShowing)
      {
        // User hit CTRL+V - just use base method.

        // Deselect anything that's selected, otherwise
        // pasted item will be incompatible:
        if (!this.IsDiagramSelected())
        {
          docView.SelectObjects(1, new object[] { diagram }, 0);
        }

        // Paste into a convenient spare space on diagram:
    base.ProcessOnMenuPasteCommand();
      }
      else
      {
        // User right-clicked - paste at mouse position.

        // Utility class:
        DesignSurfaceElementOperations op = diagram.ElementOperations;

        ShapeElement pasteTarget = diagram;

        // Check whether what's in the paste buffer is acceptable on the target.
        if (pasteTarget != null && op.CanMerge(pasteTarget, data))
        {

        // Although op.Merge would be a no-op if CanMerge failed, we check CanMerge first
          // so that we don't create an empty transaction (after which Undo would be no-op).
          using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("paste"))
          {
            PointD place = docView.ContextMenuMousePosition;
            op.Merge(pasteTarget, data, PointD.ToPointF(place));
            t.Commit();
          }
        }
      }
    }
  }
```

 **Umožní uživateli přetáhnout prvky.**
Zobrazit [postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="customizeLinks"></a> Přizpůsobení chování kopírování propojení
 Když uživatel zkopíruje element, standardní chování je, že všechny vložené prvky jsou zkopírovány také. Standardní chování kopírování můžete upravit. V definici DSL vybrat roli na jedné straně relace a okno sady vlastností **šíří kopírování** hodnotu.

 ![Rozšíří kopírování Vlastnosti rolí domény](../modeling/media/dslpropagatescopy.png)

 Existují tři hodnoty:

- Nejsou rozšířena kopírování

- Šíření kopírování propojení pouze - vloženého skupině novou kopii tohoto odkazu se odkazovat na existující prvek na druhém konci odkazu.

- Šíření kopírování propojení a Aktér opačné role - zkopírovaný skupina obsahuje kopii elementu na druhém konci odkazu.

  ![Kopírování s PropagateCopyToLinkOnly efekt](../modeling/media/dslpropagatecopy.png)

  Změna, kterou bude mít vliv na elementy a obrázek, který se zkopíruje.

## <a name="programming-copy-and-paste-behavior"></a>Programování kopírování a vložení chování
 Mnoho aspektů DSL chování s ohledem na kopírování, vložení, vytváření a odstraňování objektů se řídí instance <xref:Microsoft.VisualStudio.Modeling.ElementOperations> , který je s velkou provázaností do diagramu. Můžete změnit chování vašeho kódu DSL odvozením vlastních tříd z <xref:Microsoft.VisualStudio.Modeling.ElementOperations> a přepsáním <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> vlastnosti diagramu třídy.

> [!TIP]
>  Další informace o přizpůsobení modelu pomocí kódu programu najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 ![Sekvenční diagram pro operace kopírování](../modeling/media/dslcopyseqdiagram.png)

 ![Sekvenční diagram operaci vložení](../modeling/media/dslpasteseqdiagram.png)

#### <a name="to-define-your-own-elementoperations"></a>Chcete-li definovat vlastní ElementOperations

1. V novém souboru ve vašem projektu DSL, vytvořte třídu, která je odvozena od <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations>.

2. Přidáte definici částečné třídy pro třídu diagramu. Název této třídy lze najít v **Dsl\GeneratedCode\Diagrams.cs**.

    V diagramu tříd, přepište <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> vrátit instanci vaší ElementOperations podtřídy. Měli byste vrátit stejnou instanci při každém volání.

   Přidejte tento kód v souboru vlastního kódu v projektu DslPackage:

```csharp

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;

  public partial class MyDslDiagram
  {
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, MyDslDiagram diagram)
      : base(serviceProvider, diagram)
    { }
    // Overridden methods follow
  }
```

## <a name="receiving-items-dragged-from-other-models"></a>Příjem položek přetáhnout z dalších modelů
 ElementOperations lze také definovat chování kopírování, přesunutí, odstranění a přetáhněte myší. Jako ukázkový používání ElementOperations zde příklad definuje vlastní chování a přetažení. Ale pro tento účel můžete zvážit alternativní postupu popsaného v [postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md), což je více rozšiřitelné.

 Ve své třídě ElementOperations definujte dvě metody:

-   `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` který určuje, zda source element můžete přetahovat do tvar target, konektoru nebo diagramu.

-   `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` zahrnující prvek zdroje do cíle.

### <a name="canmerge"></a>CanMerge()
 `CanMerge()` je volána k určení zpětnou vazbu, která by se měly provádět uživateli při pohybu myši v diagramu. Parametry metody jsou elementu nad tím, které je najedete myší a údaje o zdroji, odkud byla provedena operace přetažení. Uživatel můžete přetáhnout z libovolné místo na obrazovce. Zdrojový objekt proto může být mnoho různých typů a je možné serializovat v různých formátech. Pokud je zdroj modelu DSL nebo UML, parametr data je serializace <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Operace přetažení, kopírování a sady nástrojů znázornit ElementGroupPrototypes fragmenty modelů.

 Prototyp skupiny Element může obsahovat libovolný počet prvků a odkazy. Typy elementů lze identifikovat pomocí jejich identifikátorů GUID. Identifikátor GUID je obrazce, která byla přetažena není základní prvek modelu. V následujícím příkladu `CanMerge()` vrací true, pokud třída tvaru z diagramu UML je přetáhnout do tohoto diagramu.

```csharp
public override bool CanMerge(ModelElement targetShape, System.Windows.Forms.IDataObject data)
 {
  // Extract the element prototype from the data.
  ElementGroupPrototype prototype = ElementOperations.GetElementGroupPrototype(this.ServiceProvider, data);
  if (targetShape is MyTargetShape && prototype != null &&
        prototype.RootProtoElements.Any(rootElement =>
          rootElement.DomainClassId.ToString()
          ==  "3866d10c-cc4e-438b-b46f-bb24380e1678")) // Guid of UML Class shapes
          // or SourceClass.DomainClassId
        return true;
   return base.CanMerge(targetShape, data);
 }
```

## <a name="mergeelementgroupprototype"></a>MergeElementGroupPrototype()
 Tato metoda je volána, když uživatel elementu do diagramu, obrazec nebo spojnici. Ji by měl sloučit Přetahované obsah do cílového elementu. V tomto příkladu kódu určuje, zda rozpozná kombinace cílové a vytváření prototypů typů; Pokud ano, metoda převede přetažené prvky do prototypu prvků, které mají být přidány do modelu. Základní metoda je volána k provedení sloučení elementů převedený nebo nepřevedeném.

```csharp
public override void MergeElementGroupPrototype(ModelElement targetShape, ElementGroupPrototype sourcePrototype)
{
  ElementGroupPrototype prototypeToMerge = sourcePrototype;
  MyTargetShape pel = targetShape as MyTargetShape;
  if (pel != null)
  {
    prototypeToMerge = ConvertDraggedTypeToLocal(pel, sourcePrototype);
  }
  if (prototypeToMerge != null)
    base.MergeElementGroupPrototype(targetShape, prototypeToMerge);
}
```

 V tomto příkladu se zabývá elementů tříd UML přetáhnout z diagramu tříd UML. DSL není určené k ukládání tříd UML přímo, ale místo toho vytvoříme DSL element pro každou Přetahované třídu modelu UML. To bude užitečné, například když DSL je diagramu instance. Uživatel může tříd přetáhněte do diagramu pro vytvoření instancí těchto tříd.

```csharp

private ElementGroupPrototype ConvertDraggedTypeToLocal (MyTargetShape snapshot, ElementGroupPrototype prototype)
{
  // Find the UML project:
  EnvDTE.DTE dte = snapshot.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
  foreach (EnvDTE.Project project in dte.Solution.Projects)
  {
    IModelingProject modelingProject = project as IModelingProject;
    if (modelingProject == null) continue; // not a modeling project
    IModelStore store = modelingProject.Store;
    if (store == null) continue;
    // Look for the shape that was dragged:
    foreach (IDiagram umlDiagram in store.Diagrams())
    {
      // Get modeling diagram that implements UML diagram:
      Diagram diagram = umlDiagram.GetObject<Diagram>();
      Guid elementId = prototype.SourceRootElementIds.FirstOrDefault();
      ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
      if (shape == null) continue;
      IClass classElement = shape.ModelElement as IClass;
      if (classElement == null) continue;

      // Create a prototype of elements in my DSL, based on the UML element:
      Instance instance = new Instance(snapshot.Store);
      instance.Type = classElement.Name;
      // Pack them into a prototype:
      ElementGroup group = new ElementGroup(instance);
      return group.CreatePrototype();
    }
  }
  return null;
}
```

## <a name="standard-copy-behavior"></a>Chování standardní kopírování
 Kód v této části ukazuje, že můžete přepsat metody, které můžete změnit chování kopírování. Můžete zjistit, jak dosáhnout vlastní úpravy, tato část zobrazuje kód, který se přepíše při kopírování metody, ale nezmění standardní chování.

 Když uživatel stiskne klávesu CTRL + C nebo používá příkaz nabídky kopírování metodu <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> je volána. Zobrazí se, jak toto nastavení **DslPackage\Generated Code\CommandSet.cs**. Další informace o tom, jak jsou příkazy nastavit, najdete v části [postupy: přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 ProcessOnMenuCopyCommand můžete přepsat tak, že přidáte definicí částečné třídy *MyDsl* `ClipboardCommandSet` DslPackage projektu.

```csharp
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

partial class MyDslClipboardCommandSet
{
  /// <summary>
  /// Override ProcessOnMenuCopyCommand() to copy elements to the
  /// clipboard in different formats, or to perform additional tasks
  /// before or after copying - for example deselect the copied elements.
  /// </summary>
  protected override void ProcessOnMenuCopyCommand()
  {
    IList<ModelElement> selectedModelElements = this.SelectedElements;
    if (selectedModelElements.Count == 0) return;

    // System container for clipboard data.
    // The IDataObject can contain data in several formats.
    IDataObject dataObject = new DataObject();

    Bitmap bitmap = null; // For export to other programs.
    try
    {
      #region Create EGP for copying to a DSL.
      this.CopyModelElementsIntoElementGroupPrototype
                     (dataObject, selectedModelElements);
      #endregion

      #region Create bitmap for copying to another application.
      // Find all the shapes associated with this selection:
      List<ShapeElement> shapes = new List<ShapeElement>(
        this.ResolveExportedShapesForClipboardImages
              (dataObject, selectedModelElements));

      bitmap = this.CreateBitmapForClipboard(shapes);
      if (bitmap != null)
      {
        dataObject.SetData(DataFormats.Bitmap, bitmap);
      }
      #endregion

      // Add the data to the clipboard:
      Clipboard.SetDataObject(dataObject, true, 5, 100);
    }
    finally
    {
      // Dispose bitmap after SetDataObject:
      if (bitmap != null) bitmap.Dispose();
    }
  }
/// <summary>
/// Override this to customize the element group that is copied to the clipboard.
/// </summary>
protected override void CopyModelElementsIntoElementGroupPrototype(IDataObject dataObject, IList<ModelElement> selectedModelElements)
{
  return this.ElementOperations.Copy(dataObject, selectedModelElements);
}
}
```

 Každý diagram má instanci typu singleton ElementOperations. Můžete zadat vlastní odvozených děl na základě. Tento soubor, který je možné použít v projektu DSL, by se chovalo stejně jako kód, který přepíše:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace Company.MyDsl
{
  partial class MyDslDiagram
  {
    /// <summary>
    /// Singleton ElementOperations attached to this diagram.
    /// </summary>
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  // Our own version of ElementOperations so that we can override:
  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
    { }

    /// <summary>
    /// Copy elements to the clipboard data.
    /// Provides a hook for adding custom data.
    /// </summary>
    public override void Copy(System.Windows.Forms.IDataObject data,
      ICollection<ModelElement> elements,
      ClosureType closureType,
      System.Drawing.PointF sourcePosition)
    {
      if (CanAddElementGroupFormat(elements, closureType))
      {
        AddElementGroupFormat(data, elements, closureType);
      }

      // Override these to store additional data:
      if (CanAddCustomFormat(elements, closureType))
      {
        AddCustomFormat(data, elements, closureType, sourcePosition);
      }
    }

    protected override void AddElementGroupFormat(System.Windows.Forms.IDataObject data, ICollection<ModelElement> elements, ClosureType closureType)
    {
      // Add the selected elements and those implied by the propagate copy rules:
      ElementGroup elementGroup = this.CreateElementGroup(elements, closureType);

      // Mark all the elements that are not embedded under other elements:
      this.MarkRootElements(elementGroup, elements, closureType);

      // Store in the clipboard data:
      ElementGroupPrototype elementGroupPrototype = this.CreateElementGroupPrototype(elementGroup, elements, closureType);
      data.SetData(ElementGroupPrototype.DefaultDataFormatName, elementGroupPrototype);
    }

    /// <summary>
    /// Override this to store additional elements in the element group:
    /// </summary>
    protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
    {
      ElementGroupPrototype prototype = new ElementGroupPrototype(this.Partition, elementGroup.RootElements, elementGroup);
      return prototype;
    }

    /// <summary>
    /// Create an element group from the given starting elements, using the
    /// copy propagation rules specified in the DSL Definition.
    /// By default, this includes all the embedded descendants of the starting elements,
    /// and also includes reference links where both ends are already included.
    /// </summary>
    /// <param name="startElements">model elements to copy</param>
    /// <param name="closureType"></param>
    /// <returns></returns>
    protected override ElementGroup CreateElementGroup(ICollection<ModelElement> startElements, ClosureType closureType)
    {
      // ElementClosureWalker finds all the connected elements,
      // according to the propagate copy rules specified in the DSL Definition:
      ElementClosureWalker walker = new ElementClosureWalker(this.Partition,
        closureType, // Normally ClosureType.CopyClosure
        startElements,
        true, // Do not load other models.
        null, // Optional list of domain roles not to traverse.
        true); // Include relationship links where both ends are already included.

      walker.Traverse(startElements);
      IList<ModelElement> closureList = walker.ClosureList;
      Dictionary<object, object> closureContext = walker.Context;

      // create a group for this closure
      ElementGroup group = new ElementGroup(this.Partition);
      group.AddRange(closureList, false);

      // create the element group prototype for the group
      foreach (object key in closureContext.Keys)
      {
        group.SourceContext.ContextInfo[key] = closureContext[key];
      }

      return group;
    }
  }
}
```

## <a name="see-also"></a>Viz také:

- [Přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Přizpůsobení chování odstranění](../modeling/customizing-deletion-behavior.md)
- [Ukázka: Ukázka vmsdk následující položky okruhů](http://go.microsoft.com/fwlink/?LinkId=213879)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]