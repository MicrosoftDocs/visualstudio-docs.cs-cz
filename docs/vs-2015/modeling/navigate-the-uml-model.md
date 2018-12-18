---
title: Procházení modelu UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6f77e72c55c0984f66a6884b0582716e5529abd0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727773"
---
# <a name="navigate-the-uml-model"></a>Procházení modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma uvádí hlavní typy modelu UML.  
  
## <a name="the-model-elements-model-and-model-store"></a>Prvky modelu, Model a Model Store  
 Typy definované v sestavení **Microsoft.VisualStudio.Uml.Interfaces.dll** odpovídají typům definovaným v [specifikaci UML, verze 2.1.2](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).  
  
 Typy ve specifikaci UML jsou realizovány jako rozhraní v sadě Visual Studio. Písmeno "I" je přidáno před název každého typu. Příklad: <xref:Microsoft.VisualStudio.Uml.Classes.IElement>, <xref:Microsoft.VisualStudio.Uml.Classes.IClass>, <xref:Microsoft.VisualStudio.Uml.Interactions.IInteraction>, <xref:Microsoft.VisualStudio.Uml.Classes.IOperation>.  
  
 Všechny typy s výjimkou IElement dědí vlastnosti z jednoho nebo více nadtypů.  
  
-   Shrnutí typů modelu viz [typy prvků modelu UML](../modeling/uml-model-element-types.md).  
  
-   Úplné podrobnosti o rozhraní API najdete v části [Reference k rozhraní API pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  
  
### <a name="relationships"></a>Relace  
 Vlastnosti a vztahy, které jsou definovány ve specifikaci UML jsou implementovány jako vlastnosti rozhraní .NET.  
  
 Jsou většinu vztahů lze procházet v obou směrech. Vztah odpovídá dvojici vlastností s jednou vlastností pro typ na každém konci. Například vlastnosti `IElement.Owner` a `IElement.OwnedElements` představují dva konce vztahu. Proto tento výraz bude vždy vyhodnocen na hodnotu true:  
  
 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`  
  
 Mnoho vztahů, například IAssociation, jsou také reprezentované objektem, který může mít svůj vlastní vlastnosti.  
  
 Pokud odstraníte z modelu prvek, každá relace, ve kterém se účastní se odstraní automaticky a vlastnost na druhém konci je aktualizována.  
  
 Pokud specifikace UML přiřadí vlastnosti násobnost 0.. 1, může mít hodnotu `null`. Násobnost s maximem větším než 1 znamená, že má vlastnost .NET typ: `IEnumerable<` *typ*`>`.  
  
 Další informace o překračování vztahů naleznete v tématu [procházení vztahů pomocí rozhraní API UML](../modeling/navigate-relationships-with-the-uml-api.md).  
  
### <a name="the-ownership-tree"></a>Strom vlastnictví  
 Model obsahuje strom <xref:Microsoft.VisualStudio.Uml.Classes.IElement> objekty. Každý prvek má vlastnosti `OwnedElements` a `Owner`.  
  
 Ve většině případů cíle `Owner` a `OwnedElements` vlastnosti jsou také odkazovány jinými vlastnostmi, které mají specifičtější názvy. Například každé operace UML je vlastněná třídou UML. Proto <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> má vlastnost s názvem <xref:Microsoft.VisualStudio.Uml.Classes.IOperation.Class%2A>a v každé <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> objektu, `Class == Owner`.  
  
 Nejvyšší prvek stromu, který nemá vlastníka, je <xref:Microsoft.VisualStudio.Uml.AuxiliaryConstructs.IModel>. IModel je součástí <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, v níž je <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore.Root%2A>.  
  
 Každý prvek modelu je vytvořen s vlastníkem. Další informace najdete v tématu [vytváření elementů a vztahů v modelech UML](../modeling/create-elements-and-relationships-in-uml-models.md).  
  
 ![Diagram tříd: Model, Diagram, tvar a Element](../modeling/media/uml-mm1.png "UML_MM1")  
  
## <a name="shapes-and-diagrams"></a>Tvary a diagramy  
 Prvky v modelu UML lze zobrazit v diagramech. Různé typy diagramů mohou zobrazit různé podtypy IElement.  
  
 V některých případech se může prvek zobrazit ve více než jeden diagram. Například IUseCase prvek může mít například několik IShapes, které lze zobrazit na jednom diagramu nebo různých diagramech.  
  
 Tvary jsou uspořádány ve stromové struktuře. Okraje stromu jsou reprezentovány vlastnostmi ParentShape a ChildShapes. Diagramy jsou pouze tvary, které nemají nadřazené položky. Tvary na povrchu diagramu se skládají z menších částí. Například tvar třídy má oddíly pro atributy a operace.  
  
 Další informace o tvarech naleznete v tématu [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="access-to-the-model-in-extensions"></a>Přístup k modelu v rozšířeních  
 V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření definovaných jako komponenty MEF můžete deklarovat vlastnosti, které importují informace z kontextu, ve kterém se spustí rozšíření.  
  
|Typ atributu|Získáte přístup k|Další informace|  
|--------------------|----------------------------------|----------------------|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> . IDiagramContext<br /><br /> (v Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|Aktuální diagram výběru.|[Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|  
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> . ILinkedUndoContext<br /><br /> (v Microsoft.VisualStudio.Modeling.Sdk. [version] .dll)|Umožňuje seskupení změn do transakce.|[Propojení aktualizací modelu UML pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md)|  
|Microsoft.VisualStudio.Shell. SVsServiceProvider<br /><br /> (v Microsoft.VisualStudio.Shell.Immutable. [version] .dll)|Hostitel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Odtud můžete přístup k souborům, projektům a další aspekty.|[Otevření modelu UML pomocí rozhraní API sady Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|  
  
### <a name="to-get-the-context"></a>Získání kontextu  
 Deklarace jednoho nebo obou z následujících rozhraní uvnitř vaší třídy rozšíření:  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
  
```  
  
 Managed Extensibility Framework (MEF) je naváže na definice, ze kterých můžete získat aktuální diagram, úložiště modelu, kořenový objekt a tak dále:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
IClassDiagram classDiagram = diagram as IClassDiagram;  
       // or diagrams of other types  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
### <a name="to-get-the-current-selection"></a>Chcete-li získat aktuální výběr  
  
```  
// All selected shapes and their elements  
foreach (IShape shape in diagram.SelectedShapes)  
{    
   IDiagram selectedDiagram = shape as IDiagram;  
   if (selectedDiagram != null)  
   { // no shape selected - user right-clicked the diagram  
     ... Context.CurrentDiagram ...  
   }  
   else  
   {  
     IElement selectedElement = shape.Element;  
   ...}  
// All selected shapes that display a specfic type of element  
foreach (IShape<IInterface> in   
   diagram.GetSelectedShapes<IInterface>())   
{...}  
```  
  
## <a name="accessing-another-model-or-diagrams"></a>Přístup k jiným modelům nebo diagramům  
 Můžeš:  
  
-   Použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model Service bus k vytvoření odkazů mezi prvky v různých modelech. Další informace najdete v tématu [modely UML integrovat s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Načíst projekt modelování a diagramy v režimu jen pro čtení bez zviditelnění v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uživatelské rozhraní. Další informace najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).  
  
-   Otevřete projekt modelování a jeho diagramy v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]a pak přístup k obsahu. Další informace najdete v tématu [otevření modelu UML pomocí rozhraní API sady Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)



