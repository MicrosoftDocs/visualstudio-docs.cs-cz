---
title: 'Postupy: přidání obslužné rutiny operace přetažení myší | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39ee88a0-85c3-485e-8c0a-d9644c6b25d9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f89ea35c9113ddff67a9d1322b1c83c41e05709a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848975"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Postupy: Přidání obslužné rutiny operace přetažení myší
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL, můžete přidat obslužné rutiny události přetažení myší, tak, aby uživatelé můžete přetáhnout položky do diagramu z jiných diagramů nebo z jiných částí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Můžete také přidat obslužné rutiny pro události, jako poklikáním. Společně se nazývají přetahování myší a dvakrát klikněte na obslužné rutiny *obslužné rutiny gesta*.  
  
 Toto téma popisuje gesta přetažení myší, které pocházejí na jiných diagramů. Pro přesun a kopírování události v rámci jednoho diagramu, vezměte v úvahu alternativní definice podtřída `ElementOperations`. Další informace najdete v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md). Také je možné přizpůsobit definici DSL.  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   Alternativní způsoby definování obslužné rutiny gesta v prvních dvou částech:  
  
    -   [Definování obslužné rutiny gesta ShapeElement přepsání metody](#overrideShapeElement). `OnDragDrop`, `OnDoubleClick`, `OnDragOver`, a další metody můžete přepsat.  
  
    -   [Definování obslužné rutiny gesta pomocí MEF](#MEF). Tuto metodu použijte, pokud chcete, aby vývojáři třetích stran, abyste mohli definovat jejich vlastní obslužné rutiny do vašeho DSL. Uživatelé mohou nainstalovat rozšíření třetích stran po instalují vašeho DSL.  
  
-   [Dekódování přetaženou položku](#extracting). Elementy můžete přetáhnout z jakékoli okno nebo z plochy, stejně jako z DSL.  
  
-   [Získání původní přetáhnout položky](#getOriginal). Pokud přetaženou položku je prvek DSL, můžete otevřít zdrojový model a přístup k elementu.  
  
-   [Pomocí akce myši: Přetažení položek oddílu](#mouseActions). Tento příklad ukazuje rutinu nižší úrovně, která zachycuje akce myši na pole obrazce. Příklad umožňuje uživateli změnit pořadí položek v prostoru přetažením myší.  
  
##  <a name="overrideShapeElement"></a> Definování obslužné rutiny gesta tak, že přepíšete ShapeElement metody  
 Přidejte nový soubor kódu do projektu DSL. Pro obslužnou rutinu gesta, je obvykle musí mít minimálně následující `using` příkazy:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using System.Linq;  
```  
  
 V novém souboru definujte částečnou třídu pro obrazec ani diagram třídy, která by měla odpovídat operace přetažení. Přepište následující metody:  
  
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>– Tato metoda je volána, pokud kurzor myši vstoupí na obrazec během operace přetažení. Metodu by měl zkontrolovat, že uživatel přetahuje položku a nastavte vlastnost účinek označující, zda uživatele lze přetáhnout položky v tomto tvaru. Vlastnost účinek určuje vzhled kurzor, zatímco je nad tímto obrazcem a také určuje, zda `OnDragDrop()` bude volána, když uživatel uvolní tlačítko myši.  
  
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
  
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> – Tato metoda je volána, pokud uživatel uvolní tlačítko myši při umístění ukazatele myši stisknuté tento tvar nebo diagram, pokud `OnDragOver(DiagramDragEventArgs e)` předtím nastavili `e.Effect` hodnotu jinou než `None`.  
  
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
  
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> – Tato metoda je volána, když uživatel pokliká na tvar nebo diagram.  
  
   Další informace najdete v tématu [postupy: zachycení kliknutí na obrazec či Dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
  Definování `IsAcceptableDropItem(e)` k určení, zda je přijatelné přetaženou položku a ProcessDragDropItem(e) aktualizovat váš model, když položka byla vynechána. Tyto metody musí nejprve extrahovat položky z argumentů událostí. Informace o tom, jak to udělat, najdete v části [jak získat odkaz na přetaženou položku](#extracting).  
  
##  <a name="MEF"></a> Definování obslužné rutiny gesta pomocí MEF  
 MEF (Managed Extensibility Framework) umožňuje definovat součásti, které mohou být nainstalovány s minimální konfigurací. Další informace najdete v tématu [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-define-a-mef-gesture-handler"></a>Chcete-li definovat obslužnou rutinu gesta MEF  
  
1.  Přidat do vaší **Dsl** a **DslPackage** projektů **MefExtension** soubory, které jsou popsány v [rozšíření vašeho DSL pomocí MEF](../modeling/extend-your-dsl-by-using-mef.md).  
  
2.  Nyní je možné definovat obslužnou rutinu gesta jako komponentu MEF:  
  
    ```  
  
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
  
     Můžete vytvořit více než jedna komponenta obslužné rutiny gesta, například pokud máte různé typy přetažených objektů.  
  
3.  Přidat definicí částečné třídy pro tvar target, konektoru nebo diagramu třídy a definujte metody `IsAcceptableDropItem()` a `ProcessDragDropItem()`. Tyto metody musí začínat extrahováním přetaženou položku z argumentů události. Další informace najdete v tématu [jak získat odkaz na přetaženou položku](#extracting).  
  
##  <a name="extracting"></a> Dekódování přetaženou položku  
 Když uživatel přetáhne položku do diagramu, nebo z jedné části diagramu do druhého, je k dispozici v informace o položce, který je přetažen `DiagramDragEventArgs`. Vzhledem k tomu, že operace přetažení může začít na libovolný objekt na obrazovce, data mohou být k dispozici v některém z různých formátech. Kódu musí rozpoznat formátů, se kterými je schopen práci.  
  
 Ke zjištění formátů, v nichž je k dispozici vaše informace o zdroji přetažení svůj kód spustit v režimu, nastavení zarážky na položce, aby ladění `OnDragOver()` nebo `CanDragDrop()`. Zkontrolovat hodnoty `DiagramDragEventArgs` parametru. Informace jsou poskytovány ve dvou formách:  
  
- <xref:System.Windows.Forms.IDataObject>  `Data` – Tato vlastnost představuje serializovaná verze zdrojových objektů, obvykle více než jeden formát. Jeho nejužitečnější funkce jsou:  
  
  -   diagramEventArgs.Data.GetDataFormats() – obsahuje seznam formátů, ve kterých umí dekódovat přetahovaného objektu. Například pokud uživatel přetáhne soubor z plochy, dostupné formáty patří název souboru ("`FileNameW`").  
  
  -   `diagramEventArgs.Data.GetData(format)` – Dekóduje přetahovaného objektu v zadaném formátu. Objekt na příslušný typ přetypování. Příklad:  
  
       `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`  
  
       Objekty, jako jsou odkazy na Service bus model ze zdroje může taky přenášet v vlastní formát. Další informace najdete v tématu [jak odeslat odkazy na Model Service Bus v operace přetažení](#mbr).  
  
- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> `Prototype` – Pomocí této vlastnosti, pokud chcete uživatelům přetáhněte položky z DSL nebo modelu UML. Prvku skupiny prototyp obsahuje jeden nebo více objektů, odkazy a jejich hodnot vlastností. Používá se také operace vložení a jsou při přidávání prvku z panelu nástrojů. V prototypu objektů a jejich typy jsou označeny identifikátorem Guid. Tento kód například umožňuje uživateli prvky třídu přetáhnout z Průzkumníku modelů UML nebo diagramu UML:  
  
  ```csharp  
  private bool IsAcceptableDropItem(DiagramDragEventArgs e)  
  {  
    return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>   
          element.DomainClassId.ToString()   
          == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.  
   // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId  
  }  
  
  ```  
  
   Tak, aby přijímal obrazce UML, určuje na základě experiment identifikátory GUID tvar tříd UML. Mějte na paměti, že je obvykle více než jeden typ prvku na jakýkoliv diagram. Nezapomeňte, že je objekt přetažen z diagramu DSL nebo UML obrazec není na prvek modelu.  
  
  `DiagramDragEventArgs` také obsahuje vlastnosti, které označují aktuální pozici ukazatele myši a určuje, zda uživatel je stisknutím klávesy CTRL, ALT a SHIFT – klávesy.  
  
##  <a name="getOriginal"></a> Získání původní Přetahované element  
 `Data` a `Prototype` vlastností argumentů události obsahují pouze odkaz na přetaženou tvaru. Obvykle Pokud chcete vytvořit objekt v cíli DSL, která je odvozena z prototypu nějakým způsobem, musíte získat přístup k původní, například čtení obsah souboru nebo přechod na prvek modelu reprezentovány ve tvaru.  Sběrnice modelu Visual Studio můžete použít pro usnadnění.  
  
### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Příprava sběrnice modelu projektu DSL  
  
1.  Zpřístupnění zdroje DSL pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sběrnice modelu:  
  
    1.  Stáhněte a nainstalujte rozšíření sběrnice modelu Visual Studio, pokud ještě není nainstalovaná. Další informace najdete v tématu [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Otevřete soubor definice DSL zdroje DSL v návrháře DSL. Klikněte pravým tlačítkem na návrhové ploše a potom klikněte na tlačítko **povolit Modelbus**. V dialogovém okně zvolte jednu nebo obě možnosti.  Klikněte na tlačítko **OK**. Nový projekt "ModelBus" je přidán do řešení DSL.  
  
    3.  Klikněte na tlačítko **Transformovat všechny šablony** a znovu sestavte řešení.  
  
###  <a name="mbr"></a> Odesílat objekt ze zdroje DSL  
  
1.  Do vaší podtřídy ElementOperations přepsat `Copy()` tak, aby kóduje odkaz modelu Service Bus (MBR) do IDataObject. Tato metoda bude volána, když uživatel spustí přetáhněte ze zdrojového diagramu. Kódovaný MBR budou k dispozici v IDataObject, když uživatel v diagramu cíl.  
  
    ```  
  
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
  
### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Pro příjem z DSL v projektu DSL nebo UML Cílový odkaz modelu Service Bus  
  
1.  V projektu DSL target přidejte odkazy na:  
  
    -   Zdrojový projekt Dsl.  
  
    -   Zdrojový projekt ModelBus.  
  
2.  V souboru kódu obslužné rutiny gesta přidejte následující odkazy na obor názvů:  
  
    ```csharp  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
    using Microsoft.VisualStudio.Modeling.Integration;  
    using SourceDslNamespace;  
    using SourceDslNamespace.ModelBusAdapters;  
  
    ```  
  
3.  Následující příklad ukazuje, jak získat přístup k prvku modelu zdroje:  
  
    ```  
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
  
### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Tak, aby přijímal element Source z modelu UML  
  
-   Následující vzorový kód přijímá objekt v diagramu UML.  
  
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
  
##  <a name="mouseActions"></a> Pomocí akce myši: Přetažení položek oddílu  
 Můžete napsat obslužnou rutinu, která zachycuje akce myši na pole obrazce. Následující příklad umožňuje uživateli změnit pořadí položek v prostoru přetažením myší.  
  
 Sestavení tohoto příkladu, vytvořte řešení pomocí **diagramů tříd** šablonu řešení. Přidat soubor s kódem a přidejte následující kód. Upravte obor názvů být stejný jako vlastní.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)   
 [Nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md)



