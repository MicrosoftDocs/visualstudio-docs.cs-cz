---
title: Definování obslužné rutiny gesta v diagramu modelování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fbf111dbf8297994994f10b9b867e03321268679
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654875"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Definování obslužné rutiny gest v diagramu modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete definovat příkazy, které se mají provést, když uživatel dvakrát klikne nebo přetáhne položky do diagramu UML. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) a distribuovat je ostatním uživatelům aplikace Visual Studio.

 Pokud již existuje předdefinované chování pro typ diagramu a typ prvku, který chcete přetáhnout, pravděpodobně nebudete moci přidat nebo přepsat toto chování.

## <a name="requirements"></a>Požadavky
 Viz [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-gesture-handler"></a>Vytvoření obslužné rutiny gesta
 Chcete-li definovat obslužnou rutinu gesta pro návrháře UML, je nutné vytvořit třídu, která definuje chování obslužné rutiny gesta, a vložit tuto třídu do rozšíření integrace sady Visual Studio (VSIX). VSIX funguje jako kontejner, který může nainstalovat obslužnou rutinu. Existují dvě alternativní metody definování obslužné rutiny gesta:

- **Vytvořte obslužnou rutinu gesta ve vlastním souboru VSIX pomocí šablony projektu.** Toto je rychlejší metoda. Použijte jej, pokud nechcete kombinovat svou obslužnou rutinu s jinými typy rozšíření, jako jsou například rozšíření ověřování, vlastní položky sady nástrojů nebo příkazy nabídky.

- **Vytvořte samostatnou obslužnou rutinu gesta a VSIX projekty.** Tuto metodu použijte, pokud chcete zkombinovat několik typů rozšíření do stejného VSIX. Například pokud vaše obslužná rutina gesta očekává, že model bude dodržovat konkrétní omezení, můžete jej vložit do stejného VSIX jako metodu ověřování.

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Vytvoření obslužné rutiny gesta ve vlastním souboru VSIX

1. V dialogovém okně **Nový projekt** , v části **modelování projektů**vyberte **rozšíření gesta**.

2. Otevřete soubor **. cs** v novém projektu a upravte třídu `GestureExtension` pro implementaci obslužné rutiny gesta.

    Další informace naleznete v tématu [implementace obslužné rutiny gesta](#Implementing).

3. Stisknutím klávesy F5 otestujte obslužnou rutinu gesta. Další informace naleznete v tématu [provádění obslužné rutiny gesta](#Executing).

4. Nainstalujte obslužnou rutinu gesta v jiném počítači zkopírováním souboru **bin \\ \* \\ \*. vsix** sestaveného vaším projektem. Další informace najdete v tématu [instalace a odinstalace rozšíření](#Installing).

   Tady je alternativní postup:

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Vytvoření samostatného projektu knihovny tříd (DLL) pro obslužnou rutinu gesta

1. Vytvořte projekt knihovny tříd, a to buď v novém řešení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nebo v existujícím řešení.

   1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**.

   2. V části **Nainstalované šablony**rozbalte **položku C# Visual** nebo **Visual Basic**a potom v prostředním sloupci zvolte možnost **Knihovna tříd**.

2. Do projektu přidejte následující odkazy.

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` – budete ho potřebovat jenom v případě, že rozšiřujete diagramy vrstev. Další informace naleznete v tématu [Rozšířené diagramy vrstev](../modeling/extend-layer-diagrams.md).

3. Přidejte soubor třídy do projektu a nastavte jeho obsah na následující kód.

   > [!NOTE]
   > Změňte obor názvů a název třídy podle vaší předvolby.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Modeling.Diagrams;
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Modeling;
   using Microsoft.VisualStudio.Uml.Classes;
   // ADD other UML namespaces if required

   namespace MyGestureHandler // CHANGE
   {
     // DELETE any of these attributes if the handler
     // should not work with some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // Gesture handlers must export IGestureExtension:
     [Export(typeof(IGestureExtension))]
     // CHANGE class name
     public class MyGesture1 : IGestureExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       /// <summary>
       /// Called when the user double-clicks on the diagram
       /// </summary>
       /// <param name="targetElement"></param>
       /// <param name="diagramPointEventArgs"></param>
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target shape, if any. Null if the target is the diagram.
         IShape targetIShape = targetElement.CreateIShape();

         // Do something...
       }

       /// <summary>
       /// Called repeatedly when the user drags from anywhere on the screen.
       /// Return value should indicate whether a drop here is allowed.
       /// </summary>
       /// <param name="targetMergeElement">References the element to be dropped on.</param>
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>
       /// <returns></returns>
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target element, if any. Null if the target is the diagram.
         IShape targetIShape = targetMergeElement.CreateIShape();

         // This example allows drag of any UML elements.
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;
       }

       /// <summary>
       /// Execute the action to be performed on the drop.
       /// </summary>
       /// <param name="targetDropElement"></param>
       /// <param name="diagramDragEventArgs"></param>
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.
       }

       /// <summary>
       /// Retrieves UML IElements from drag arguments.
       /// Works for drags from UML diagrams.
       /// </summary>
       private IEnumerable<IElement> GetModelElementsFromDragEvent
               (DiagramDragEventArgs dragEvent)
       {
         //ElementGroupPrototype is the container for
         //dragged and copied elements and toolbox items.
         ElementGroupPrototype prototype =
            dragEvent.Data.
            GetData(typeof(ElementGroupPrototype))
                 as ElementGroupPrototype;
         // Locate the originals in the implementation store.
         IElementDirectory implementationDirectory =
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

         return prototype.ProtoElements.Select(
           prototypeElement =>
           {
             ModelElement element = implementationDirectory
               .FindElement(prototypeElement.ElementId);
             ShapeElement shapeElement = element as ShapeElement;
             if (shapeElement != null)
             {
               // Dragged from a diagram.
               return shapeElement.ModelElement as IElement;
             }
             else
             {
               // Dragged from UML Model Explorer.
               return element as IElement;
             }
           });
       }

     }
   }

   ```

    Další informace o tom, co vložit do metod, viz [implementace obslužné rutiny gesta](#Implementing).

   Příkaz nabídky je nutné přidat do projektu VSIX, který slouží jako kontejner pro instalaci příkazu. Pokud chcete, můžete zahrnout další komponenty do stejného VSIX.

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Přidání samostatné obslužné rutiny gesta do projektu VSIX

1. Tento postup nebudete potřebovat, pokud jste vytvořili obslužnou rutinu gesta s vlastním souborem VSIX.

2. Vytvořte projekt VSIX, pokud vaše řešení již jednu nemá.

    1. V **Průzkumník řešení**v místní nabídce řešení vyberte možnost **Přidat**, **Nový projekt**.

    2. V části **Nainstalované šablony**rozbalte **položku C# Visual** nebo **Visual Basic**a potom vyberte možnost **rozšiřitelnost**. V prostředním sloupci vyberte **projekt VSIX**.

3. Nastavte projekt VSIX jako projekt po spuštění řešení.

    - V Průzkumník řešení v místní nabídce projektu VSIX vyberte možnost **nastavit jako projekt po spuštění**.

4. V části **source. extension. vsixmanifest**přidejte projekt knihovny tříd obslužné rutiny gesta jako součást MEF:

    1. Na kartě **metadata** nastavte název VSIX.

    2. Na kartě **cíle instalace** nastavte jako cíle verze sady Visual Studio.

    3. Na kartě **assets (prostředky** ) vyberte **Nový**a v dialogovém okně nastavte:

         **Typ**  = **Komponenta MEF**

         **Zdrojový**  = **projekt v aktuálním řešení**

         **Projekt**  = *projektu knihovny tříd*

## <a name="Executing"></a>Provádění obslužné rutiny gesta
 Pro účely testování spusťte obslužnou rutinu gesta v režimu ladění.

#### <a name="to-test-the-gesture-handler"></a>Testování obslužné rutiny gesta

1. Stiskněte klávesu **F5**nebo v nabídce **ladění** klikněte na **Spustit ladění**.

    Spustí se experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

    **Řešení potíží**: Pokud se nový [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nespustí:

   - Pokud máte více než jeden projekt, ujistěte se, že projekt VSIX je nastaven jako projekt po spuštění řešení.

   - V Průzkumník řešení v místní nabídce spouštěcího nebo pouze projektu vyberte možnost Vlastnosti. V editoru vlastností projektu klikněte na kartu **ladění** . Zkontrolujte, zda je řetězec v poli **spustit externí program** úplný název cesty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], obvykle:

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. V experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otevřete nebo vytvořte projekt modelování a otevřete nebo vytvořte diagram modelování. Použijte diagram, který patří k jednomu z typů uvedených v atributech vaší třídy obslužné rutiny gesta.

3. Poklikejte na libovolné místo v diagramu. Měla by být volána obslužná rutina dvojitého kliknutí.

4. Přetáhněte element z Průzkumníka UML do diagramu. Měla by být volána obslužná rutina pro přetahování.

   **Řešení potíží**: Pokud obslužná rutina gesty nefunguje, ujistěte se, že:

- Projekt obslužné rutiny gesta je uveden jako Komponenta MEF na kartě **assets (prostředky** ) ve složce **source. Extensions. manifest** v projektu VSIX.

- Parametry všech atributů `Import` a `Export` jsou platné.

- Metoda `CanDragDrop` nevrací `false`.

- Typ diagramu modelu, který používáte (třída UML, sekvence a tak dále), je uveden jako jeden z atributů třídy obslužné rutiny gesta [ClassDesignerExtension], [SequenceDesignerExtension] atd.

- Pro tento typ cíle a vynechaného prvku již není definována žádná předdefinovaná funkce.

## <a name="Implementing"></a>Implementace obslužné rutiny gesta

### <a name="the-gesture-handler-methods"></a>Metody obslužné rutiny gesta
 Třída obslužné rutiny gesta implementuje a exportuje <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Metody, které je třeba definovat, jsou následující:

|||
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Vraťte `true`, aby bylo možné na tomto cíli vyřadit zdrojový element odkazovaný v `dragEvent`.<br /><br /> Tato metoda by neměla dělat změny modelu. Měla by fungovat rychle, protože se používá k určení stavu šipky, když uživatel přesouvá myš.|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Aktualizujte model na základě zdrojového objektu, na který odkazuje `dragEvent`, a cíle.<br /><br /> Volá se, když uživatel uvolní myš po přetažení.|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` je tvar, na který uživatel dvakrát klikne.|

 Můžete napsat obslužné rutiny, které mohou přijmout nejen UML i celou řadu dalších položek, například soubory, uzly v zobrazení tříd .NET a tak dále. Uživatel může přetáhnout kteroukoli z těchto položek do diagramu UML za předpokladu, že napíšete `OnDragDrop` metodu, která může dekódovat serializovanou formu položek. Metody dekódování se liší od jednoho typu položky k druhé.

 Parametry těchto metod jsou:

- `ShapeElement target`. Tvar nebo diagram, na který uživatel něco přetáhl.

    `ShapeElement` je třída v implementaci, která je umístěná v nástrojích modelování UML. Aby se snížilo riziko uvedení modelu a diagramů UML do nekonzistentního stavu, doporučujeme nepoužívat metody této třídy přímo. Místo toho zabalte prvek do `IShape` a pak použijte metody popsané v tématu [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md).

  - Postup získání `IShape`:

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - Pro získání prvku modelu, který je cílem operace přetažení nebo poklikání:

      ```
      IElement target = targetIShape.Element;
      ```

      Tuto možnost můžete přetypovat na konkrétnější typ elementu.

  - Chcete-li získat úložiště modelu UML, které obsahuje model UML:

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - Chcete-li získat přístup k hostiteli a poskytovateli služeb:

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs`. Tento parametr přenáší serializovanou formu zdrojového objektu operace přetažení:

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     Prvky mnoha různých druhů můžete přetahovat do diagramu, z různých částí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo z plochy Windows. Různé typy prvků jsou kódovány různými způsoby v `IDataObject`. Chcete-li z něj extrahovat prvky, přečtěte si dokumentaci k příslušnému typu objektu.

     Pokud je zdrojový objekt prvkem UML přetaženého z Průzkumníka modelů UML nebo z jiného diagramu UML, přečtěte si téma [získání prvků modelu UML z IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

### <a name="writing-the-code-of-the-methods"></a>Zápis kódu metod
 Další informace o psaní kódu pro čtení a aktualizaci modelu naleznete v tématu [programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md).

 Informace o přístupu k informacím o modelu v operaci přetažení najdete v tématu [získání prvků modelu UML z IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

 Pokud pracujete s sekvenčním diagramem, přečtěte si téma [Úpravy sekvenčních diagramů UML pomocí rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Kromě parametrů metod můžete také deklarovat importovanou vlastnost ve třídě, která poskytuje přístup k aktuálnímu diagramu a modelu.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 Deklarace `IDiagramContext` umožňuje psát kód v metodách, které přistupují k diagramu, aktuálnímu výběru a modelu:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

 Další informace najdete v tématu [Navigace v modelu UML](../modeling/navigate-the-uml-model.md).

## <a name="Installing"></a>Instalace a odinstalace rozšíření
 Rozšíření [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] můžete nainstalovat jak na svém počítači, tak i v jiných počítačích.

#### <a name="to-install-an-extension"></a>Instalace rozšíření

1. V počítači Najděte soubor **. vsix** , který byl SESTAVEN projektem VSIX.

    1. V **Průzkumník řešení**v místní nabídce projektu VSIX vyberte možnost **Otevřít složku v Průzkumníku Windows**.

    2. Vyhledejte soubor **bin \\ \* \\** _YourProject_ **. vsix**

2. Zkopírujte soubor **. vsix** do cílového počítače, do kterého chcete nainstalovat rozšíření. Může to být váš vlastní počítač nebo jiný.

     Cílový počítač musí mít jednu z edic [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], kterou jste zadali v části **source. extension. vsixmanifest**.

3. V cílovém počítači otevřete soubor **. vsix** .

     **Instalační program rozšíření sady Visual Studio** se otevře a nainstaluje rozšíření.

4. Spusťte nebo restartujte [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Odinstalace rozšíření

1. V nabídce **nástroje** vyberte **rozšíření a aktualizace**.

2. Rozbalte položku **nainstalovaná rozšíření**.

3. Vyberte rozšíření a pak zvolte **odinstalovat**.

   Zřídka se vadné rozšíření nedokáže načíst a vytvoří sestavu v okně chyb, ale nezobrazí se ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z:

   *% Localappdata%* **\Local\Microsoft\VisualStudio \\ [verze] \Extensions**

## <a name="DragExample"></a>Případě
 Následující příklad ukazuje, jak vytvořit životnosti v sekvenčním diagramu na základě částí a portů komponenty přetažené z diagramu komponent.

 Pokud ho chcete otestovat, stiskněte klávesu F5. Otevře se experimentální instance aplikace Visual Studio. V této instanci otevřete model UML a vytvořte komponentu v diagramu komponent. Přidejte do této součásti některá rozhraní a součásti interní součásti. Vyberte rozhraní a části. Poté přetáhněte rozhraní a části do sekvenčního diagramu. (Přetáhněte z diagramu komponenty až na kartu pro sekvenční diagram a pak dolů do sekvenčního diagramu.) Životnost se zobrazí pro každé rozhraní a část.

 Další informace o interakcích vazeb s sekvenčními diagramy najdete v tématu [Úpravy sekvenčních diagramů UML pomocí rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Interactions;
using Microsoft.VisualStudio.Uml.CompositeStructures;
using Microsoft.VisualStudio.Uml.Components;

/// <summary>
/// Creates lifelines from component ports and parts.
/// </summary>
[Export(typeof(IGestureExtension))]
[SequenceDesignerExtension]
public class CreateLifelinesFromComponentParts : IGestureExtension
{
  [Import]
  public IDiagramContext Context { get; set; }

  /// <summary>
  /// Called by the modeling framework when
  /// the user drops something on a target.
  /// </summary>
  /// <param name="target">The target shape or diagram </param>
  /// <param name="dragEvent">The item being dragged</param>
  public void OnDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    ISequenceDiagram diagram = Context.CurrentDiagram
            as ISequenceDiagram;
    IInteraction interaction = diagram.Interaction;
    if (interaction == null)
    {
      // Sequence diagram is empty: create an interaction.
      interaction = diagram.ModelStore.Root.CreateInteraction();
      interaction.Name = Context.CurrentDiagram.Name;
      diagram.Bind(interaction);
    }
    foreach (IConnectableElement connectable in
       GetConnectablesFromDrag(dragEvent))
    {
      ILifeline lifeline = interaction.CreateLifeline();
      lifeline.Represents = connectable;
      lifeline.Name = connectable.Name;
    }
  }

  /// <summary>
  /// Called by the modeling framework to determine whether
  /// the user can drop something on a target.
  /// Must not change anything.
  /// </summary>
  /// <param name="target">The target shape or diagram</param>
  /// <param name="dragEvent">The item being dragged</param>
  /// <returns>true if this item can be dropped on this target</returns>
  public bool CanDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);
    return connectables.Count() > 0;
  }

  ///<summary>
  /// Get dragged parts and ports of an IComponent.
  ///</summary>
  private IEnumerable<IConnectableElement>
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)
  {
    foreach (IElement element in
      GetModelElementsFromDragEvent(dragEvent))
    {
      IConnectableElement part = element as IConnectableElement;
      if (part != null)
      {
        yield return part;
      }
    }
  }

  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
          (DiagramDragEventArgs dragEvent)
  {
    //ElementGroupPrototype is the container for
    //dragged and copied elements and toolbox items.
    ElementGroupPrototype prototype =
       dragEvent.Data.
       GetData(typeof(ElementGroupPrototype))
            as ElementGroupPrototype;
    // Locate the originals in the implementation store.
    IElementDirectory implementationDirectory =
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

    return prototype.ProtoElements.Select(
      prototypeElement =>
      {
        ModelElement element = implementationDirectory
          .FindElement(prototypeElement.ElementId);
        ShapeElement shapeElement = element as ShapeElement;
        if (shapeElement != null)
        {
          // Dragged from a diagram.
          return shapeElement.ModelElement as IElement;
        }
        else
        {
          // Dragged from UML Model Explorer.
          return element as IElement;
        }
      });
  }

  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
  {
  }
}

```

 Kód `GetModelElementsFromDragEvent()` je popsán v tématu [získání prvků modelu UML z IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

## <a name="see-also"></a>Viz také
 [Definování a instalace rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md) [rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definování omezení ověření pro programování modelů UML](../modeling/define-validation-constraints-for-uml-models.md) [s rozhraním API UML](../modeling/programming-with-the-uml-api.md)
