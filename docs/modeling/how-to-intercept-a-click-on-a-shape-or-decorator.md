---
title: 'Postupy: Zachycení kliknutí na obrazec či dekorátor'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4923a858d9d46c477f50df2a08440a10e9309ef
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114521"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Postupy: Zachycení kliknutí na obrazec či dekorátor
Následující postupy ukazují, jak zachytit kliknutí na tvar nebo ikonu dekoratér. Můžete zachytit kliknutím, dvojitým kliknutím, přetažením a dalším gestům a nastavit prvek jako odpověď.

## <a name="to-intercept-clicks-on-shapes"></a>Zachycení kliknutí na obrazce
 V projektu DSL v souboru kódu, který je oddělen od generovaných souborů kódu, zapište částečnou definici třídy pro třídu Shape. Přepište `OnDoubleClick()` nebo jednu jinou metodu, která má název začínající na `On...`. Příklad:

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
> Nastavte `e.Handled` na `true`, pokud nechcete, aby byla událost předána k nadřazenému obrazci nebo diagramu.

## <a name="to-intercept-clicks-on-decorators"></a>Zachycení kliknutí na dekoratéry
 Image dekoratéry se přenesou na instanci třídy ImageField, která má metodu-DoubleClick. Můžete zachytit kliknutím, pokud píšete podtřídu ImageField. Pole jsou nastavena v metodě InitializeShapeFields. Proto je nutné změnit tuto metodu pro vytvoření instance podtřídy namísto normálního ImageField. Metoda InitializeShapeFields je ve vygenerovaném kódu třídy Shape. Můžete přepsat třídu Shape, pokud nastavíte vlastnost `Generates Double Derived`, jak je popsáno v následujícím postupu.

 I když InitializeShapeFields je metoda instance, je volána pouze jednou pro každou třídu. Proto pro každé pole v každé třídě existuje pouze jedna instance ClickableImageField, nikoli jedna instance pro každý prvek v diagramu. Když uživatel dvakrát klikne na instanci, je nutné určit, která instance byla vybrána, jak kód v příkladu ukazuje.

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>Zachycení kliknutí na ikonu dekoratér

1. Otevřete nebo vytvořte řešení DSL.

2. Vyberte nebo vytvořte obrazec s ikonou dekoratér a namapujte ho na doménovou třídu.

3. V souboru kódu, který je oddělen od souborů ve složce `GeneratedCode`, vytvořte novou podtřídu třídy ImageField:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     Nastavte na hodnotu true, pokud nechcete, aby byla událost předána nadřazenému obrazci.

4. Přepište metodu InitializeShapeFields ve třídě Shape přidáním následující definice částečné třídy.

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1. Sestavte a spusťte řešení.

2. Dvakrát klikněte na ikonu v instanci tvaru. Vaše zkušební zpráva by se měla zobrazit.

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>Zachycení kliknutí a přetahování na seznam CompartmentShape
 Následující ukázka umožňuje uživatelům přeuspořádat položky v obrazci oddílu přetažením. Spuštění tohoto kódu:

1. Vytvořte nové řešení DSL pomocí šablony řešení **diagramy tříd** .

    Můžete také pracovat s řešením, které obsahuje obrazce oddílu. Tento kód předpokládá, že existuje vztah vložení mezi prvky modelu reprezentované obrazcem a prvky reprezentované v položkách seznamu oddílů.

2. Nastavte vlastnost **Generovat dvojitou hodnotu odvozenou** pro tvar oddílu.

3. Přidejte tento kód do souboru v projektu **DSL** .

4. Upravte názvy tříd domény a tvarů v tomto kódu tak, aby odpovídaly vaší vlastní DSL.

   V souhrnu kód funguje následujícím způsobem. V tomto příkladu je `ClassShape` název obrazce oddílu.

- Sada obslužných rutin událostí myši je při vytvoření přiřazena ke každé instanci oddílu.

- Událost `ClassShape.MouseDown` ukládá aktuální položku.

- Když se ukazatel myši přesune mimo aktuální položku, vytvoří se instance MouseAction, která nastaví kurzor a zachytí ukazatel myši, dokud se neuvolní.

     Aby nedošlo ke konfliktu s ostatními akcemi myši, jako je například výběr textu položky, MouseAction se nevytvoří, dokud myš neopustí původní položku.

     Alternativou k vytvoření MouseAction by bylo jednoduše naslouchat MouseUp. To ale nefunguje správně, pokud uživatel uvolní myš po přetažení mimo oddíl. MouseAction je schopný provést odpovídající akci bez ohledu na to, kde byla myš vydaná.

- Po uvolnění myši MouseAction. MouseUp změní pořadí propojení mezi prvky modelu.

- Změna pořadí rolí vyvolá pravidlo, které aktualizuje zobrazení. Toto chování je už definované a nevyžaduje se žádný další kód.

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
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
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
  /// click somewhere else in the source shape.
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
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
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

- [Reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md)
- [Vlastnosti dekorátorů](../modeling/properties-of-decorators.md)
