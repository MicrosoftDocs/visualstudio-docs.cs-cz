---
title: Navigace a aktualizace modelů vrstev v programovém kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 88ab52f1b06e6a2da94d17225bdb26ecec358a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668576"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Procházení a aktualizace modelů vrstev v programovém kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje prvky a vztahy v modelech vrstev, které můžete procházet a aktualizovat pomocí kódu programu. Další informace o diagramech vrstev z pohledu uživatele naleznete v tématu [diagramy vrstev: Reference](../modeling/layer-diagrams-reference.md) a [diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md).

 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer`Model popsaný v tomto tématu je fasáda na obecnější <xref:Microsoft.VisualStudio.GraphModel> modelu. Při psaní [příkazu nabídky nebo rozšíření gesta](../modeling/add-commands-and-gestures-to-layer-diagrams.md)použijte `Layer` model. Pokud píšete [rozšíření pro ověření vrstvy](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), je snazší použít `GraphModel` .

## <a name="transactions"></a>Transakce
 Při aktualizaci modelu zvažte uzavření změn v `ILinkedUndoTransaction` . Tím se změny seskupí do jedné transakce. Pokud některé ze změn selžou, celá transakce se vrátí zpět. Pokud uživatel tuto změnu zruší, všechny změny budou provedeny zpět dohromady.

 Další informace najdete v tématu [propojení aktualizací modelů UML pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md).

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Členství ve skupině
 ![ILayer a ILayerModel můžou obsahovat i ILayers.](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 Vrstvy ([ILayer](/previous-versions/ff644251(v=vs.140))) a model vrstvy ([ILayerModel](/previous-versions/ff643069(v=vs.140))) můžou obsahovat komentáře a vrstvy.

 Vrstva ( `ILayer` ) může být obsažena v modelu vrstvy ( `ILayerModel` ) nebo může být vnořena v rámci jiné `ILayer` .

 Chcete-li vytvořit komentář nebo vrstvu, použijte metody vytváření v příslušném kontejneru.

## <a name="dependency-links"></a>Odkazy na závislosti
 Odkaz na závislost je reprezentován objektem. Dá se navigovat v obou směrech:

 ![ILayerDependencyLink spojuje dvě ILayers.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 Chcete-li vytvořit odkaz na závislost, zavolejte `source.CreateDependencyLink(target)` .

## <a name="comments"></a>Komentáře
 Komentáře mohou být obsaženy uvnitř vrstev nebo modelu vrstvy a lze je také propojit s libovolným prvkem vrstvy:

 ![Komentáře lze připojit k jakémukoli elementu vrstvy.](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 Komentář lze propojit s libovolným počtem prvků, včetně žádné.

 Chcete-li získat komentáře, které jsou připojeny k elementu vrstvy, použijte:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> `Comments`Vlastnost `ILayer` získá komentáře obsažené v `ILayer` . Nezíská komentáře, které jsou s ním spojeny.

 Vytvořte komentář vyvoláním `CreateComment()` na odpovídajícím kontejneru.

 Vytvořte odkaz pomocí `CreateLink()` komentáře.

## <a name="layer-elements"></a>Prvky vrstvy
 Všechny typy elementů, které mohou být obsaženy v modelu, jsou prvky vrstvy:

 ![Obsah diagramu vrstev je ILayerElements.](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>Vlastnosti
 Každý `ILayerElement` má řetězcový slovník s názvem `Properties` . Pomocí tohoto slovníku můžete připojit libovolné informace k libovolnému elementu vrstvy.

## <a name="artifact-references"></a>Odkazy na artefakty
 Odkaz na artefakt ([ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))) představuje propojení mezi vrstvou a položkou projektu, jako je například soubor, třída nebo složka. Uživatel vytvoří artefakty, když vytvoří vrstvu nebo k ní přidáte přetažením položek z Průzkumník řešení, Zobrazení tříd nebo Prohlížeč objektů do diagramu vrstev. Libovolný počet odkazů na artefakty lze propojit s vrstvou.

 Každý řádek v Průzkumníkovi vrstev zobrazuje odkaz na artefakt. Další informace naleznete v tématu [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md).

 Hlavní typy a metody, které se týkají odkazů na artefakty, jsou následující:

 [ILayerArtifactReference](/previous-versions/ff644536(v=vs.140)). Vlastnost Categories označuje, jaký typ artefaktu je odkazováno, jako je například třída, spustitelný soubor nebo sestavení. Kategorie určují, jak identifikátor identifikuje cílový artefakt.

 [ArtifactReferenceExtensions. CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140)) vytvoří odkaz artefaktu z <xref:EnvDTE.Project> nebo <xref:EnvDTE.ProjectItem> . Toto je asynchronní operace. Proto obvykle zadáte zpětné volání, které je voláno po dokončení vytváření.

 Odkazy na artefakty vrstev by neměly být zaměňovány s artefakty v diagramech případů použití.

## <a name="shapes-and-diagrams"></a>Tvary a diagramy
 Dva objekty slouží k reprezentaci každého elementu v modelu vrstvy: `ILayerElement` a a [IShape](/previous-versions/ee806673(v=vs.140)). `IShape`Představuje umístění a velikost obrazce v diagramu. V modelech vrstev má každý `ILayerElement` z nich jednu `IShape` a každý `IShape` v diagramu vrstev má jednu `ILayerElement` . `IShape` se používá také pro modely UML. Proto ne každý `IShape` má element vrstvy.

 Stejným způsobem se `ILayerModel` zobrazí na jednom [IDiagram](/previous-versions/ee789658(v=vs.140)).

 V kódu vlastního obslužné rutiny příkazu nebo gesta můžete získat aktuální diagram a aktuální výběr obrazců z `DiagramContext` importu:

```
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

 ![Jednotlivé ILayerElementy prezentují IShape.](../modeling/media/layerapi-shapes.png)

 [IShape](/previous-versions/ee806673(v=vs.140)) a [IDiagram](/previous-versions/ee789658(v=vs.140)) se používají také k zobrazení modelů UML. Další informace najdete v tématu [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="see-also"></a>Viz také

- [Přidávání příkazů a gest do diagramů vrstev](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Přidání ověřování vlastní architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Přidání vlastních vlastností do diagramů vrstev](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)
- [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)
