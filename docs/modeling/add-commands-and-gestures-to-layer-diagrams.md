---
title: Přidávání příkazů a gest do diagramů závislostí
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ff23e07bd6e81b11d94a8256c33b57b4b0c558c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531388"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Přidávání příkazů a gest do diagramů závislostí

V diagramech závislostí v aplikaci Visual Studio můžete definovat příkazy nabídky na základě pravého tlačítka a obslužné rutiny gesta. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio (VSIX), které můžete distribuovat dalším uživatelům aplikace Visual Studio.

Pokud chcete, můžete definovat několik obslužných rutin příkazů a gest v jednom projektu sady Visual Studio. Můžete také zkombinovat několik takových projektů do jednoho VSIX. Můžete například definovat jeden VSIX, který obsahuje příkazy vrstev a jazyk specifický pro doménu.

> [!NOTE]
> Můžete také přizpůsobit ověření architektury, ve kterém je zdrojový kód uživatele porovnán s diagramy závislosti. Ověřování architektury byste měli definovat v samostatném projektu sady Visual Studio. Můžete ji přidat ke stejnému VSIX jako další rozšíření. Další informace najdete v tématu [Přidání ověření vlastní architektury do diagramů závislostí](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Požadavky

Viz [požadavky](../modeling/extend-layer-diagrams.md#requirements).

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>Definování příkazu nebo gesta v novém VSIX

Nejrychlejší způsob, jak vytvořit rozšíření, je použití šablony projektu. Tím se umístí kód a manifest VSIX do stejného projektu.

1. Vytvoří nové **rozšíření příkazu návrháře vrstvy** nebo **rozšíření pro návrháře vrstvy** projektu.

   Šablona vytvoří projekt, který obsahuje malý pracovní příklad.

2. Rozšíření otestujete stisknutím **kláves CTRL** + **F5** nebo **F5**.

    Spustí se experimentální instance sady Visual Studio. V této instanci vytvořte diagram závislostí. Vaše příkazy nebo rozšíření gesta by mělo fungovat v tomto diagramu.

3. Zavřete experimentální instanci a upravte vzorový kód.

4. Do stejného projektu můžete přidat další obslužné rutiny příkazu nebo gesta. Další informace naleznete v jedné z následujících částí:

    [Definování příkazu nabídky](#command)

    [Definování obslužné rutiny gesta](#gesture)

::: moniker range="vs-2017"

5. Chcete-li nainstalovat rozšíření v hlavní instanci aplikace Visual Studio nebo v jiném počítači, vyhledejte soubor *. vsix* v adresáři *bin* . Zkopírujte ho do počítače, kam ho chcete nainstalovat, a dvakrát na něj klikněte. Pokud ho chcete odinstalovat, v nabídce **nástroje** vyberte **rozšíření a aktualizace** .

::: moniker-end

::: moniker range=">=vs-2019"

5. Chcete-li nainstalovat rozšíření v hlavní instanci aplikace Visual Studio nebo v jiném počítači, vyhledejte soubor *. vsix* v adresáři *bin* . Zkopírujte ho do počítače, kam ho chcete nainstalovat, a dvakrát na něj klikněte. Pokud ho chcete odinstalovat, v nabídce **rozšíření** vyberte **Spravovat rozšíření** .

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>Přidání příkazu nebo gesta do samostatného souboru VSIX

Pokud chcete vytvořit jeden VSIX, který obsahuje příkazy, validátory vrstev a další rozšíření, doporučujeme vytvořit jeden projekt k definování VSIX a samostatné projekty pro obslužné rutiny.

1. Vytvořte nový projekt **knihovny tříd** . Tento projekt bude obsahovat třídy obslužné rutiny příkazu nebo gesta.

   > [!NOTE]
   > Můžete definovat více než jednu třídu příkazu nebo obslužné rutiny gesta v jedné knihovně tříd, ale měli byste definovat třídy ověřování vrstvy v samostatné knihovně tříd.

2. Přidejte nebo vytvořte projekt VSIX ve vašem řešení. Projekt VSIX obsahuje soubor s názvem **source. extension. vsixmanifest**.

3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt VSIX a vyberte **nastavit jako spouštěný projekt**.

4. V části **source. extension. vsixmanifest**v části **assety**přidejte projekt obslužné rutiny příkazu nebo gesta jako komponentu MEF.

    1. Na kartě **assets**. klikněte na tlačítko **Nový**.

    2. V **typu**vyberte **Microsoft. VisualStudio. MefComponent**.

    3. V části **zdroj**vyberte **projekt v aktuálním řešení** a vyberte název projektu obslužné rutiny příkazu nebo gesta.

    4. Uložte soubor.

5. Vraťte se do projektu obslužné rutiny příkazu nebo gesta a přidejte následující odkazy projektu:

   |**Odkaz**|**Co vám to umožňuje**|
   |-|-|
   |Program Files\Microsoft Visual Studio [verze] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Vytváření a úpravy vrstev|
   |Microsoft. VisualStudio. Uml. Interfaces|Vytváření a úpravy vrstev|
   |Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost|Úprava tvarů v diagramech|
   |System. ComponentModel. složení|Definovat komponenty pomocí Managed Extensibility Framework (MEF)|
   |Microsoft. VisualStudio. Modeling. SDK. znění|Definování rozšíření modelování|
   |Microsoft. VisualStudio. Modeling. SDK. Diagrams. znění|Aktualizovat obrazce a diagramy|

6. Upravte soubor třídy v projektu knihovny tříd jazyka C# tak, aby obsahoval kód pro vaše rozšíření. Další informace naleznete v jedné z následujících částí:

     [Definování příkazu nabídky](#command)

     [Definování obslužné rutiny gesta](#gesture)

7. Pokud chcete funkci otestovat, stiskněte klávesy **CTRL** + **F5** nebo **F5**.

   Otevře se experimentální instance aplikace Visual Studio. V této instanci vytvořte nebo otevřete diagram závislosti.

8. Chcete-li nainstalovat VSIX v hlavní instanci aplikace Visual Studio nebo v jiném počítači, vyhledejte soubor **. vsix** v adresáři **bin** projektu VSIX. Zkopírujte jej do počítače, kam chcete nainstalovat VSIX. Dvakrát klikněte na soubor VSIX v Průzkumníkovi souborů.

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

Chcete-li přidat nový příkaz, vytvořte nový soubor kódu, který obsahuje následující ukázku. Pak ho otestujte a upravte.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
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

Obslužná rutina gesta reaguje, když uživatel přetáhne položky do diagramu závislostí a když uživatel dvakrát klikne na libovolné místo v diagramu.

Do stávajícího projektu VSIX obslužné rutiny příkazu nebo gesta můžete přidat soubor kódu, který definuje obslužnou rutinu gesta:

```csharp
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

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

- Obslužné rutiny pro některé typy přetažených položek jsou již definovány. Uživatel může třeba přetáhnout položky z Průzkumník řešení do diagramu závislostí. Pro tyto typy položek nelze definovat obslužnou rutinu přetáhnutí. V těchto případech vaše `DragDrop` metody nebudou vyvolány.

## <a name="see-also"></a>Viz také

- [Přidání vlastního ověřování architektury do diagramů závislostí](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
