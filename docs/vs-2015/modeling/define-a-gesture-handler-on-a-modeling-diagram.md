---
title: Definování obslužné rutiny gest v diagramu modelování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3e448b14a2a24994b9f03a569b0bb568d538bc69
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722184"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Definování obslužné rutiny gest v diagramu modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio můžete definovat příkazy, které jsou prováděny, když uživatel dvakrát klikne nebo přetáhne položky do diagramu UML. Tato rozšíření můžete zabalit do rozšíření integrace Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) a distribuovat ho ostatním uživatelům aplikace Visual Studio.  
  
 Pokud je již vestavěné chování pro typ diagramu a typ prvku, který chcete přetáhnout, možná budete moci přidat nebo přepsat toto chování.  
  
## <a name="requirements"></a>Požadavky  
 Zobrazit [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-gesture-handler"></a>Vytvoření obslužné rutiny gesta  
 Chcete-li definovat obslužnou rutinu gesta pro UML designer, musíte vytvořit třídu, která definuje chování obslužné rutiny gesta a vložit tuto třídu v Visual Studio integrace rozšíření (VSIX). VSIX funguje jako kontejner, který můžete nainstalovat obslužnou rutinu. Existují dva alternativní způsoby definování obslužné rutiny gesta:  
  
-   **Vytvořte obslužnou rutinu gesta ve vlastním souboru VSIX pomocí šablony projektu.** Toto je rychlejší metoda. Pokud nechcete vaši obslužnou rutinu kombinovat s jinými typy rozšíření například rozšířeními ověřování, položky vlastního panelu nástrojů nebo příkazy nabídek, použijte ji.  
  
-   **Vytvořte obslužnou rutinu samostatného gesta a projekty VSIX.** Tuto metodu použijte, pokud chcete sloučit několik typů rozšíření do stejného VSIX. Například pokud vaše obslužná rutina gesta očekává, že model bude dodržovat zvláštní omezení, můžete ho vložit do stejného VSIX jako metodu ověřování.  
  
#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Chcete-li vytvořit obslužnou rutinu gesta ve vlastním souboru VSIX  
  
1. V **nový projekt** dialogovém okně **projekty modelování**vyberte **rozšíření gesta**.  
  
2. Otevřít **.cs** souboru v novém projektu a upravit `GestureExtension` třídu pro implementaci obslužné rutiny gesta.  
  
    Další informace najdete v tématu [implementace obslužné rutiny gesta](#Implementing).  
  
3. Otestujte obslužnou rutinu gesta stisknutím klávesy F5. Další informace najdete v tématu [provádění obslužné rutiny gest](#Executing).  
  
4. Nainstalujte obslužnou rutinu gesta v jiném počítači zkopírováním souboru **bin\\\*\\\*VSIX** , který je sestaven projektem. Další informace najdete v tématu [instalace a odinstalace rozšíření](#Installing).  
  
   Tady je alternativní postup:  
  
#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Chcete-li vytvořit projekt samostatné třídy knihovny (DLL) pro obslužnou rutinu gesta  
  
1. Vytvořte projekt knihovny tříd v novém [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, nebo v existujícím řešení.  
  
   1.  Na **souboru** nabídce zvolte **nový**, **projektu**.  
  
   2.  V části **nainstalované šablony**, rozbalte **Visual C#** nebo **jazyka Visual Basic**, potom v prostředním sloupci zvolte možnost **knihovny tříd**.  
  
2. Přidejte následující odkazy do projektu.  
  
    `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`  
  
    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`  
  
    `Microsoft.VisualStudio.Uml.Interfaces`  
  
    `System.ComponentModel.Composition`  
  
    `System.Windows.Forms`  
  
    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` – Toto budete potřebovat pouze tehdy, pokud rozšiřujete diagramy vrstev. Další informace najdete v tématu [rozšíření diagramů vrstev](../modeling/extend-layer-diagrams.md).  
  
3. Přidejte soubor třídy do projektu a nastavte jeho obsah následujícím kódem.  
  
   > [!NOTE]
   >  Změňte název oboru názvů a třídy podle vašich potřeb.  
  
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
  
    Další informace o tom, co vložit do metod najdete v tématu [implementace obslužné rutiny gesta](#Implementing).  
  
   Příkaz nabídky je nutné přidat do projektu VSIX, který se chová jako kontejner pro instalaci příkazu. Pokud chcete, můžete zahrnout další součásti do stejného VSIX.  
  
#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Přidání zvláštní obslužné rutiny gesta do projektu VSIX  
  
1.  Tento postup není nutné, pokud jste vytvořili obslužnou rutinu gesta s vlastním souborem VSIX.  
  
2.  Vytvořte projekt VSIX, pokud vaše řešení již existuje.  
  
    1.  V **Průzkumníka řešení**, v místní nabídce řešení zvolte **přidat**, **nový projekt**.  
  
    2.  V části **nainstalované šablony**, rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **rozšiřitelnost**. V prostředním sloupci zvolte **projekt VSIX**.  
  
3.  Nastavte projekt VSIX jako projekt po spuštění řešení.  
  
    -   V Průzkumníku řešení v místní nabídce projektu VSIX zvolte **nastavit jako spouštěný projekt**.  
  
4.  V **source.extension.vsixmanifest**, přidejte projekt knihovny tříd obslužné rutiny gesta jako komponentu MEF:  
  
    1.  Na **metadat** kartu, nastavte název souboru VSIX.  
  
    2.  Na **cíle instalace** kartu, nastavte verze sady Visual Studio jako cíle.  
  
    3.  Na **prostředky** kartě **nový**a v dialogovém okně nastavte:  
  
         **Typ** = **Komponenta MEF**  
  
         **Zdroj** = **projekt v aktuálním řešení**  
  
         **Projekt** = *váš projekt knihovny tříd*  
  
##  <a name="Executing"></a> Spuštění obslužné rutiny gesta  
 Pro účely testování spusťte obslužnou rutina gesta v režimu ladění.  
  
#### <a name="to-test-the-gesture-handler"></a>Testování obslužné rutiny gesta  
  
1. Stisknutím klávesy **F5**, nebo **ladění** nabídky, klikněte na tlačítko **spustit ladění**.  
  
    Experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí.  
  
    **Řešení potíží s**: Pokud se nová [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nespustí:  
  
   -   Pokud máte více než jeden projekt, ujistěte se, že projekt VSIX je nastaven jako projekt po spuštění řešení.  
  
   -   V Průzkumníku řešení v místní nabídce startupu nebo projektu, zvolte Vlastnosti. V editoru vlastností projektu, zvolte **ladění** kartu. Ujistěte se, že řetězec v **externí program Start** pole je úplný název cesty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], obvykle:  
  
        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete nebo vytvořte projekt modelování a otevřete nebo vytvořte diagram modelování. Použijte diagram, který patří k jednomu z typů uvedených v atributech vaší třídy obslužné rutiny gesta.  
  
3. Poklepejte na libovolné místo v diagramu. Vaše obslužná rutina poklepání by měla být volána.  
  
4. Přetáhněte element z Průzkumníka UML do diagramu. Vaše obslužná rutina přetažení by měla být volána.  
  
   **Řešení potíží s**: Pokud obslužná rutina gesta nefunguje, ujistěte se, že:  
  
-   Projekt obslužné rutiny gest je uveden jako Komponenta MEF na **prostředky** kartu **source.extensions.manifest** v projektu VSIX.  
  
-   Parametry všech vlastností `Import` a `Export` jsou platné.  
  
-   `CanDragDrop` Metoda nevrací `false`.  
  
-   Typ modelu diagram používáte (UML třídy, sekvence a tak dále) je uveden jako jeden z gesta atributů třídy obslužné rutiny [ClassDesignerExtension], [SequenceDesignerExtension] a tak dále.  
  
-   Neexistuje žádná vestavěná funkce již definovaná pro tento typ cíle a vynechaného prvku.  
  
##  <a name="Implementing"></a> Implementace obslužné rutiny gesta  
  
### <a name="the-gesture-handler-methods"></a>Metody obslužné rutiny gesta  
 Třída obslužné rutiny gesta implementuje a exportuje <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Metody, které je třeba definovat jsou následující:  
  
|||  
|-|-|  
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Vrátí `true` umožňující zdrojového prvku odkazovaného v `dragEvent` přeruší v tomto cíli.<br /><br /> Tato metoda by neměla provést změny modelu. Musí pracovat rychle, protože se používá k určení stavu šipky, jak uživatel přesouvá ukazatel myši.|  
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Aktualizujte model podle zdrojového objektu odkazovaného v `dragEvent`a cíl.<br /><br /> Volá se, když uživatel uvolní tlačítko myši po přetažení.|  
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` je tvar, který uživatel poklepal.|  
  
 Obslužné rutiny, které lze také přijímají nejen UML můžete napsat celou řadu dalších položek, jako jsou soubory, uzly ve zobrazení třídy .NET a tak dále. Uživatel můžete přetáhnout libovolnou z těchto položek do diagramu UML napíšete `OnDragDrop` metodu, která umí dekódovat serializovanou formu položek. Metody dekódování se liší podle položky do jiného.  
  
 Parametry těchto metod jsou:  
  
-   `ShapeElement target`. Tvar nebo diagram, do kterého uživatel něco přetáhl.  
  
     `ShapeElement` je třída implementace, které je základem UML v modelovacích nástrojích. Aby se snížilo riziko uvedení modelu a diagramů do nekonzistentního stavu, doporučujeme vám, že je velmi riskantní používat metody této třídy přímo. Místo toho zabalte prvek do `IShape`a pak použijte metody popsané v [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md).  
  
    -   Získat `IShape`:  
  
        ```  
        IShape targetIShape = target.CreateIShape(target);  
        ```  
  
    -   Chcete-li získat prvek modelu, který je cílen operací přetažení nebo poklepání:  
  
        ```  
        IElement target = targetIShape.Element;  
        ```  
  
         Můžete přetypovat na konkrétnější typ prvku.  
  
    -   Získání úložiště modelu UML, který obsahuje UML model:  
  
        ```  
        IModelStore modelStore =   
          targetIShape.Element.GetModelStore();   
        ```  
  
    -   Chcete-li získat přístup k hostiteli a poskytovateli služby:  
  
        ```  
        target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE  
        ```  
  
-   `DiagramDragEventArgs eventArgs`. Tento parametr provede serializovanou formu zdrojového objektu operace přetažení:  
  
    ```  
    System.Windows.Forms.IDataObject data = eventArgs.Data;    
    ```  
  
     Prvky z mnoha různých druhů můžete přetáhnout do diagramu z různých částí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nebo z plochy Windows. Různé typy prvků jsou kódovány různými způsoby v `IDataObject`. Chcete-li z něj extrahovat prvky, naleznete v dokumentaci pro příslušný typ objektu.  
  
     Pokud zdrojový objekt je prvek UML přetáhli z Průzkumníku modelů UML nebo jiný diagram UML, podívejte se na [elementů modelu UML získat z objektu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Psaní kódu metod  
 Další informace o psaní kódu pro čtení a aktualizaci modelu naleznete v tématu [programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md).  
  
 Informace o přístupu k informacím modelu při operaci přetažení viz [elementů modelu UML získat z objektu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
 Pokud pracujete se sekvenčním diagramem, viz také [sekvenčních diagramech UML upravit s použitím rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 Kromě parametrů metod můžete také deklarovat importovanou vlastnost ve třídě, která poskytuje přístup k aktuálnímu diagramu a modelu.  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  
  
 Deklarace `IDiagramContext` umožňuje psát kód ve vašich metodách, které přistupuje k diagramu, aktuálnímu výběru a modelu:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
 Další informace najdete v tématu [procházení modelu UML](../modeling/navigate-the-uml-model.md).  
  
##  <a name="Installing"></a> Instalace a odinstalace rozšíření  
 Můžete nainstalovat [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozšíření ve vašem počítači i v jiných počítačích.  
  
#### <a name="to-install-an-extension"></a>Instalace rozšíření  
  
1.  V počítači, vyhledejte **VSIX** soubor, který byl vytvořen vaším projektem VSIX.  
  
    1.  V **Průzkumníka řešení**, v místní nabídce projektu VSIX zvolte **otevřít složku v Průzkumníku Windows**.  
  
    2.  Vyhledejte soubor **bin\\\*\\**_YourProject_**VSIX.**  
  
2.  Kopírovat **VSIX** souboru k cílovému počítači, na kterém chcete nainstalovat rozšíření. To může být vlastní počítač nebo jiný.  
  
     Cílový počítač musí mít některou z edicí systému [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , který jste zadali v **source.extension.vsixmanifest**.  
  
3.  V cílovém počítači, otevřete **VSIX** souboru.  
  
     **Instalační program rozšíření sady Visual Studio** otevře a nainstaluje rozšíření.  
  
4.  Spusťte nebo restartujte [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Odinstalace rozšíření  
  
1. Na **nástroje** nabídce zvolte **rozšíření a aktualizace**.  
  
2. Rozbalte **nainstalovaná rozšíření**.  
  
3. Vyberte požadované rozšíření a klikněte na tlačítko **odinstalovat**.  
  
   Jen zřídka se chybné rozšíření se nepodaří načíst a vytvoří sestavu v okně chyb, ale nezobrazí ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z:  
  
   *% LocalAppData %* **\Local\Microsoft\VisualStudio\\\Extensions [verze]**  
  
##  <a name="DragExample"></a> Příklad  
 Následující příklad ukazuje, jak vytvořit životnosti v sekvenčním diagramu podle částí a portů komponentu přetažených z diagramu komponent.  
  
 Chcete-li ho otestovat, stiskněte klávesu F5. Otevře se experimentální instanci sady Visual Studio. V tomto případě otevřete UML model a vytvořte komponentu v diagramu komponent. Přidejte tuto komponentu do některých rozhraní a částí vnitřních komponent. Vyberte rozhraní a části. Potom přetáhněte rozhraní a části do sekvenčního diagramu. (Táhněte od diagramu komponent až po kartu pro sekvenční diagram a potom dolů do sekvenčního diagramu.) Životnost se zobrazí pro každé rozhraní a části.  
  
 Další informace o interakcích vazeb s diagramy sekvencí viz [sekvenčních diagramech UML upravit s použitím rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
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
  
 Kód `GetModelElementsFromDragEvent()` je popsána v [elementů modelu UML získat z objektu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).  
  
## <a name="see-also"></a>Viz také  
 [Definování a instalace rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md)   
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)



