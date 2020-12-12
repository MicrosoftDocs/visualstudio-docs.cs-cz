---
title: Přizpůsobení chování kopírování
description: Přečtěte si, že v DSL vytvořené pomocí sady Visual Studio vizualizace and modeling SDK můžete změnit, co se stane, když uživatel zkopíruje a vloží prvky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8eee81440c0dda7f193d3e37eab700ada3ff259f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363104"
---
# <a name="customizing-copy-behavior"></a>Přizpůsobení chování kopírování
V sadě DSL (Domain-Specific Language) vytvořené pomocí sady Visual Studio vizualizace and modeling SDK můžete změnit, co se stane, když uživatel zkopíruje a vloží prvky.

## <a name="standard-copy-and-paste-behavior"></a>Standardní chování při kopírování a vkládání
 Chcete-li povolit kopírování, nastavte vlastnost **Povolit kopírování** pro uzel **editoru** v Průzkumníku DSL.

 Ve výchozím nastavení, když uživatel kopíruje prvky do schránky, jsou zkopírovány také následující prvky:

- Vložené následníky vybraných prvků (To znamená, že elementy, které jsou cílem vložení vztahů, které jsou nasource ve zkopírovaných prvcích.)

- Propojení vztahů mezi zkopírovanými prvky

  Toto pravidlo se rekurzivně aplikuje na zkopírované elementy a odkazy.

  ![Zkopírované a vložené elementy](../modeling/media/dslcopypastedefault.png)

  Zkopírované elementy a odkazy jsou serializovány a uloženy v <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), které jsou umístěny ve schránce.

  Obrázek kopírovaných prvků je také umístěn ve schránce. Uživatel tak může vkládat do jiných aplikací, jako je Word.

  Uživatel může vložit zkopírované prvky do cíle, který může přijmout prvky podle definice DSL. Například v rámci DSL vygenerovaného šablonou řešení komponent může uživatel vkládat porty do součástí, ale ne do diagramu. a může vkládat součásti do diagramu, ale ne do jiných komponent.

## <a name="customizing-copy-and-paste-behavior"></a>Přizpůsobení chování kopírování a vkládání
 Další informace o přizpůsobení modelu pomocí kódu programu naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 **Povolí nebo zakáže kopírování, vyjmutí a vložení.**
V Průzkumníku DSL nastavte vlastnost **Povolit kopírování pro vložení** uzlu **editoru** .

 **Zkopírujte odkazy na stejný cíl.** Například pokud chcete, aby pole zkopírovaného komentáře bylo propojené se stejným prvkem předmětu.
