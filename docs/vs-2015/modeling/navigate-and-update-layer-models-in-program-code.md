---
title: Procházení a aktualizace modelů vrstev v programovém kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ec36aa78ce5ed90098587092207806444681146a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734734"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Procházení a aktualizace modelů vrstev v programovém kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje prvky a vztahy v modelech vrstvy, které můžete přejít a aktualizovat pomocí kódu programu. Další informace o diagramech vrstev z pohledu uživatele najdete v tématu [diagramy vrstev: referenční](../modeling/layer-diagrams-reference.md) a [diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md).  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Modelu popsaného v tomto tématu je fasáda na obecnějšího <xref:Microsoft.VisualStudio.GraphModel> modelu. Při psaní [rozšíření příkazu nebo gesta nabídky](../modeling/add-commands-and-gestures-to-layer-diagrams.md), použijte `Layer` modelu. Pokud píšete [rozšíření ověření vrstvy](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), je jednodušší použít `GraphModel`.  
  
## <a name="transactions"></a>Transakce  
 Při aktualizaci modelu, vezměte v úvahu změny v nadřazeném `ILinkedUndoTransaction`. Toto zadání seskupí provedené změny do jedné transakce. Pokud některý z změny selže, celá transakce bude vrácena zpět. Pokud uživatel vrátí zpět změny, všechny změny budou vrátit zpět společně.  
  
 Další informace najdete v tématu [UML propojení aktualizací modelů pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Členství ve skupině  
 ![ILayer a ILayerModel může obsahovat i ILayers. ](../modeling/media/layerapi-containment.png "LayerApi_Containment")  
  
 Vrstvy (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) a vrstva modelu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) může obsahovat komentáře a vrstvy.  
  
 Vrstva (`ILayer`) mohou být obsaženy v modelu vrstvy (`ILayerModel`) nebo může být vnořena do jiné `ILayer`.  
  
 K vytvoření komentáře nebo vrstvu, používají metody vytvoření odpovídajícího kontejneru.  
  
## <a name="dependency-links"></a>Odkazy závislostí  
 Objekt je reprezentován odkazu závislostí. To lze procházet v obou směrech:  
  
 ![ILayerDependencyLink připojí dva ILayers. ](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")  
  
 Chcete-li vytvořit odkaz závislosti, zavolejte `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Komentáře  
 Komentáře mohou být obsaženy v rámci vrstvy nebo model vrstvy a také může být propojený libovolného prvku vrstvy:  
  
 ![Komentáře lze připojit k libovolnému prvku vrstvy. ](../modeling/media/layerapi-comments.png "LayerApi_Comments")  
  
 Komentář může být propojený libovolný počet prvků, včetně none.  
  
 Chcete-li získat poznámky, které jsou připojeny k elementu vrstvy, použijte:  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  `Comments` Vlastnost `ILayer` získá komentáře, které jsou obsaženy v rámci `ILayer`. Poznámky, které jsou propojeny k němu nedostane.  
  
 Vytvořit poznámku vyvoláním `CreateComment()` na příslušný kontejner.  
  
 Vytvoření odkazu pomocí `CreateLink()` na komentář.  
  
## <a name="layer-elements"></a>Elementy vrstvy  
 Všechny typy elementu, který může být součástí modelu jsou elementy vrstvy:  
  
 ![Obsah diagramu vrstvy jsou ILayerElements. ](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Vlastnosti  
 Každý `ILayerElement` s řetězci slovník s názvem `Properties`. Vám pomůže tento slovník připojte libovolné informace do libovolného prvku vrstvy.  
  
## <a name="artifact-references"></a>Odkazy na artefaktu  
 Odkaz na artefaktu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) představuje propojení mezi vrstvou a položky projektu, například soubor, třídy nebo složky. Uživatel vytvoří artefakty při vytvoření vrstvy nebo k němu přidat přetažením položek z Průzkumníka řešení, zobrazení tříd nebo prohlížeči objektů do diagramu vrstvy. Libovolný počet artefaktů odkazy může být propojeny s vrstvou.  
  
 Každý řádek v Průzkumníku vrstev zobrazí odkaz na artefakt. Další informace najdete v tématu [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Hlavní typy a metody s odkazy na artefaktů jsou následující:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Vlastnost kategorie určuje, jaký druh artefaktu je odkazováno jako třída, spustitelný soubor nebo sestavení. Kategorie určuje způsobu, jakým identifikuje identifikátor artefaktu cíl.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> Vytvoří odkaz na artefaktů z <xref:EnvDTE.Project> nebo <xref:EnvDTE.ProjectItem>. Toto je asynchronní operace. Proto se obvykle poskytují zpětné volání, která je volána po vytvoření se zobrazí.  
  
 Odkazy artefaktů vrstvy neměly by být zaměňovány s artefakty v diagramech případů použití.  
  
## <a name="shapes-and-diagrams"></a>Tvary a diagramy  
 Dva objekty se používají k vyjádření každý prvek v modelu vrstev: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>a <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` Představuje pozici a velikost obrazce v diagramu. V modelů vrstvy každý `ILayerElement` má jeden `IShape`a každý `IShape` ve vrstvě diagram má jeden `ILayerElement`. `IShape` slouží také pro modely UML. Proto nepodporují `IShape` má prvek vrstvy.  
  
 Stejným způsobem <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> se zobrazí na jednom <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.  
  
 V kódu vlastního příkazu nebo obslužné rutiny gesta, můžete získat aktuální diagram a tvarů z aktuálního výběru `DiagramContext` importovat:  
  
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
  
 ![Každý ILayerElement je předkládán IShape. ](../modeling/media/layerapi-shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> a <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> slouží také k zobrazení modelů UML. Další informace najdete v tématu [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidávání příkazů a gest do diagramů vrstev](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Přidání ověřování vlastní architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Přidání vlastních vlastností do diagramů vrstev](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Diagramy vrstev: referenční dokumentace](../modeling/layer-diagrams-reference.md)   
 [Diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)   
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)



