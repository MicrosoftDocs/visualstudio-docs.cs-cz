---
title: Procházení a aktualizace modelů vrstev v programovém kódu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8ca10b8504dc4383ad6251e3819c14b7102d32d3
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566736"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Procházení a aktualizace modelů vrstev v programovém kódu

Tento článek popisuje prvky a vztahy v modelech vrstvy, které můžete přejít a aktualizovat pomocí kódu programu. Další informace o diagramů závislostí z pohledu uživatele najdete v tématu [diagramy závislostí: referenční](../modeling/layer-diagrams-reference.md) a [diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md).

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Modelu popsaného v tomto tématu je fasáda na obecnějšího <xref:Microsoft.VisualStudio.GraphModel> modelu. Při psaní [rozšíření příkazu nebo gesta nabídky](../modeling/add-commands-and-gestures-to-layer-diagrams.md), použijte `Layer` modelu. Pokud píšete [rozšíření ověření vrstvy](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), je jednodušší použít `GraphModel`.

## <a name="transactions"></a>Transakce

Při aktualizaci modelu, vezměte v úvahu změny v nadřazeném `ILinkedUndoTransaction`, která seskupuje vaše změny do jedné transakce. Pokud některý z změny selže, celá transakce vrácena zpět. Pokud uživatel vrátí zpět změny, jsou všechny změny vrátit zpět společně.

```csharp
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Členství ve skupině

![ILayer a ILayerModel může obsahovat i ILayers.](../modeling/media/layerapi_containment.png)

Vrstvy (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) a vrstva modelu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) může obsahovat komentáře a vrstvy.

Vrstva (`ILayer`) mohou být obsaženy v modelu vrstvy (`ILayerModel`) nebo může být vnořena do jiné `ILayer`.

K vytvoření komentáře nebo vrstvu, používají metody vytvoření odpovídajícího kontejneru.

## <a name="dependency-links"></a>Odkazy závislostí

Objekt je reprezentován odkazu závislostí. To lze procházet v obou směrech:

![ILayerDependencyLink připojí dva ILayers.](../modeling/media/layerapi_dependency.png)

Chcete-li vytvořit odkaz závislosti, zavolejte `source.CreateDependencyLink(target)`.

## <a name="comments"></a>Komentáře

Komentáře mohou být obsaženy v rámci vrstvy nebo model vrstvy a také může být propojený libovolného prvku vrstvy:

![Komentáře lze připojit k libovolnému prvku vrstvy.](../modeling/media/layerapi_comments.png)

Komentář může být propojený libovolný počet prvků, včetně none.

Chcete-li získat poznámky, které jsou připojeny k elementu vrstvy, použijte:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));
```

> [!CAUTION]
> `Comments` Vlastnost `ILayer` získá komentáře, které jsou obsaženy v rámci `ILayer`. Poznámky, které jsou propojeny k němu nedostane.

Vytvořit poznámku voláním `CreateComment()` na příslušný kontejner.

Vytvoření odkazu pomocí `CreateLink()` na komentář.

## <a name="layer-elements"></a>Elementy vrstvy

Všechny typy elementu, který může být součástí modelu jsou elementy vrstvy:

![obsah diagram závislostí je ILayerElements.](../modeling/media/layerapi_layerelements.png)

## <a name="properties"></a>Vlastnosti

Každý `ILayerElement` s řetězci slovník s názvem `Properties`. Vám pomůže tento slovník připojte libovolné informace do libovolného prvku vrstvy.

## <a name="artifact-references"></a>Odkazy na artefaktu

Odkaz na artefaktu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) představuje propojení mezi vrstvou a položky projektu, například soubor, třídy nebo složky. Uživatel vytvoří artefakty při vytvoření vrstvy nebo k němu přidat přetažením položek z Průzkumníka řešení, zobrazení tříd nebo prohlížeči objektů na diagram závislostí. Libovolný počet artefaktů odkazy může být propojeny s vrstvou.

Každý řádek v Průzkumníku vrstev zobrazí odkaz na artefakt. Další informace najdete v tématu [vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md).

Hlavní typy a metody s odkazy na artefaktů jsou následující:

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Vlastnost kategorie určuje, jaký druh artefaktu je odkazováno jako třída, spustitelný soubor nebo sestavení. Vlastnost kategorie určuje způsobu, jakým identifikuje identifikátor artefaktu cíl.

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> Vytvoří odkaz na artefaktů z <xref:EnvDTE.Project> nebo <xref:EnvDTE.ProjectItem>. Toto je asynchronní operace. Proto se obvykle poskytují zpětné volání, která je volána po dokončení vytváření.

Odkazy artefaktů vrstvy se liší na artefakty v diagramech případů použití.

## <a name="shapes-and-diagrams"></a>Tvary a diagramy

Dva objekty se používají k vyjádření každý prvek v modelu vrstev: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>a <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` Představuje pozici a velikost obrazce v diagramu. V modelů vrstvy každý `ILayerElement` má jeden `IShape`a každý `IShape` na závislost diagram má jeden `ILayerElement`. `IShape` slouží také pro modely UML. Proto nepodporují `IShape` má prvek vrstvy.

Stejným způsobem <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> se zobrazí na jednom <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.

V kódu vlastního příkazu nebo obslužné rutiny gesta, můžete získat aktuální diagram a tvarů z aktuálního výběru `DiagramContext` importovat:

```csharp
public class ... {
[Import]
    public IDiagramContext DiagramContext { get; set; }
...
public void ... (...)
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;
  ILayerModel model = diagram.GetLayerModel();
  if (model != null)
  { foreach (ILayer layer in model.Layers) { ... }}
  foreach (IShape selected in diagram.SelectedShapes)
  { ILayerElement element = selected.GetLayerElement();
    if (element != null) ... }}
```

![Každý ILayerElement je předkládán IShape.](../modeling/media/layerapi_shapes.png)

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> a <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> slouží také k zobrazení modelů UML.

## <a name="see-also"></a>Viz také

- [Přidávání příkazů a gest do diagramů závislostí](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Přidání vlastního ověřování architektury do diagramů závislostí](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Přidání vlastních vlastností do diagramů závislostí](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)
