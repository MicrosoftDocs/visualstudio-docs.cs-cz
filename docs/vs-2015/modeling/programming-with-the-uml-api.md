---
title: Programování s rozhraním API UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dcb179ae80e60654c981da8c76e9a57e6fb8ed66
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296058"
---
# <a name="programming-with-the-uml-api"></a>Programování s rozhraním API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozhraní API UML sady Visual Studio umožňuje psát kód pro vytváření, čtení a aktualizaci modelů a diagramů UML. Chcete-li zjistit, které verze aplikace Visual Studio podporují modely UML, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Kromě referenčních stránek rozhraní API popisují následující témata rozhraní API.

|Téma|Příklady popsaných typů a metod|Popsané funkce|
|-----------|-----------------------------------------|------------------------|
|[Procházení vztahů pomocí rozhraní API UML](../modeling/navigate-relationships-with-the-uml-api.md)|Prvky UML a jejich vlastnosti a přidružení. Například IElement a jeho potomci, včetně: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage|V aplikaci Visual Studio modely UML vyhovují specifikaci UML verze 2.1.2, která se dá získat na [stránce prostředků UML](https://go.microsoft.com/fwlink/?LinkId=160796). Každý typ je rozhraní, které má stejný název jako typ UML s předponou "I".|
|[Vytváření elementů a vztahů v modelech UML](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Každý typ elementu obsahuje metody pro vytváření podřízených objektů.|
|[Zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape. Move ()|Každý prvek v modelu může být reprezentován jako tvar v diagramu. V některých případech můžete vytvořit nové tvary pro každý objekt. Tyto tvary můžete přesouvat, měnit jejich velikost, měnit jejich barvy, sbalovat je nebo je rozbalit.|
|[Procházení modelu UML](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|Úložiště modelu ukládá model.<br /><br /> Kontext diagramu vám umožní přístup k aktuálnímu diagramu a obchodu.|
|[Propojení aktualizací modelu UML pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Můžete propojit řadu změn do jedné transakce.|
|[Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Funkce diagramu můžete roztáhnout tak, že definujete příkazy vyvolané dvojitým kliknutím a přetažením do diagramu.|
|[Definování omezení ověřování pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Můžete definovat ověřovací pravidla, která vám pomohou zajistit, že model odpovídá zadaným omezením.|
|[Získávání elementů modelu UML z objektu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Když je prvek přetažen z Průzkumníka modelů UML nebo diagramu UML do jiného diagramu nebo aplikace, je serializován jako IDataObject.|
|[Úpravy sekvenčních diagramů UML pomocí rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|Vytváření a aktualizace diagramu interakce se mírně liší od práce s ostatními typy diagramů.|
|[Rozšíření diagramů vrstev](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|Můžete napsat kód pro vytváření a úpravy diagramů vrstev a také pro ně ověřit kód programu.|

## <a name="about-the-implementation"></a>O implementaci
 Nástroje pro modelování UML jsou postaveny na [!INCLUDE[dsl](../includes/dsl-md.md)]. Každý balíček a jednotlivé diagramy jsou reprezentovány [!INCLUDE[dsl](../includes/dsl-md.md)]m modelem a kolekce pravidel a dalších metod udržuje konzistenci mezi nimi.

 Typy z této platformy jsou viditelné v některých sestaveních, na která odkazujete, aby bylo možné zapisovat rozšíření UML. I když můžete k nástrojům UML přistupovat pomocí rozhraní [!INCLUDE[dsl](../includes/dsl-md.md)] API, měli byste mít na paměti následující skutečnosti:

- Může se stát, že některé zjevně jednoduché změny představují nekonzistence a neočekávané účinky.

- Implementace se může v budoucnu změnit, takže změny provedené pomocí rozhraní [!INCLUDE[dsl](../includes/dsl-md.md)] API možná nebudou fungovat.

## <a name="the-api-assemblies"></a>Sestavení rozhraní API
 Tato tabulka shrnuje sestavení, která poskytují rozšiřitelnost pro nástroje UML, a obory názvů, které se doporučuje použít.

|Assembly|Jmenné prostory|Poskytuje přístup k:|
|--------------|----------------|-------------------------|
|Microsoft.VisualStudio.Uml.Interfaces|Všem|Typy UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost. UML|[Metody vytváření](../modeling/create-elements-and-relationships-in-uml-models.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation|[Diagramy a obrazce](../modeling/display-a-uml-model-on-diagrams.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility|[Projekt modelování](../modeling/read-a-uml-model-in-program-code.md)|
|Microsoft.VisualStudio.Modeling.Sdk.[version]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Přípona příkazu nabídky](../modeling/define-a-menu-command-on-a-modeling-diagram.md)<br /><br /> [Propojené transakce vrácení zpět](../modeling/link-uml-model-updates-by-using-transactions.md).|
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Ověřování](../modeling/define-validation-constraints-for-uml-models.md)|
||(jiné obory názvů)|Doporučuje se jenom pro pokročilé použití.|
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Obslužné rutiny gesta](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|
||(jiné obory názvů)|Doporučuje se jenom pro pokročilé použití.|
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|[Odkazy na pracovní položky](../modeling/define-a-work-item-link-handler.md).|
|Microsoft.TeamFoundation.WorkItemTracking.Client|Microsoft.TeamFoundation.WorkItemTracking.Client|[Pracovní položky a jejich pole](../modeling/define-a-work-item-link-handler.md).|
|Microsoft.TeamFoundation.Client|Microsoft.TeamFoundation.Client|[Pracovní položky a jejich pole](../modeling/define-a-work-item-link-handler.md).|
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Export a import pro komponenty MEF](../modeling/define-and-install-a-modeling-extension.md)|
|System. Linq|<xref:System.Linq>|[Snadná manipulace s kolekcemi, zejména při práci se vztahy](../modeling/navigate-relationships-with-the-uml-api.md).|

## <a name="see-also"></a>Viz také
 Rozšíření referencí k rozhraní API [modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
