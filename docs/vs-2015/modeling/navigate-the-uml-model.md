---
title: Navigace v modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23f87c81e43b2dfafb1c9c78c3135faff809bb9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74289852"
---
# <a name="navigate-the-uml-model"></a>Procházení modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma představuje hlavní typy modelu UML.

## <a name="the-model-elements-model-and-model-store"></a>Modely prvků, modelů a úložiště modelu
 Typy definované v sestavení **Microsoft.VisualStudio.Uml.Interfaces.dll** odpovídat typům definovaným ve [specifikaci UML verze 2.1.2](https://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).

 Typy ve specifikaci UML jsou realizovány jako rozhraní v aplikaci Visual Studio. K názvu každého typu se přidá písmeno "I". Příklad: [IElement](/previous-versions/dd516035(v=vs.140)), [IClass](/previous-versions/dd523539%28v%3dvs.140%29), [IOperation](/previous-versions/dd481186(v=vs.140)).

 Všechny typy s výjimkou IElement dědí vlastnosti z jednoho nebo více typů.

- Souhrn typů modelů naleznete v tématu [typy prvků modelu UML](../modeling/uml-model-element-types.md).

- Úplné podrobnosti o rozhraní API najdete v tématu [Reference k rozhraní API pro rozšiřitelnost modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md).

### <a name="relationships"></a>Relace
 Vlastnosti a vztahy, které jsou definovány ve specifikaci UML, jsou implementovány jako vlastnosti rozhraní .NET.

 Většina vztahů se v obou směrech naviguje. Vztah odpovídá páru vlastností s jednou vlastností typu na každém konci. Například vlastnosti `IElement.Owner` a `IElement.OwnedElements` reprezentují dva konce relace. Proto se tento výraz vždy vyhodnotí jako true:

 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`

 Mnoho vztahů, například IAssociation, je také reprezentované objektem, který může mít své vlastní vlastnosti.

 Odstraníte-li prvek z modelu, dojde k automatickému odstranění všech relací, ve kterých je součást obsažena a vlastnost na druhém konci je aktualizována.

 Pokud specifikace UML přiřadí násobnost 0.. 1 k vlastnosti, může mít hodnotu `null` . Násobnost s maximálním limitem větším než 1 znamená, že vlastnost .NET má typ: `IEnumerable<` *Type* `>` .

 Další informace o přecházení mezi vztahy najdete v tématu [navigace s rozhraním API UML](../modeling/navigate-relationships-with-the-uml-api.md).

### <a name="the-ownership-tree"></a>Strom vlastnictví
 Model obsahuje strom objektů [IElement](/previous-versions/dd516035(v=vs.140)) . Každý prvek má vlastnosti `OwnedElements` a `Owner` .

 Ve většině případů cíle `Owner` `OwnedElements` vlastností a odkazují také na jiné vlastnosti, které mají konkrétnější názvy. Například každá operace UML je vlastněna třídou UML. Proto [IOperation](/previous-versions/dd481186(v=vs.140)) má vlastnost s názvem [IOperation. Class](/previous-versions/dd473473%28v%3dvs.140%29)a v každém objektu [IOperation](/previous-versions/dd481186(v=vs.140)) `Class == Owner` .

 Nejvyšší prvek stromu, který nemá žádného vlastníka, je `AuxiliaryConstructs.IModel` . IModel je obsažen v `IModelStore` , ve kterém je [IModelStore. root](/previous-versions/ee789368(v=vs.140)).

 Každý prvek modelu je vytvořen s vlastníkem. Další informace najdete v tématu [vytváření elementů a vztahů v modelech UML](../modeling/create-elements-and-relationships-in-uml-models.md).

 ![Diagram tříd: model, diagram, tvar a element](../modeling/media/uml-mm1.png)

## <a name="shapes-and-diagrams"></a>Tvary a diagramy
 Prvky v modelu UML lze zobrazit v diagramech. Různé typy diagramů mohou zobrazovat různé podtypy IElement.

 V některých případech se element může objevit ve více než jednom diagramu. Například element IUseCase může mít několik IShapes, které se mohou objevit na jednom nebo několika diagramech.

 Tvary jsou uspořádány ve stromové struktuře. Okraje stromu jsou reprezentovány vlastnostmi ParentShape a ChildShapes. Diagramy jsou jediné tvary, které nemají nadřazené položky. Tvary na povrchu diagramu se skládají z menších částí. Například tvar třídy má oddíly pro atributy a operace.

 Další informace o obrazcích naleznete v tématu [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="access-to-the-model-in-extensions"></a>Přístup k modelu v rozšířeních
 V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšířeních definovaných jako komponenty MEF můžete deklarovat vlastnosti, které importují informace z kontextu, ve kterém je rozšíření spuštěno.

|Typ atributu|K čemu poskytuje přístup|Další informace|
|--------------------|----------------------------------|----------------------|
|Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost. Presentation<br /><br /> . IDiagramContext<br /><br /> (v Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|Aktuální diagram fokusu|[Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|
|Microsoft. VisualStudio. Modeling. ExtensionEnablement<br /><br /> . ILinkedUndoContext<br /><br /> (v Microsoft. VisualStudio. Modeling. SDK. [Version]. dll)|Umožňuje seskupit změny do transakcí.|[Propojení aktualizací modelu UML pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md)|
|Microsoft. VisualStudio. Shell. SVsServiceProvider<br /><br /> (v Microsoft. VisualStudio. Shell. unmutable. [Version]. dll)|Hostitel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Odtud získáte přístup k souborům, projektům a dalším aspektům.|[Otevření modelu UML pomocí rozhraní API sady Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|

### <a name="to-get-the-context"></a>Získání kontextu
 Deklarujte jedno nebo obě následující rozhraní v rámci třídy rozšíření:

```
[Import] public IDiagramContext DiagramContext { get; set; }

```

 Managed Extensibility Framework (MEF) je sváže s definicemi, ze kterých můžete získat aktuální diagram, úložiště modelu, kořenový objekt a tak dále:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
IClassDiagram classDiagram = diagram as IClassDiagram;
       // or diagrams of other types
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

### <a name="to-get-the-current-selection"></a>Získání aktuálního výběru

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

## <a name="accessing-another-model-or-diagrams"></a>Přístup k jinému modelu nebo diagramům
 Další možnosti:

- Pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Sběrnice modelu můžete vytvořit propojení mezi prvky v různých modelech. Další informace najdete v tématu [Integrace modelů UML s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Načtěte projekt modelování a diagramy v režimu jen pro čtení, bez toho, aby se zobrazily v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uživatelském rozhraní. Další informace najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).

- Otevřete projekt modelování a jeho diagramy v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a potom přejděte k obsahu. Další informace najdete v tématu [otevření modelu UML pomocí rozhraní API sady Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="see-also"></a>Viz také

- [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)
- [Programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)
