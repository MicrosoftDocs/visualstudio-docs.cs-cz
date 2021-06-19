---
title: Přidávání příkazů a gest do diagramů závislostí
description: Zjistěte, jak v diagramech závislostí v diagramech závislostí definovat příkazy nabídky a obslužné rutiny gest po kliknutí pravým Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43d6cf5410aed3d79814d5304705a424bcc71e89
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387447"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Přidávání příkazů a gest do diagramů závislostí

Příkazy nabídky po kliknutí pravým tlačítkem a obslužné rutiny gest můžete definovat v diagramech závislostí v Visual Studio. Tato rozšíření můžete zabalit do Visual Studio (VSIX), které můžete distribuovat ostatním Visual Studio uživatelům.

Pokud chcete, můžete definovat několik obslužných rutin příkazů a gest Visual Studio projektu. Několik takových projektů můžete také zkombinovat do jednoho VSIX. Můžete například definovat jeden soubor VSIX, který obsahuje příkazy vrstvy, a jazyk specifický pro doménu.

> [!NOTE]
> Můžete také přizpůsobit ověřování architektury, ve kterém se zdrojový kód uživatelů porovnává s diagramy závislostí. Ověřování architektury byste měli definovat v samostatném Visual Studio projektu. Můžete ho přidat do stejného VSIX jako ostatní rozšíření. Další informace najdete v tématu [Přidání vlastního ověření architektury do diagramů závislostí.](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

## <a name="requirements"></a>Požadavky

Viz [Požadavky.](../modeling/extend-layer-diagrams.md#requirements)

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>Definování příkazu nebo gesta v novém VSIX

Nejrychlejší metodou vytvoření rozšíření je použití šablony projektu. Tím se kód a manifest VSIX umístí do stejného projektu.

1. Vytvořte nový projekt **rozšíření příkazů návrháře vrstev nebo** rozšíření **gest návrháře** vrstev.

   Šablona vytvoří projekt, který obsahuje malý funkční příklad.

2. Pokud chcete rozšíření otestovat, stiskněte **Ctrl** + **F5** nebo **F5**.

    Spustí se experimentální Visual Studio instance. V tomto případě vytvořte diagram závislostí. V tomto diagramu by měl fungovat váš příkaz nebo rozšíření gest.

3. Zavřete experimentální instanci a upravte vzorový kód.

4. Do stejného projektu můžete přidat další obslužné rutiny příkazů nebo gest. Další informace najdete v jedné z následujících částí:

    [Definování příkazu nabídky](#command)

    [Definování obslužné rutiny gest](#gesture)

::: moniker range="vs-2017"

5. Pokud chcete rozšíření nainstalovat do hlavní instance Visual Studio nebo na jiný počítač, vyhledejte *soubor .vsix* v *adresáři bin.* Zkopírujte ho do počítače, do kterého ho chcete nainstalovat, a dvakrát na něj klikněte. Pokud ho chcete odinstalovat, **zvolte Rozšíření a aktualizace** v **nabídce** Nástroje.

::: moniker-end

::: moniker range=">=vs-2019"

5. Pokud chcete rozšíření nainstalovat do hlavní instance Visual Studio nebo na jiný počítač, vyhledejte *soubor .vsix* v *adresáři bin.* Zkopírujte ho do počítače, do kterého ho chcete nainstalovat, a dvakrát na něj klikněte. Pokud ho chcete odinstalovat, **zvolte Spravovat** rozšíření **v nabídce** Rozšíření.

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>Přidání příkazu nebo gesta do samostatného VSIX

Pokud chcete vytvořit jeden VSIX, který obsahuje příkazy, validátory vrstev a další rozšíření, doporučujeme vytvořit jeden projekt, který definuje VSIX, a samostatné projekty pro obslužné rutiny.

1. Vytvořte nový **projekt knihovny** tříd. Tento projekt bude obsahovat třídy obslužných rutin příkazů nebo gest.

   > [!NOTE]
   > V jedné knihovně tříd můžete definovat více než jeden příkaz nebo třídu obslužné rutiny gest, ale třídy ověřování vrstev byste měli definovat v samostatné knihovně tříd.

2. Přidejte nebo vytvořte projekt VSIX ve vašem řešení. Projekt VSIX obsahuje soubor s názvem **source.extension.vsixmanifest**.

3. V Průzkumník řešení klikněte pravým tlačítkem na projekt VSIX **a** zvolte Nastavit **jako spouštěný projekt.**

4. V **souboru source.extension.vsixmanifest** přidejte v části **Assets**(Prostředky) projekt obslužné rutiny příkazů nebo gest jako komponentu MEF.

    1. Na **kartě Assets**(Prostředky) zvolte **New (Nový).**

    2. V **okně** Typ vyberte **Microsoft.VisualStudio.MefComponent.**

    3. V **části Source**(Zdroj) vyberte Project in current **solution** (Projekt v aktuálním řešení) a vyberte název projektu obslužné rutiny příkazu nebo gest.

    4. Soubor uložte.

5. Vraťte se do projektu obslužné rutiny příkazů nebo gest a přidejte následující odkazy na projekt:

   |**Odkaz**|**Co vám to umožňuje dělat**|
   |-|-|
   |Program Files\Microsoft Visual Studio [verze]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Vytváření a úpravy vrstev|
   |Microsoft.VisualStudio.Uml.Interfaces|Vytváření a úpravy vrstev|
   |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Úpravy obrazců v diagramech|
   |System.ComponentModel.Composition|Definování komponent pomocí Managed Extensibility Framework (MEF)|
   |Microsoft.VisualStudio.Modeling.Sdk. [version]|Definování rozšíření modelování|
   |Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [version]|Aktualizace obrazců a diagramů|

6. Upravte soubor třídy v projektu knihovny tříd jazyka C# tak, aby obsahoval kód pro vaši příponu. Další informace najdete v jedné z následujících částí:

     [Definování příkazu nabídky](#command)

     [Definování obslužné rutiny gest](#gesture)

7. Pokud chcete funkci otestovat, stiskněte **Ctrl** + **F5** nebo **F5.**

   Otevře se experimentální Visual Studio aplikace. V tomto případě vytvořte nebo otevřete diagram závislostí.

8. Pokud chcete nainstalovat VSIX v hlavní instanci Visual Studio nebo na jiném počítači, vyhledejte **soubor .vsix** v adresáři **bin** projektu VSIX. Zkopírujte ho do počítače, do kterého chcete nainstalovat VSIX. Poklikejte na soubor VSIX v Průzkumník souborů.

## <a name="defining-a-menu-command"></a><a name="command"></a> Definování příkazu nabídky

Do existujícího projektu gest nebo příkazu můžete přidat další definice příkazů nabídky. Každý příkaz je definován třídou, která má následující charakteristiky:

- Třída je deklarována takto:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- Obor názvů a název třídy nejsou důležité.

- Implementují se `ICommandExtension` tyto metody:

  - `string Text {get;}` – Popisek, který se zobrazí v nabídce.

  - `void QueryStatus(IMenuCommand command)` – volá se, když uživatel klikne pravým tlačítkem na diagram a určí, jestli má být příkaz viditelný a povolený pro aktuální výběr uživatele.

  - `void Execute(IMenuCommand command)` – volá se, když uživatel vybere příkaz .

- Pokud chcete určit aktuální výběr, můžete importovat `IDiagramContext` :

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

Pokud chcete přidat nový příkaz, vytvořte nový soubor kódu, který obsahuje následující ukázku. Pak ho otestujte a upravte.

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

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> Definování obslužné rutiny gest

Obslužná rutina gesta odpoví, když uživatel přetáhne položky do diagramu závislostí a když uživatel dvakrát klikne kamkoli do diagramu.

Do existujícího projektu obslužné rutiny příkazů nebo gest VSIX můžete přidat soubor kódu, který definuje obslužnou rutinu gest:

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

Všimněte si následujících bodů o obslužných rutinách gest:

- Členy jsou `IGestureExtension` následující:

     **OnDoubleClick** – volá se, když uživatel dvakrát klikne na libovolné místo v diagramu.

     **CanDragDrop** – opakovaně se volá, když uživatel posouvá myš při přetažení položky do diagramu. Musí rychle fungovat.

     **OnDragDrop** – volá se, když uživatel zahodí položku do diagramu.

- Prvním argumentem každé metody je `IShape` , ze kterého můžete získat prvek vrstvy. Příklad:

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

- Obslužné rutiny pro některé typy přetáhlých položek jsou už definované. Uživatel může například přetáhnout položky z Průzkumník řešení do diagramu závislostí. Pro tyto typy položek nelze definovat obslužnou rutinu přetažení. V těchto případech nebudou `DragDrop` vaše metody vyvolány.

## <a name="see-also"></a>Viz také

- [Přidání vlastního ověřování architektury do diagramů závislostí](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
