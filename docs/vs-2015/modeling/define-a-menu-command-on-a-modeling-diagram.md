---
title: Definování příkazu nabídky v diagramu modelování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c211c37817ba996105d7496dc49e91db9fa9298e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809100"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Definování příkazu nabídky v diagramu modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio můžete definovat další položky nabídky v místních nabídkách diagramu UML. Můžete řídit, zda příkaz nabídky zobrazí a je povolen v místní nabídce libovolného prvku v diagramu a můžete napsat kód, který se spustí, když uživatel klepne na položku nabídky. Tato rozšíření můžete zabalit do rozšíření integrace Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) a distribuovat ho ostatním uživatelům aplikace Visual Studio.  

## <a name="requirements"></a>Požadavky  
 Zobrazit [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).  

 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="defining-the-menu-command"></a>Definování příkazu nabídky  
 Chcete-li vytvořit příkaz nabídky pro UML designer, musíte vytvořit třídu, která definuje chování příkazu a vložit tuto třídu v Visual Studio integrace rozšíření (VSIX). VSIX funguje jako kontejner, který může příkaz nainstalovat. Existují dva alternativní způsoby definování příkazu nabídky:  

-   **Vytvoření příkazu nabídky ve vlastním souboru VSIX pomocí šablony projektu.** Toto je rychlejší metoda. Pokud nechcete vaše příkazy nabídek kombinovat s jinými typy rozšíření například rozšířeními ověřování, položky vlastního panelu nástrojů nebo obslužnými rutinami gest, použijte ji.  

-   **Vytvořte samostatný příkaz nabídky a projekty VSIX.** Tuto metodu použijte, pokud chcete sloučit několik typů rozšíření do stejného VSIX. Například pokud váš příkaz nabídky očekává, že model bude dodržovat zvláštní omezení, můžete ho vložit do stejného VSIX jako metodu ověřování.  

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Chcete-li vytvořit příkaz nabídky ve vlastním souboru VSIX  

1. V **nový projekt** dialogovém okně **projekty modelování**vyberte **rozšíření příkazu**.  