Nastavte vlastnost **rozšíření kopírování** role tak, aby **rozšířila pouze kopírování na odkaz**. Další informace najdete v tématu [přizpůsobení chování při kopírování odkazů](#customizeLinks).

 Kopírování propojených elementů. Například při kopírování nového prvku jsou provedeny také kopie všech propojených polí komentáře.
Nastavte vlastnost **rozšíření kopírování** role tak, aby se **rozšířila kopie na odkaz a opačný aktér role**. Další informace najdete v tématu [přizpůsobení chování při kopírování odkazů](#customizeLinks).

 **Rychlé duplikace prvků kopírováním a vložením.** V normálním případě je položka, kterou jste právě zkopírovali, stále vybrána a nelze do ní vložit stejný typ prvku.
Přidejte do třídy domény direktivu sloučení elementů a nastavte ji tak, aby předalo sloučení do nadřazené třídy. To bude mít stejný účinek na operace přetažení. Další informace naleznete v tématu [přizpůsobení vytváření a přesunu prvku](../modeling/customizing-element-creation-and-movement.md).

 \- ani

 Vyberte diagram před vložením prvků přepsáním `ClipboardCommandSet.ProcessOnPasteCommand()` . Přidejte tento kód do vlastního souboru v projektu DslPackage:

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

 **Vytvořte další odkazy, když uživatel vloží do vybraného cíle.** Například když je pole komentáře vloženo do prvku, je mezi nimi vytvořen odkaz.
Přidejte direktivu sloučení elementů do cílové doménové třídy a nastavte ji pro zpracování sloučení přidáním odkazů. To bude mít stejný účinek na operace přetažení. Další informace naleznete v tématu [přizpůsobení vytváření a přesunu prvku](../modeling/customizing-element-creation-and-movement.md).

 \- ani

 Přepsáním `ClipboardCommandSet.ProcessOnPasteCommand()` vytvoříte další odkazy po volání základní metody.

 **Přizpůsobení formátů, ve kterých mohou být prvky zkopírovány** do externích aplikací – například pro přidání ohraničení do formuláře rastrového obrázku.
Přepište *MyDsl* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` v projektu DslPackage.

 **Upravte způsob, jakým se zkopírují prvky do schránky pomocí příkazu copy, ale ne v operaci přetažení.**
Přepište *MyDsl* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` v projektu DslPackage.

 **Zachovat rozložení obrazce pomocí kopírování a vložení**
Když uživatel zkopíruje více obrazců, můžete při jejich vložení zachovat jejich relativní pozice. Tato technika je znázorněna příkladem na [VMSDK: Ukázka diagramů okruhů](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8).

 Pro dosažení tohoto efektu přidejte obrazce a konektory do zkopírovaného ElementGroupPrototype.. Nejpohodlnější způsob přepsání je ElementOperations. CreateElementGroupPrototype (). Chcete-li to provést, přidejte do projektu DSL následující kód:

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

 **Vloží tvary do zvoleného umístění, jako je například aktuální pozice kurzoru.**
Když uživatel zkopíruje více obrazců, můžete při jejich vložení zachovat jejich relativní pozice. Tato technika je znázorněna příkladem na [VMSDK: Ukázka diagramů okruhů](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8).

 Chcete-li dosáhnout tohoto efektu, přepište, `ClipboardCommandSet.ProcessOnMenuPasteCommand()` aby se použila verze specifická pro umístění `ElementOperations.Merge()` . Chcete-li to provést, přidejte do projektu DslPackage následující kód:

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
Viz [Postupy: Přidání obslužné rutiny](../modeling/how-to-add-a-drag-and-drop-handler.md)přetažení myší.

## <a name="customizing-link-copy-behavior"></a><a name="customizeLinks"></a> Přizpůsobení chování při kopírování propojení
 Když uživatel zkopíruje prvek, standardní chování je také zkopírování všech vložených prvků. Můžete upravit standardní chování při kopírování. V definici DSL vyberte roli na jedné straně relace a v okno Vlastnosti nastavte hodnotu **šířit kopírování** .

 ![Šíří vlastnost copy role domény.](../modeling/media/dslpropagatescopy.png)

 Existují tři hodnoty:

- Nešířit kopii

- Rozšířit kopírování pouze na odkaz – Pokud je skupina vložena, nová kopie tohoto odkazu bude odkazovat na existující prvek na druhém konci odkazu.

- Rozšířit kopii na aktéra role a proti ní – zkopírovaná skupina obsahuje kopii elementu na druhém konci odkazu.

  ![Účinek kopírování pomocí PropagateCopyToLinkOnly](../modeling/media/dslpropagatecopy.png)

  Změny, které provedete, budou mít vliv na prvky i na kopírovaný obrázek.

## <a name="programming-copy-and-paste-behavior"></a>Programové chování při kopírování a vkládání
 Mnoho aspektů chování DSL s ohledem na kopírování, vkládání, vytváření a mazání objektů se řídí instancí <xref:Microsoft.VisualStudio.Modeling.ElementOperations> , která je spojena s diagramem. Chování vaší DSL můžete upravit odvozením vlastní třídy z <xref:Microsoft.VisualStudio.Modeling.ElementOperations> a přepsáním <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> vlastnosti vaší třídy diagramu.

> [!TIP]
> Další informace o přizpůsobení modelu pomocí kódu programu naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 ![Sekvenční diagram operace kopírování](../modeling/media/dslcopyseqdiagram.png)

 ![Sekvenční diagram operace vložení](../modeling/media/dslpasteseqdiagram.png)

#### <a name="to-define-your-own-elementoperations"></a>Definování vlastního ElementOperations

1. V novém souboru v projektu DSL vytvořte třídu, která je odvozena z <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations> .

2. Přidejte definici částečné třídy pro třídu diagramu. Název této třídy najdete v **Dsl\GeneratedCode\Diagrams.cs**.

    V rámci třídy diagramu přepište  <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> a vraťte instanci podtřídy ElementOperations. Při každém volání byste měli vracet stejnou instanci.

   Přidejte tento kód do vlastního souboru kódu v projektu DslPackage:

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

## <a name="receiving-items-dragged-from-other-models"></a>Příjem položek přetažených z jiných modelů
 ElementOperations lze také použít k definování chování funkce kopírovat, přesunout, odstranit a přetáhnout. Jako ukázka použití ElementOperations je zde uvedený příklad definující vlastní chování při přetahování myší. Pro tento účel ale můžete uvažovat o alternativním přístupu popsaném v tématu [Postupy: Přidání obslužné rutiny](../modeling/how-to-add-a-drag-and-drop-handler.md)přetažení, která je rozšiřitelná.

 Ve třídě ElementOperations definujte dvě metody:

- `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` Určuje, zda lze zdrojový prvek přetáhnout na cílový obrazec, spojnici nebo diagram.

- `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` který kombinuje zdrojový prvek do cíle.

### <a name="canmerge"></a>CanMerge()
 `CanMerge()` je volána k určení zpětné vazby, která by měla být dána uživateli, když se ukazatel myši pohybuje v diagramu. Parametry metody jsou prvek, nad nímž je ukazatel myši umístěn, a data o zdroji, ze kterého byla operace přetažení provedena. Uživatel může přetáhnout z libovolného místa na obrazovce. Proto může být zdrojový objekt v mnoha různých typech a může být serializován v různých formátech. Pokud je zdrojem DSL nebo model UML, je datovým parametrem serializace <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . Operace přetažení, kopírování a sady nástrojů používají ElementGroupPrototypes k vyjádření fragmentů modelů.

 Prototyp skupiny elementů může obsahovat libovolný počet prvků a odkazů. Typy prvků mohou být identifikovány pomocí identifikátorů GUID. Identifikátor GUID je tvar, který byl přetažen, nikoli podkladový prvek modelu. V následujícím příkladu `CanMerge()` vrátí hodnotu true, pokud je obrazec třídy z diagramu UML přetažen do tohoto diagramu.

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
 Tato metoda je volána, když uživatel přetáhne prvek do diagramu, tvaru nebo spojnice. Měl by sloučit přetažený obsah do cílového prvku. V tomto příkladu kód určuje, zda rozpozná kombinaci typů Target a Prototype; Pokud ano, metoda převede přetažené prvky na prototyp prvků, které by měly být přidány do modelu. Základní metoda je volána pro provedení sloučení, buď převedených nebo nepřeváděných prvků.

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

 Tento příklad se zabývá prvky třídy UML přetažené z diagramu tříd UML. DSL není navržená tak, aby přímo ukládala třídy UML, ale místo toho vytvoříme element DSL pro každou přetaženou třídu UML. To je užitečné, například pokud je DSL instancí diagramu instance. Uživatel může přetáhnout třídy do diagramu a vytvořit tak instance těchto tříd.

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

## <a name="standard-copy-behavior"></a>Standardní chování kopírování
 Kód v této části ukazuje metody, které lze přepsat pro změnu chování kopírování. V této části se dozvíte, jak dosáhnout vlastního nastavení, v této části se zobrazuje kód, který Přepisuje metody spojené s kopírováním, ale nemění standardní chování.

 Když uživatel stiskne kombinaci kláves CTRL + C nebo použije příkaz Kopírovat nabídku, <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> je volána metoda. Můžete vidět, jak se nastavuje v **DslPackage\Generated Code\CommandSet.cs**. Další informace o tom, jak jsou nastaveny příkazy, naleznete v tématu [How to: Add a Command to a příkaz do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 ProcessOnMenuCopyCommand můžete přepsat přidáním částečné třídy definice *MyDsl* `ClipboardCommandSet` v projektu DslPackage.

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

 Každý diagram má instanci typu Singleton (ElementOperations). Můžete dodat svůj vlastní derivát. Tento soubor, který může být umístěn v projektu DSL, se bude chovat stejně jako kód, který Přepisuje:

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
- [Ukázka: Ukázka diagramů okruhu VMSDK](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
