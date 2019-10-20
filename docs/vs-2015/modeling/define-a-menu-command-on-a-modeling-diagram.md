---
title: Definování příkazu nabídky v diagramu modelování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 87acbb53fd8fe5eae744aa4ef72c808da8eb6642
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663478"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Definování příkazu nabídky v diagramu modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete definovat další položky nabídky v místních nabídkách diagramu UML. Můžete určit, zda se příkaz nabídky zobrazí a je povolen v místní nabídce libovolného prvku v diagramu, a můžete napsat kód, který se spustí, když uživatel zvolí položku nabídky. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) a distribuovat je ostatním uživatelům aplikace Visual Studio.

## <a name="requirements"></a>Požadavky
 Viz [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="defining-the-menu-command"></a>Definování příkazu nabídky
 Chcete-li vytvořit příkaz nabídky pro návrháře UML, je nutné vytvořit třídu, která definuje chování příkazu, a vložit třídu do rozšíření integrace sady Visual Studio (VSIX). VSIX funguje jako kontejner, který může nainstalovat příkaz. Existují dvě alternativní metody definování příkazu nabídky:

- **Vytvořte příkaz nabídky ve vlastním souboru VSIX pomocí šablony projektu.** Toto je rychlejší metoda. Použijte ji v případě, že nechcete kombinovat příkazy nabídky s jinými typy rozšíření, jako jsou například rozšíření ověřování, vlastní položky sady nástrojů nebo obslužné rutiny gest.

- **Vytvořte samostatné příkazy nabídky a VSIX projekty.** Tuto metodu použijte, pokud chcete zkombinovat několik typů rozšíření do stejného VSIX. Například pokud příkaz nabídky očekává, že model bude dodržovat konkrétní omezení, můžete jej vložit do stejného VSIX jako metodu ověřování.

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Vytvoření příkazu nabídky ve vlastním souboru VSIX

1. V dialogovém okně **Nový projekt** , v části **modelování projektů**, vyberte možnost **rozšíření příkazu**.

2. Otevřete soubor **. cs** v novém projektu a upravte třídu `CommandExtension` pro implementaci příkazu.

    Další informace naleznete v tématu [implementace příkazu nabídky](#Implementing).

3. Do tohoto projektu můžete přidat další příkazy definováním nových tříd.

4. Otestujte příkaz nabídky stisknutím klávesy F5. Další informace naleznete v tématu [provádění příkazu nabídky](#Executing).

5. Nainstalujte příkaz nabídky do jiného počítače zkopírováním souboru **bin \\ \* \\ \*. vsix** sestaveného vaším projektem. Další informace najdete v tématu [instalace a odinstalace rozšíření](#Installing).

   Tady je alternativní postup:

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Vytvoření příkazu nabídky v samostatném projektu knihovny tříd (DLL)

1. Vytvořte projekt knihovny tříd, a to buď v novém řešení sady Visual Studio, nebo v existujícím řešení.

   1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**.

   2. V části **Nainstalované šablony**vyberte **možnost C# Visual** nebo **Visual Basic**. V prostředním sloupci vyberte možnost **Knihovna tříd**.

   3. Nastavte **řešení** tak, aby označovalo, zda chcete vytvořit nové řešení nebo přidat komponentu do řešení VSIX, které jste již otevřeli.

   4. Nastavte název projektu a umístění a klikněte na tlačítko OK.

2. Do projektu přidejte následující odkazy.

   |                                                                                                    Odkaz                                                                                                    |                                                                                                  Co vám to umožňuje                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System. ComponentModel. složení                                                                                        |                                         Definujte komponenty pomocí [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft. VisualStudio. Uml. Interfaces                                                                                      |                                                                                        Čtení a změna vlastností prvků modelu.                                                                                         |
   |                                                                             Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost                                                                              |                                                                                      Vytváření elementů modelu, úprava tvarů v diagramech.                                                                                       |
   |                                                                                  Microsoft. VisualStudio. Modeling. SDK. znění                                                                                  | Definujte obslužné rutiny událostí modelu.<br /><br /> Zapouzdří řady změn do modelu. Další informace najdete v tématu [propojení aktualizací modelů UML pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft. VisualStudio. Modeling. SDK. Diagrams. znění<br /><br /> (není vždycky nutné)                                                             |                                                                                   Přístup k dalším prvkům diagramu pro obslužné rutiny gesta.                                                                                   |
   | Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost. vrstva<br /><br /> Vyžaduje se jenom pro příkazy v diagramech vrstev. Další informace naleznete v tématu [Rozšířené diagramy vrstev](../modeling/extend-layer-diagrams.md). |                                                                                             Definujte příkazy v diagramu vrstev.                                                                                              |

3. Přidejte soubor třídy do projektu a nastavte jeho obsah na následující kód.

   > [!NOTE]
   > Změňte obor názvů, název třídy a hodnotu vrácenou `Text` na vaše preference.
   >
   >  Pokud definujete více příkazů, zobrazí se v nabídce v abecedním pořadí názvů tříd.

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

    Další informace o tom, co vložit do metod, naleznete v tématu [implementace příkazu nabídky](#Implementing).

   Příkaz nabídky je nutné přidat do projektu VSIX, který slouží jako kontejner pro instalaci příkazu. Pokud chcete, můžete zahrnout další komponenty do stejného VSIX.

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Přidání příkazu nabídky do projektu VSIX

1. Tento postup nebudete potřebovat, pokud jste vytvořili příkaz nabídky s vlastním souborem VSIX.

2. Vytvořte projekt VSIX, pokud vaše řešení již jednu nemá.

    1. V **Průzkumník řešení**v místní nabídce řešení vyberte možnost **Přidat**, **Nový projekt**.

    2. V části **Nainstalované šablony**rozbalte **položku C# Visual** nebo **Visual Basic**a pak zvolte možnost **rozšiřitelnost**. V prostředním sloupci vyberte **projekt VSIX**.

3. V Průzkumník řešení v místní nabídce projektu VSIX vyberte **nastavit jako projekt po spuštění**.

4. Otevřete **source. extension. vsixmanifest**.

    1. Na kartě **metadata** nastavte název VSIX.

    2. Na kartě **cíle instalace** nastavte jako cíle verze sady Visual Studio.

    3. Na kartě **assets (prostředky** ) vyberte **Nový**a v dialogovém okně nastavte:

         **Typ**  = **Komponenta MEF**

         **Zdrojový**  = **projekt v aktuálním řešení**

         **Projekt**  = *projektu knihovny tříd*

## <a name="Implementing"></a>Implementace příkazu nabídky
 Třída příkazu nabídky implementuje požadované metody pro <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.

|||
|-|-|
|`string Text { get; }`|Vrátí popisek položky nabídky.|
|`void QueryStatus(IMenuCommand command);`|Volá se, když uživatel klikne pravým tlačítkem myši v diagramu.<br /><br /> Tato metoda by neměla měnit model.<br /><br /> Pomocí `DiagramContext.CurrentDiagram.SelectedShapes` určete, zda se má příkaz Zobrazit a povolit.<br /><br /> Stanovenými<br /><br /> -    `command.Visible` na `true`, pokud se příkaz musí zobrazit v nabídce, když uživatel klikne pravým tlačítkem myši v diagramu.<br />-    `command.Enabled` na `true`, pokud uživatel může kliknout na příkaz v nabídce<br />-    `command.Text` k nastavení popisku nabídky dynamicky|
|`void Execute (IMenuCommand command);`|Volá se, když uživatel klikne na položku nabídky, pokud je viditelný a povolený.|

### <a name="accessing-the-model-in-code"></a>Přístup k modelu v kódu
 Zahrnutí následující deklarace do třídy příkazu nabídky:

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 ...

 Deklarace `IDiagramContext` umožňuje psát kód v metodách, které přistupují k diagramu, aktuálnímu výběru a modelu:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}
```

### <a name="navigating-and-updating-the-model"></a>Navigace a aktualizace modelu
 Prvky modelu UML jsou k dispozici prostřednictvím rozhraní API. Z aktuálního výběru nebo z kořene modelu můžete získat přístup ke všem ostatním prvkům. Další informace najdete v tématu [navigace modelu UML](../modeling/navigate-the-uml-model.md) a [programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md).

 Pokud pracujete s sekvenčním diagramem, přečtěte si téma [Úpravy sekvenčních diagramů UML pomocí rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Rozhraní API také umožňuje změnit vlastnosti prvků, odstranit prvky a vztahy a vytvořit nové prvky a vztahy.

 Ve výchozím nastavení se každá změna, kterou uděláte v metodě Execute, provede v samostatné transakci. Uživatel bude moci vrátit každou změnu samostatně. Chcete-li seskupit změny do jediné transakce, použijte <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction>, jak je popsáno v tématu [propojení aktualizací modelů UML pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md).

### <a name="use-the-ui-thread-for-updates"></a>Použití vlákna uživatelského rozhraní pro aktualizace
 V některých případech může být užitečné provést aktualizace modelu z vlákna na pozadí. Například pokud váš příkaz načte data z pomalého prostředku, můžete provést načítání ve vlákně vláknu, aby uživatel mohl zobrazit změny, které se právě probíhají, a operaci zrušit, pokud je to nutné.

 Nicméně byste si měli být vědomi, že úložiště modelu není bezpečné pro přístup z více vláken. Při provádění aktualizací byste měli vždy použít vlákno uživatelského rozhraní (UI), a pokud je to možné, zabráníte uživateli v provádění úprav v průběhu operace na pozadí. Příklad naleznete v tématu [aktualizace modelu UML z vlákna na pozadí](../modeling/update-a-uml-model-from-a-background-thread.md).

## <a name="Executing"></a>Provedení příkazu nabídky
 Pro účely testování spusťte příkaz v režimu ladění.

#### <a name="to-test-the-menu-command"></a>Otestování příkazu nabídky

1. Stiskněte klávesu **F5**nebo v nabídce **ladění** zvolte možnost **Spustit ladění**.

     Spustí se experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

     **Řešení potíží**: Pokud se nový [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nespustí:

    - Pokud máte více než jeden projekt, ujistěte se, že projekt VSIX je nastaven jako projekt po spuštění řešení.

    - V Průzkumník řešení v místní nabídce spouštěcího nebo pouze projektu vyberte možnost **vlastnosti**. V editoru vlastností projektu vyberte kartu **ladění** . Zajistěte, aby byl řetězec v poli **spustit externí program** úplný název cesty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], obvykle:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. V experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otevřete nebo vytvořte projekt modelování a otevřete nebo vytvořte diagram modelování. Použijte diagram, který patří k jednomu z typů, které jsou uvedeny v atributech třídy příkazu nabídky.

3. Otevřete místní nabídku kdekoli v diagramu. Váš příkaz by se měl zobrazit v nabídce.

     **Řešení potíží**: Pokud se příkaz v nabídce nezobrazí, ujistěte se, že:

    - Projekt příkazu nabídky je uveden jako Komponenta MEF na kartě **assets (prostředky** ) ve složce **source. Extensions. manifest** v projektu VSIX.

    - Parametry atributů `Import` a `Export` jsou platné.

    - Metoda `QueryStatus` nenastavuje `command`. `Enabled` nebo `Visible` pole, která chcete `false`.

    - Typ diagramu modelu, který používáte (třída UML, sekvence a tak dále), je uveden jako jeden z atributů třídy příkazu nabídky `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` a tak dále.

## <a name="Installing"></a>Instalace a odinstalace rozšíření
 Rozšíření [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] můžete nainstalovat jak na svém počítači, tak i v jiných počítačích.

#### <a name="to-install-an-extension"></a>Instalace rozšíření

1. V počítači Najděte soubor **. vsix** , který byl SESTAVEN projektem VSIX.

    1. V **Průzkumník řešení**v místní nabídce projektu VSIX vyberte možnost **Otevřít složku v Průzkumníku Windows**.

    2. Vyhledejte soubor **bin \\ \* \\** _YourProject_ **. vsix**

2. Zkopírujte soubor **. vsix** do cílového počítače, do kterého chcete nainstalovat rozšíření. Může to být váš vlastní počítač nebo jiný.

     Cílový počítač musí mít jednu z edic [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], kterou jste zadali v části **source. extension. vsixmanifest**.

3. V cílovém počítači otevřete soubor **. vsix** , například dvojitým kliknutím na něj.

     **Instalační program rozšíření sady Visual Studio** se otevře a nainstaluje rozšíření.

4. Spusťte nebo restartujte [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Odinstalace rozšíření

1. V nabídce **nástroje** vyberte **rozšíření a aktualizace**.

2. Rozbalte položku **nainstalovaná rozšíření**.

3. Vyberte rozšíření a pak zvolte **odinstalovat**.

   Zřídka se vadné rozšíření nedokáže načíst a vytvoří sestavu v okně chyb, ale nezobrazí se ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z:

   *% Localappdata%* **\Local\Microsoft\VisualStudio \\ [verze] \Extensions**

## <a name="MenuExample"></a>Případě
 Následující příklad ukazuje kód pro příkaz nabídky, který bude zakódovat názvy dvou prvků v diagramu tříd. Tento kód musí být sestaven v projektu rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a nainstalován tak, jak je popsáno v předchozích částech.

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
 [Definování a instalace rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md) [rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [Definování obslužné rutiny gesta v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md) definování [omezení ověření pro úpravy modelů UML](../modeling/define-validation-constraints-for-uml-models.md) [ Sekvenční diagramy UML pomocí programování rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md) [s ukázkou rozhraní API UML](../modeling/programming-with-the-uml-api.md) [– příkaz pro zarovnání obrazců v diagramu UML](http://go.microsoft.com/fwlink/?LinkID=213809)
