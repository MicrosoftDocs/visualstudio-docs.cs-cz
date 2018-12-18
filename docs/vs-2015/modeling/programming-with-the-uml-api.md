---
title: Programování s rozhraním API UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d5670b0c0806d59119e1a1af87bae5642255c5a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793175"
---
# <a name="programming-with-the-uml-api"></a>Programování s rozhraním API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML rozhraní API sady Visual Studio umožňuje napsat kód k vytvoření, čtení a aktualizaci modelů a diagramů UML. Pokud chcete zobrazit, které verze sady Visual Studio podporují modelech UML, naleznete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Kromě rozhraní API referenčních stránkách následující témata popisují rozhraní API.  
  
|Téma|Vzorové typy a metody jsou popsány|Funkce popsané|  
|-----------|-----------------------------------------|------------------------|  
|[Procházení vztahů pomocí rozhraní API UML](../modeling/navigate-relationships-with-the-uml-api.md)|Prvky UML a jejich vlastnosti a asociace. Například IElement a jeho potomci, včetně: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage|V sadě Visual Studio, modely UML odpovídají specifikaci verze 2.1.2, kterou lze získat [stránky prostředků UML](http://go.microsoft.com/fwlink/?LinkId=160796). Každý typ je rozhraní, který má stejný název jako typ UML, s předponou "I".|  
|[Vytváření elementů a vztahů v modelech UML](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Každý typ elementu má metody pro vytváření podřízených.|  
|[Zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md)|IShape IDiagram<br /><br /> IShape.Move()|Každý prvek v modelu může být reprezentován jako tvar v diagramu. V některých případech můžete vytvořit nové obrazce pro každý objekt. Můžete přesunout, změnit velikost, barvu a sbalit nebo rozbalit tyto obrazce.|  
|[Procházení modelu UML](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|Store Model uložen model.<br /><br /> Kontext diagramu umožňuje přístup k aktuálnímu diagramu a úložišti.|  
|[Propojení aktualizací modelu UML pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Je možné propojit řadu změn do jedné transakce.|  
|[Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Funkci diagramu můžete rozšířit definováním příkazů vyvolaných poklepáním a přetažením do diagramu.|  
|[Definování omezení ověřování pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)|Parametr ValidationContext|Můžete definovat pravidla, která vám pomohou Ujistěte se, že model odpovídá zadaným omezením ověření.|  
|[Získávání elementů modelu UML z objektu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|IElement IShape|Když je prvek přetažen z Průzkumníka modelů UML nebo diagramu UML do jiného diagramu nebo aplikace, je serializován jako objekt IDataObject.|  
|[Úpravy sekvenčních diagramů UML pomocí rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|Vytváření a aktualizace diagramu interakce se mírně liší od práce s jinými typy diagramů.|  
|[Rozšíření diagramů vrstev](../modeling/extend-layer-diagrams.md)|ILayer ILayerDiagram|Můžete napsat kód pro vytváření a úpravy diagramů vrstev a také ověřit kód programu proti nim.|  
  
## <a name="about-the-implementation"></a>O implementaci  
 Nástroje pro modelování UML jsou postaveny na [!INCLUDE[dsl](../includes/dsl-md.md)]. Každý balíček a každý diagram je reprezentován [!INCLUDE[dsl](../includes/dsl-md.md)] modelu a kolekce pravidel a dalších metod udržuje konzistenci mezi nimi.  
  
 Typy z této platformy jsou viditelné v některých sestaveních, na která odkazujete pro zápis rozšíření UML. I když můžete provést rozšíření nástroje UML přístupem k [!INCLUDE[dsl](../includes/dsl-md.md)] rozhraní API, následující aspekty byste měli mít na paměti:  
  
-   Můžete zjistit, že některé zdánlivě jednoduché změny zavedou nekonzistence a neočekávané důsledky.  
  
-   Implementace může v budoucnu, změnit tak, aby provedené pomocí [!INCLUDE[dsl](../includes/dsl-md.md)] rozhraní API už nemusí fungovat.  
  
## <a name="the-api-assemblies"></a>Sestavení rozhraní API  
 Tato tabulka shrnuje sestavení, která poskytují rozšíření pro nástroje UML a obory názvů, které jsou vhodné pro použití.  
  
|Assembly|Jmenné prostory|Poskytuje přístup k:|  
|--------------|----------------|-------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces|(Vše)|Typy UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml>|[Metody vytváření](../modeling/create-elements-and-relationships-in-uml-models.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation>|[Diagramy a tvary](../modeling/display-a-uml-model-on-diagrams.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility>|[Projekt modelování](../modeling/read-a-uml-model-in-program-code.md)|  
|Microsoft.VisualStudio.Modeling.Sdk.[version]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Rozšíření příkazu nabídky](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Propojené transakce zpět](../modeling/link-uml-model-updates-by-using-transactions.md).|  
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Ověřování](../modeling/define-validation-constraints-for-uml-models.md)|  
||(jiné obory názvů)|Doporučeno pouze pro pokročilé uživatele.|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Obslužné rutiny gesta](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|  
||(jiné obory názvů)|Doporučeno pouze pro pokročilé uživatele.|  
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|<xref:Microsoft.VisualStudio.TeamFoundation.WorkItemTracking>|[Odkazy na pracovní položky](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.WorkItemTracking.Client|<xref:Microsoft.TeamFoundation.WorkItemTracking.Client>|[Pracovní položky a jejich polí](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.Client|<xref:Microsoft.TeamFoundation.Client>|[Pracovní položky a jejich polí](../modeling/define-a-work-item-link-handler.md).|  
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Export a Import součástí MEF](../modeling/define-and-install-a-modeling-extension.md)|  
|System.Linq|<xref:System.Linq>|[Snadná manipulace s kolekcemi, zejména při práci s relací](../modeling/navigate-relationships-with-the-uml-api.md).|  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Referenční dokumentace k rozhraní API pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md)