2. Otevřít **.cs** souboru v novém projektu a upravit `CommandExtension` třídu pro implementaci příkazu.  

    Další informace najdete v tématu [implementace příkazu nabídky](#Implementing).  

3. Další příkazy můžete přidat do tohoto projektu definováním nových tříd.  

4. Otestujte příkaz nabídky stisknutím klávesy F5. Další informace najdete v tématu [spouštění příkazu nabídky](#Executing).  

5. Nainstalujte příkaz nabídky v jiném počítači zkopírováním souboru **bin\\\*\\\*VSIX** , který je sestaven projektem. Další informace najdete v tématu [instalace a odinstalace rozšíření](#Installing).  

   Tady je alternativní postup:  

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Vytvoření příkazu nabídky v projektu samostatné třídy knihovny (DLL)  

1. Vytvořte projekt knihovny tříd v novém řešení Visual Studio nebo v existujícím řešení.  

   1.  Na **souboru** nabídce zvolte **nový**, **projektu**.  

   2.  V části **nainstalované šablony**vyberte **Visual C#** nebo **jazyka Visual Basic**. V prostředním sloupci zvolte **knihovny tříd**.  

   3.  Nastavte **řešení** označující, zda chcete vytvořit nové řešení nebo přidat součást do řešení VSIX, který jste již otevřeli.  

   4.  Nastavte projekt název a umístění a klikněte na tlačítko OK.  

2. Přidejte následující odkazy do projektu.  


   |                                                                                                    Odkaz                                                                                                    |                                                                                                  To umožňuje provést                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         Definovat součásti pomocí [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        Přečíst a změnit vlastnosti modelových prvků.                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      Vytvořit prvky modelu, upravit obrazce v diagramech.                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[version]                                                                                  | Definování obslužných rutin událostí modelu.<br /><br /> Zapouzdření sérii změn do modelu. Další informace najdete v tématu [UML propojení aktualizací modelů pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]<br /><br /> (není vždy nutné)                                                             |                                                                                   Přístup k dalším prvkům diagramu pro obslužné rutiny gest.                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> Vyžaduje se jenom pro příkazy v diagramech vrstev. Další informace najdete v tématu [rozšíření diagramů vrstev](../modeling/extend-layer-diagrams.md). |                                                                                             Definujte příkazy diagramu vrstva.                                                                                              |


3. Přidejte soubor třídy do projektu a nastavte jeho obsah následujícím kódem.  

   > [!NOTE]
   >  Změnit obor názvů, název třídy a hodnotu vrácenou příkazem `Text` dle požadavků.  
   >   
   >  Pokud definujete více příkazů v nabídce jsou uvedeny v abecedním pořadí názvů tříd.  

   ```  
   using System.ComponentModel.Composition;     
   using System.Linq;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
   using Microsoft.VisualStudio.Uml.Classes;   
       // ADD other UML namespaces if required  

   namespace UMLmenu1 // CHANGE  
   {  
     // DELETE any of these attributes if the command  
     // should not appear in some types of diagram.  
     [ClassDesignerExtension]  
     [ActivityDesignerExtension]  
     [ComponentDesignerExtension]  
     [SequenceDesignerExtension]  
     [UseCaseDesignerExtension]   
     // [LayerDesignerExtension]  

     // All menu commands must export ICommandExtension:  
     [Export (typeof(ICommandExtension))]  
     // CHANGE class name – determines order of appearance on menu:  
     public class Menu1 : ICommandExtension  
     {  
       [Import]  
       public IDiagramContext DiagramContext { get; set; }  

       public void QueryStatus(IMenuCommand command)  
       { // Set command.Visible or command.Enabled to false  
         // to disable the menu command.  
         command.Visible = command.Enabled = true;  
       }  

       public string Text  
       {  
         get { return "MENU COMMAND LABEL"; }  
       }  

       public void Execute(IMenuCommand command)  
       {  
         // A selection of starting points:  
         IDiagram diagram = this.DiagramContext.CurrentDiagram;  
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
         { IElement element = shape.Element; }  
         IModelStore modelStore = diagram.ModelStore;  
         IModel model = modelStore.Root;  
         foreach (IElement element in modelStore.AllInstances<IClass>())   
         { }  
       }  
     }  
   }  
   ```  

    Další informace o tom, co vložit do metod najdete v tématu [implementace příkazu nabídky](#Implementing).  

   Příkaz nabídky je nutné přidat do projektu VSIX, který se chová jako kontejner pro instalaci příkazu. Pokud chcete, můžete zahrnout další součásti do stejného VSIX.  

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Přidání příkazu nabídky do projektu VSIX  

1.  Tento postup není nutné, pokud jste vytvořili příkaz nabídky s vlastním souborem VSIX.  

2.  Vytvořte projekt VSIX, pokud vaše řešení již existuje.  

    1.  V **Průzkumníka řešení**, v místní nabídce řešení zvolte **přidat**, **nový projekt**.  

    2.  V části **nainstalované šablony**, rozbalte **Visual C#** nebo **jazyka Visual Basic**, klikněte na tlačítko **rozšiřitelnost**. V prostředním sloupci zvolte **projekt VSIX**.  

3.  V Průzkumníku řešení v místní nabídce projektu VSIX zvolte **nastavit jako spouštěný projekt**.  

4.  Otevřít **source.extension.vsixmanifest**.  

    1.  Na **metadat** kartu, nastavte název souboru VSIX.  

    2.  Na **cíle instalace** kartu, nastavte verze sady Visual Studio jako cíle.  

    3.  Na **prostředky** kartě **nový**a v dialogovém okně nastavte:  

         **Typ** = **Komponenta MEF**  

         **Zdroj** = **projekt v aktuálním řešení**  

         **Projekt** = *váš projekt knihovny tříd*  

##  <a name="Implementing"></a> Implementace příkazu nabídky  
 Příkaz nabídky implementuje požadované metody pro <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.  

|||  
|-|-|  
|`string Text { get; }`|Vrátí popisek položky nabídky.|  
|`void QueryStatus(IMenuCommand command);`|Volá se, když uživatel klepne pravým tlačítkem myši v diagramu.<br /><br /> Tato metoda by neměla změnit model.<br /><br /> Použití `DiagramContext.CurrentDiagram.SelectedShapes` k určení, zda má příkaz Zobrazit a povolit.<br /><br /> Nastavte:<br /><br /> -   `command.Visible` k `true` Pokud příkaz musí být uvedena v nabídce, když uživatel klepne pravým tlačítkem myši v diagramu<br />-   `command.Enabled` k `true` Pokud uživatel může kliknout na příkaz v nabídce<br />-   `command.Text` Chcete-li nastavit popisek nabídky dynamicky|  
|`void Execute (IMenuCommand command);`|Volá se, když uživatel klepne na položku nabídky, pokud je viditelná a povolená.|  

### <a name="accessing-the-model-in-code"></a>Přístup k modelu v kódu  
 Zahrnutí následujícího prohlášení do třídy příkazů nabídky:  

```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  

 ...  

 Deklarace `IDiagramContext` umožňuje psát kód ve vašich metodách, které přistupuje k diagramu, aktuálnímu výběru a modelu:  

```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}  
```  

### <a name="navigating-and-updating-the-model"></a>Procházení a aktualizace modelu  
 Prvky modelu UML jsou všechny dostupné prostřednictvím rozhraní API. Z aktuálního výběru nebo kořen modelu můžete přístup ke všem ostatním prvkům. Další informace najdete v tématu [procházení modelu UML](../modeling/navigate-the-uml-model.md) a [programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md).  

 Pokud pracujete se sekvenčním diagramem, viz také [sekvenčních diagramech UML upravit s použitím rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  

 Rozhraní API také umožňuje měnit vlastnosti prvků, odstraňovat prvky a vztahy a vytvářet nové prvky a vztahy.  

 Ve výchozím nastavení budou provedeny jednotlivé změny, které provedete ve své metodě Execute v oddělené transakci. Uživatel bude moci vrátit každou změnu zvlášť. Pokud chcete seskupit změny do jediné transakce, použijte <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> jak je popsáno v [UML propojení aktualizací modelů pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md).  

### <a name="use-the-ui-thread-for-updates"></a>Použijte vlákno uživatelského rozhraní pro aktualizace  
 V některých případech může být užitečné provést aktualizace modelu z vlákna na pozadí. Například pokud váš příkaz načte data z pomalého zdroje, můžete provést načítání ve vláknu na tak, aby uživatel můžete zobrazit změny, když probíhají a operaci zrušit, pokud je nutné.  

 Nicméně byste měli vědět, že úložiště modelu není bezpečné pro vlákna. Vždy doporučujeme provádět aktualizace pomocí vlákna uživatelského rozhraní (UI) a pokud je to možné, zabránit uživateli v provádění úprav probíhá operace na pozadí. Příklad najdete v tématu [aktualizace modelu UML z vlákna na pozadí](../modeling/update-a-uml-model-from-a-background-thread.md).  

##  <a name="Executing"></a> Spouštění příkazu nabídky  
 Pro účely testování proveďte příkaz v režimu ladění.  

#### <a name="to-test-the-menu-command"></a>Chcete-li otestovat příkaz nabídky  

1.  Stisknutím klávesy **F5**, nebo **ladění** nabídce zvolte **spustit ladění**.  

     Experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí.  

     **Řešení potíží s**: Pokud se nová [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nespustí:  

    -   Pokud máte více než jeden projekt, ujistěte se, že projekt VSIX je nastaven jako projekt po spuštění řešení.  

    -   V Průzkumníku řešení zvolte v místní nabídce startupu nebo projektu, **vlastnosti**. V editoru vlastností projektu, vyberte **ladění** kartu. Ujistěte se, že řetězec v **externí program Start** pole je úplný název cesty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], obvykle:  

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  

2.  V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete nebo vytvořte projekt modelování a otevřete nebo vytvořte diagram modelování. Použijte diagram, který patří k jednomu z typů, které jsou uvedeny v atributech vaší třídy příkazu nabídky.  

3.  Otevřete místní nabídku kdekoli v diagramu. Váš příkaz se zobrazí v nabídce.  

     **Řešení potíží s**: Pokud příkaz v nabídce nezobrazí, ujistěte se, že:  

    -   Projekt příkazu nabídky je uveden jako Komponenta MEF na **prostředky** kartu **source.extensions.manifest** v projektu VSIX.  

    -   Parametry `Import` a `Export` jsou platné.  

    -   `QueryStatus` Metoda není nastavení `command`.`Enabled` nebo `Visible` polím `false`.  

    -   Typ modelového diagramu, že používáte (UML třídy, sekvence a tak dále) je uveden jako jeden z atributů třídy příkazu nabídky `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` a tak dále.  

##  <a name="Installing"></a> Instalace a odinstalace rozšíření  
 Můžete nainstalovat [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozšíření ve vašem počítači i v jiných počítačích.  

#### <a name="to-install-an-extension"></a>Instalace rozšíření  

1.  V počítači, vyhledejte **VSIX** soubor, který byl vytvořen vaším projektem VSIX.  

    1.  V **Průzkumníka řešení**, v místní nabídce projektu VSIX zvolte **otevřít složku v Průzkumníku Windows**.  

    2.  Vyhledejte soubor **bin\\\*\\**_YourProject_**VSIX.**  

2.  Kopírovat **VSIX** souboru k cílovému počítači, na kterém chcete nainstalovat rozšíření. To může být vlastní počítač nebo jiný.  

     Cílový počítač musí mít některou z edicí systému [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , který jste zadali v **source.extension.vsixmanifest**.  

3.  V cílovém počítači, otevřete **VSIX** souboru, například poklepáním.  

     **Instalační program rozšíření sady Visual Studio** otevře a nainstaluje rozšíření.  

4.  Spusťte nebo restartujte [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  

#### <a name="to-uninstall-an-extension"></a>Odinstalace rozšíření  

1. Na **nástroje** nabídce zvolte **rozšíření a aktualizace**.  

2. Rozbalte **nainstalovaná rozšíření**.  

3. Vyberte požadované rozšíření a klikněte na tlačítko **odinstalovat**.  

   Jen zřídka se chybné rozšíření se nepodaří načíst a vytvoří sestavu v okně chyb, ale nezobrazí ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z:  

   *% LocalAppData %* **\Local\Microsoft\VisualStudio\\\Extensions [verze]**  

##  <a name="MenuExample"></a> Příklad  
 Následující příklad ukazuje kód pro příkaz nabídky, který bude Zamění názvy dvou prvků v diagramu tříd. Tento kód musí být součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření projektu a nainstalovat, jak je popsáno v předchozích částech.  

```  
using System.Collections.Generic; // for IEnumerable  
using System.ComponentModel.Composition;  
  // for [Import], [Export]  
using System.Linq; // for IEnumerable extensions  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
  // for IDiagramContext  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
  // for designer extension attributes  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  // for ShapeElement  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext  
using Microsoft.VisualStudio.Uml.Classes;  
  // for class diagrams, packages  

/// <summary>  
/// Extension to swap names of classes in a class diagram.  
/// </summary>  
namespace SwapClassNames  
{  
  // Declare the class as an MEF component:  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  // Add more ExportMetadata attributes to make  
  // the command appear on diagrams of other types.  
  public class NameSwapper : ICommandExtension  
  {  
  // MEF required interfaces:  
  [Import]  
  public IDiagramContext Context { get; set; }  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  

  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  /// <param name="command"></param>  
  public void Execute(IMenuCommand command)  
  {  
    // Get selected shapes that are IClassifiers -  
    // IClasses, IInterfaces, IEnumerators.  
    var selectedShapes = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  

    // Get model elements displayed by shapes.  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  

    // Do the swap in a transaction so that user  
    // cannot undo one change without the other.  
    using (ILinkedUndoTransaction transaction =  
    LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
    string firstName = firstElement.Name;  
    firstElement.Name = lastElement.Name;  
    lastElement.Name = firstName;  
    transaction.Commit();  
    }  
  }  

  /// <summary>  
  /// Called by Visual Studio to determine whether  
  /// menu item should be visible and enabled.  
  /// </summary>  
  public void QueryStatus(IMenuCommand command)  
  {   
    int selectedClassifiers = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>().Count();  
    command.Visible = selectedClassifiers > 0;  
    command.Enabled = selectedClassifiers == 2;  
  }  

  /// <summary>  
  /// Name of the menu command.  
  /// </summary>  
  public string Text  
  {  
    get { return "Swap Names"; }  
  }  
  }  

}  
```  

## <a name="see-also"></a>Viz také  
 [Definování a instalace rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md)   
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Úpravy sekvenčních diagramů UML pomocí rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)   
 [Programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md)   
 [Ukázka: Příkaz pro zarovnání tvarů v diagramu UML](http://go.microsoft.com/fwlink/?LinkID=213809)



