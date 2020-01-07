---
title: 'Postupy: Přidání obslužné rutiny operace přetažení myší'
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc0124df648dbc5ecfbcf60ce0cca2fdc974e7e8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594692"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Postupy: Přidání obslužné rutiny operace přetažení myší

Můžete přidat obslužné rutiny pro události přetažení do DSL, aby uživatelé mohli přetahovat položky do diagramu z jiných diagramů nebo z jiných částí sady Visual Studio. Můžete také přidat obslužné rutiny pro události, jako je například dvojité kliknutí. Společně lze obslužné rutiny přetahovat a dvakrát kliknout na obslužné rutiny, které jsou označovány jako *obslužné rutiny gest*.

Toto téma popisuje gesta přetažení, která pocházejí z jiných diagramů. Pro události přesunutí a zkopírování v rámci jednoho diagramu zvažte alternativu definování podtřídy `ElementOperations`. Další informace najdete v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md). Můžete také přizpůsobit definici DSL.

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>Definování obslužných rutin gest přepsáním metod ShapeElement

`OnDragDrop`, `OnDoubleClick`, `OnDragOver`a další metody lze přepsat.

Přidejte nový soubor kódu do projektu DSL. Pro obslužnou rutinu gesta obvykle musíte mít alespoň následující direktivy `using`:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

