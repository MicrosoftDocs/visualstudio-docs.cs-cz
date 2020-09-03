---
title: Přidávání příkazů a gest do diagramů vrstev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7b0c54975cdd5bc86f77dddbd5ca1a56c1896394
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655315"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Přidávání příkazů a gest do diagramů vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramech vrstev v aplikaci Visual Studio můžete definovat příkazy kontextové nabídky a obslužné rutiny gest. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio (VSIX), které můžete distribuovat dalším uživatelům aplikace Visual Studio.

 Pokud chcete, můžete definovat několik obslužných rutin příkazů a gest v jednom projektu sady Visual Studio. Můžete také zkombinovat několik takových projektů do jednoho VSIX. Můžete například definovat jeden VSIX, který obsahuje příkazy vrstev, jazyk specifický pro doménu a příkazy pro diagramy UML.

> [!NOTE]
> Můžete také přizpůsobit ověření architektury, ve kterém je zdrojový kód uživatele porovnán s diagramy vrstev. Ověřování architektury byste měli definovat v samostatném projektu sady Visual Studio. Můžete ji přidat ke stejnému VSIX jako další rozšíření. Další informace najdete v tématu [Přidání ověření vlastní architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Požadavky
 Viz [požadavky](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definování příkazu nebo gesta v novém VSIX
 Nejrychlejší způsob, jak vytvořit rozšíření, je použití šablony projektu. Tím se umístí kód a manifest VSIX do stejného projektu.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Definování rozšíření pomocí šablony projektu

1. Vytvořte projekt v novém řešení pomocí příkazu **Nový projekt** v nabídce **soubor** .

2. V dialogovém okně **Nový projekt** , v části **modelování projektů**, vyberte buď **rozšíření příkazu návrháře vrstvy** nebo **rozšíření gesta návrháře vrstvy**.

    Šablona vytvoří projekt, který obsahuje malý pracovní příklad.

3. Rozšíření otestujete stisknutím **kláves CTRL + F5** nebo **F5**.

    Spustí se experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . V této instanci vytvořte diagram vrstev. Vaše příkazy nebo rozšíření gesta by mělo fungovat v tomto diagramu.

4. Zavřete experimentální instanci a upravte vzorový kód. Další informace najdete v tématu [navigace a aktualizace modelů vrstev v programovém kódu](../modeling/navigate-and-update-layer-models-in-program-code.md).

5. Do stejného projektu můžete přidat další obslužné rutiny příkazu nebo gesta. Další informace naleznete v jedné z následujících částí:

    [Definování příkazu nabídky](#command)

    [Definování obslužné rutiny gesta](#gesture)

6. Chcete-li nainstalovat rozšíření v hlavní instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo v jiném počítači, vyhledejte v *přihrádce \\ *soubor **. vsix** . Zkopírujte ho do počítače, kam ho chcete nainstalovat, a dvakrát na něj klikněte. Pokud ho chcete odinstalovat, použijte **rozšíření a aktualizace** v nabídce **nástroje** .

## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Přidání příkazu nebo gesta do samostatného souboru VSIX
 Pokud chcete vytvořit jeden VSIX, který obsahuje příkazy, validátory vrstev a další rozšíření, doporučujeme vytvořit jeden projekt k definování VSIX a samostatné projekty pro obslužné rutiny. Informace o dalších typech rozšíření modelování najdete v tématu [rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Přidání rozšíření vrstvy do samostatného souboru VSIX

1. Vytvořte projekt knihovny tříd v novém nebo existujícím řešení sady Visual Studio. V dialogovém okně **Nový projekt** klikněte na položku **Visual C#** a potom klikněte na možnost **Knihovna tříd**. Tento projekt bude obsahovat třídy obslužné rutiny příkazu nebo gesta.

    > [!NOTE]
    > Můžete definovat více než jednu třídu příkazu nebo obslužné rutiny gesta v jedné knihovně tříd, ale měli byste definovat třídy ověřování vrstvy v samostatné knihovně tříd.

2. Identifikujte nebo vytvořte projekt VSIX ve vašem řešení. Projekt VSIX obsahuje soubor s názvem **source. extension. vsixmanifest**. Chcete-li přidat projekt VSIX:

    1. V dialogovém okně **Nový projekt** rozbalte položku **Visual C#**, potom klikněte na možnost **rozšiřitelnost**a potom klikněte na možnost **projekt VSIX**.

    2. V Průzkumník řešení klikněte pravým tlačítkem na projekt VSIX a pak klikněte na **nastavit jako spouštěný projekt**.

    3. Klikněte na **Vybrat edice** a ujistěte se, že je zaškrtnuté políčko **Visual Studio** .

3. V části **source. extension. vsixmanifest**v části **assety**přidejte projekt obslužné rutiny příkazu nebo gesta jako komponentu MEF.

    1. Na kartě **assets**. klikněte na tlačítko **Nový**.

    2. V **typu**vyberte **Microsoft. VisualStudio. MefComponent**.

    3. V části **zdroj**vyberte **projekt v aktuálním řešení** a vyberte název projektu obslužné rutiny příkazu nebo gesta.

    4. Uložte soubor.

4. Vraťte se do projektu obslužné rutiny příkazu nebo gesta a přidejte následující odkazy projektu.

|**Odkaz**|**Co vám to umožňuje**|
|-------------------|------------------------------------|
|Program Files\Microsoft Visual Studio [verze] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Vytváření a úpravy vrstev|
|Microsoft. VisualStudio. Uml. Interfaces|Vytváření a úpravy vrstev|
|Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost|Úprava tvarů v diagramech|
|System. ComponentModel. složení|Definovat komponenty pomocí Managed Extensibility Framework (MEF)|
|Microsoft. VisualStudio. Modeling. SDK. znění|Definování rozšíření modelování|
|Microsoft. VisualStudio. Modeling. SDK. Diagrams. znění|Aktualizovat obrazce a diagramy|

1. Upravte soubor třídy v projektu knihovny tříd jazyka C# tak, aby obsahoval kód pro vaše rozšíření. Další informace naleznete v jedné z následujících částí:

     [Definování příkazu nabídky](#command)

     [Definování obslužné rutiny gesta](#gesture)

     Viz také [navigace a aktualizace modelů vrstev v programovém kódu](../modeling/navigate-and-update-layer-models-in-program-code.md).

2. Pokud chcete funkci otestovat, stiskněte klávesy CTRL + F5 nebo F5. Otevře se experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . V této instanci vytvořte nebo otevřete diagram vrstev.

3. Chcete-li nainstalovat VSIX v hlavní instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo v jiném počítači, vyhledejte soubor **. vsix** v adresáři **bin** projektu VSIX. Zkopírujte jej do počítače, kam chcete nainstalovat VSIX. Dvakrát klikněte na soubor VSIX v Průzkumníkovi Windows (Průzkumník souborů ve Windows 8).

     Pokud ho chcete odinstalovat, použijte **rozšíření a aktualizace** v nabídce **nástroje** .

## <a name="defining-a-menu-command"></a><a name="command"></a> Definování příkazu nabídky
 Můžete přidat další definice příkazů nabídky pro existující gesto nebo projekt příkazu. Každý příkaz je definován třídou, která má následující vlastnosti:

- Třída je deklarována takto:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- Obor názvů a název třídy jsou neimportované.

- Metody, které implementují, `ICommandExtension` jsou následující:

  - `string Text {get;}` – Popisek, který se zobrazí v nabídce.

  - `void QueryStatus(IMenuCommand command)` – volána, když uživatel klikne pravým tlačítkem myši na diagram a určí, zda má být příkaz viditelný a povolen pro aktuální výběr uživatele.

  - `void Execute(IMenuCommand command)` – volána, když uživatel vybere příkaz.

- Chcete-li zjistit aktuální výběr, můžete importovat `IDiagramContext` :

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

  Další informace najdete v tématu [navigace a aktualizace modelů vrstev v programovém kódu](../modeling/navigate-and-update-layer-models-in-program-code.md).

  Chcete-li přidat nový příkaz, vytvořte nový soubor kódu, který obsahuje následující ukázku. Pak ho otestujte a upravte.

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for Layer diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> Definování obslužné rutiny gesta
 Obslužná rutina gesta reaguje, když uživatel přetáhne položky do diagramu vrstev a když uživatel dvakrát klikne na libovolné místo v diagramu.

 Do stávajícího projektu VSIX obslužné rutiny příkazu nebo gesta můžete přidat soubor kódu, který definuje obslužnou rutinu gesta:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;
namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

 Všimněte si následujících bodů pro obslužné rutiny gesta:

- Členy `IGestureExtension` jsou následující:

   Příkaz- **DoubleClick** – volá se, když uživatel dvakrát klikne na libovolné místo v diagramu.

   **CanDragDrop** – voláno opakovaně, když uživatel přesouvá myš při přetahování položky do diagramu. Musí pracovat rychle.

   **OnDragDrop** – volá se, když uživatel přetáhne položku do diagramu.

- První argument pro každou metodu je `IShape` , ze kterého lze získat prvek vrstvy. Příklad:

  ```
  public void OnDragDrop(IShape target, IDataObject data)
  {
      ILayerElement element = target.GetLayerElement();
      if (element is ILayer)
      {
          // ...
      }
  }
  ```

- Obslužné rutiny pro některé typy přetažených položek jsou již definovány. Uživatel může například přetáhnout položky z Průzkumník řešení do diagramu vrstev. Pro tyto typy položek nelze definovat obslužnou rutinu přetáhnutí. V těchto případech vaše `DragDrop` metody nebudou vyvolány.

  Další informace o tom, jak dekódovat jiné položky při jejich přetažení do diagramu, naleznete v tématu [definice obslužné rutiny gesta v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="see-also"></a>Viz také
 [Navigace a aktualizace modelů vrstev v programovém kódu](../modeling/navigate-and-update-layer-models-in-program-code.md) [Přidání vlastní ověření architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md) [Definování a instalace rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md)