V novém souboru definujte částečnou třídu pro tvar nebo třídu diagramu, která by měla reagovat na operaci přetažení. Přepište následující metody:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>– Tato metoda se volá, když ukazatel myši vstoupí do tvaru během operace přetažení. Vaše metoda by měla zkontrolovat položku, kterou uživatel přetáhne, a nastavit vlastnost Effect tak, aby označovala, zda uživatel může položku na tomto obrazci vyřadit. Vlastnost efekt určuje vzhled kurzoru, zatímco je nad tímto obrazcem, a také určuje, zda bude `OnDragDrop()` volána, když uživatel uvolní tlačítko myši.

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> – Tato metoda se volá, když uživatel uvolní tlačítko myši, zatímco ukazatel myši je nad tímto obrazcem nebo diagramem, pokud `OnDragOver(DiagramDragEventArgs e)` dřív nastavil `e.Effect` na jinou hodnotu než `None`.

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
    {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
    }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> – Tato metoda se volá, když uživatel dvakrát klikne na obrazec nebo diagram.

     Další informace najdete v tématu [Postup: zachycení kliknutí na obrazec nebo dekoratér](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Definujte `IsAcceptableDropItem(e)` pro určení, zda je přetažená položka přijatelná, a ProcessDragDropItem (e) pro aktualizaci modelu, když je položka vyřazena. Tyto metody musí nejprve extrahovat položku z argumentů události. Informace o tom, jak to provést, najdete v tématu [Jak získat odkaz na přetaženou položku](#to-send-an-object-from-a-source-dsl).

## <a name="define-gesture-handlers-by-using-mef"></a>Definování obslužných rutin gest pomocí MEF

Tuto metodu použijte, pokud chcete, aby vývojáři třetích stran mohli definovat vlastní obslužné rutiny na DSL. Uživatelé si můžou nainstalovat rozšíření od jiných výrobců po instalaci DSL.

MEF (Managed Extensibility Framework) umožňuje definovat komponenty, které se dají nainstalovat s minimální konfigurací. Další informace naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-define-a-mef-gesture-handler"></a>Definování obslužné rutiny gesta MEF

1. Do projektů **DSL** a **DslPackage** přidejte soubory **MefExtension** , které jsou POpsány v tématu [rozšiřování DSL](../modeling/extend-your-dsl-by-using-mef.md)pomocí rozhraní MEF.

2. Nyní můžete definovat obslužnou rutinu gesta jako komponentu MEF:

    ```csharp
    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }
    ```

     Můžete vytvořit více než jednu komponentu obslužné rutiny gesta, například když máte různé typy přetažených objektů.

3. Přidejte definice částečné třídy pro cílový obrazec, třídy spojnice nebo diagram a definujte metody `IsAcceptableDropItem()` a `ProcessDragDropItem()`. Tyto metody musí začít extrahováním přetažené položky z argumentů události. Další informace najdete v tématu [Jak získat odkaz na přetaženou položku](#to-send-an-object-from-a-source-dsl).

## <a name="how-to-decode-the-dragged-item"></a>Jak dekódovat přetaženou položku

Prvky lze přetáhnout z libovolného okna nebo z plochy i z DSL.

Když uživatel přetáhne položku do vašeho diagramu, nebo z jedné části diagramu na jiný, informace o položce, která je přetažena, jsou k dispozici v `DiagramDragEventArgs`. Vzhledem k tomu, že operace přetažení mohla začít na jakémkoli objektu na obrazovce, mohou být data k dispozici v některém z nejrůznějších formátů. Váš kód musí rozpoznat formáty, se kterými je schopen řešit.

Chcete-li zjistit formáty, ve kterých jsou k dispozici informace o zdroji, spusťte kód v režimu ladění a nastavte zarážku na položku `OnDragOver()` nebo `CanDragDrop()`. Zkontrolujte hodnoty parametru `DiagramDragEventArgs`. Tyto informace jsou k dispozici ve dvou formách:

- <xref:System.Windows.Forms.IDataObject>`Data` – Tato vlastnost přináší serializované verze zdrojových objektů, obvykle ve více než jednom formátu. Nejužitečnější funkce jsou:

  - diagramEventArgs. data. GetDataFormats () – vypíše formáty, ve kterých lze dekódovat přetažený objekt. Pokud uživatel například přetáhne soubor z plochy, dostupné formáty obsahují název souboru ("`FileNameW`").

  - `diagramEventArgs.Data.GetData(format)` – dekóduje přetažený objekt v zadaném formátu. Přetypování objektu na příslušný typ. Příklad:

    `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

    Objekty, jako jsou například odkazy sběrnice modelu, můžete také přenést ze zdroje ve vlastním formátu. Další informace najdete v tématu [odeslání odkazů na sběrnici modelu při přetahování myší](#to-send-an-object-from-a-source-dsl).

- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> `Prototype` – tuto vlastnost použijte v případě, že chcete, aby uživatelé přetáhli položky z modelu DSL nebo modelu UML. Prototyp skupiny elementů obsahuje jeden nebo více objektů, odkazů a jejich hodnot vlastností. Používá se také při operacích vkládání a při přidávání prvku ze sady nástrojů. V prototypu jsou objekty a jejich typy identifikovány pomocí identifikátoru GUID. Například tento kód umožňuje uživateli přetahovat prvky třídy z diagramu UML nebo Průzkumníka modelů UML:

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     Chcete-li přijmout obrazce UML, určete identifikátory GUID tříd tvarů UML pomocí experimentu. Pamatujte, že v jakémkoli diagramu je obvykle více než jeden typ elementu. Nezapomeňte také, že objekt přetažený z diagramu DSL nebo UML je tvar, nikoli prvek modelu.

`DiagramDragEventArgs` také obsahuje vlastnosti, které určují aktuální pozici ukazatele myši a zda uživatel stiskne klávesy CTRL, ALT nebo SHIFT.

## <a name="how-to-get-the-original-of-a-dragged-element"></a>Jak získat originál přetaženého elementu

Pokud je přetažená položka prvkem DSL, můžete otevřít zdrojový model a přistupovat k elementu.

Vlastnosti `Data` a `Prototype` argumentů události obsahují pouze odkaz na přetažený tvar. V případě, že chcete vytvořit objekt v cílové DSL, který je odvozen z prototypu nějakým způsobem, je třeba získat přístup k původnímu souboru, například čtení obsahu souboru nebo přechod na prvek modelu reprezentovaný obrazcem. Pomocí sběrnice modelů sady Visual Studio můžete s tímto nástrojem pomáhat.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Příprava projektu DSL pro sběrnici modelu

Zpřístupněte zdrojovou DSL přístupovou pomocí sběrnice modelů sady Visual Studio:

1. V Návrháři DSL otevřete soubor definice DSL pro zdrojovou DSL. Klikněte pravým tlačítkem na návrhové ploše a potom klikněte na tlačítko **povolit Modelbus**. V dialogovém okně vyberte jednu z možností.  Klikněte na tlačítko **OK**. Do řešení DSL se přidá nový projekt "ModelBus".

2. Klikněte na **transformovat všechny šablony** a znovu sestavte řešení.

### <a name="to-send-an-object-from-a-source-dsl"></a>Odeslání objektu ze zdrojové DSL

1. V podtřídě ElementOperations přepište `Copy()` tak, aby se do IDataObject zakódují odkaz sběrnice modelu (MBR). Tato metoda bude volána, když uživatel začne přetahovat ze zdrojového diagramu. Kódovaný MBR bude k dispozici v IDataObject, když se uživatel v cílovém diagramu přeruší.

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}
    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Získání odkazu na sběrnici modelu z DSL v cílovém projektu DSL nebo UML

1. V projektu cílové technologie DSL přidejte odkazy na projekt do:

    - Zdrojový projekt DSL

    - Zdrojový projekt ModelBus

2. V souboru kódu obslužné rutiny gesta přidejte následující odkazy na obor názvů:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3. Následující příklad ukazuje, jak získat přístup k prvku zdrojového modelu:

    ```csharp
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }
    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Přijetí elementu nasourceho z modelu UML

- Následující ukázka kódu akceptuje objekt vyřazený z diagramu UML.

    ```csharp
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Classes;
    using System;
    using System.ComponentModel.Composition;
    using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }
    ```

## <a name="using-mouse-actions-dragging-compartment-items"></a>Použití akcí myši: přetahování položek oddílu

Můžete napsat obslužnou rutinu, která zachycuje akce myši u polí obrazce. Následující příklad umožňuje uživateli změnit pořadí položek v oddílu přetažením pomocí myši.

Chcete-li sestavit tento příklad, vytvořte řešení pomocí šablony řešení **diagramy tříd** . Přidejte soubor kódu a přidejte následující kód. Upravte obor názvů tak, aby byl stejný jako váš vlastní.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape. Yuk.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>Viz také:

- [Přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)
- [Nasazení řešení jazyka specifického pro doménu](msi-and-vsix-deployment-of-a-dsl.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
