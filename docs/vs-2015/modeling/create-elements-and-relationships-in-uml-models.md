---
title: Vytváření elementů a vztahů v modelech UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ea066aa31cbc1f6408ee55c92a5ca761608f534
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667815"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>Vytváření elementů a vztahů v modelech UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V kódu programu pro rozšíření sady Visual Studio můžete vytvářet a odstraňovat prvky a vztahy.

## <a name="create-a-model-element"></a>Vytvoření elementu modelu

### <a name="namespace-imports"></a>Importy oboru názvů
 Musíte zahrnout následující příkazy `using`.

 Metody vytváření jsou definovány jako metody rozšíření v tomto oboru názvů:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Získejte vlastníka elementu, který chcete vytvořit.
 Model tvoří jeden strom, takže každá položka má jednoho vlastníka, s výjimkou kořene modelu. Kořen modelu je typu `IModel`, což je typ `IPackage`.

 Při vytváření prvku, který se zobrazí v konkrétním diagramu, například v aktuálním diagramu uživatele, byste ho měli obvykle vytvořit v balíčku připojeném k tomuto diagramu. Příklad:

```
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;
```

 Tato tabulka shrnuje vlastnictví společných prvků modelu:

|Element, který se má vytvořit|Owner|
|---------------------------|-----------|
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|
|`IAttribute, IOperation`|`IClass, IInterface`|
|`IPart, IPort`|`IComponent`|
|`IAction, IObjectNode`|`IActivity`|
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|

### <a name="invoke-the-create-method-on-the-owner"></a>Vyvolat metodu create pro vlastníka
 Název metody je ve formátu: `Create`*OwnedType* `()`. Příklad:

```
IUseCase usecase1 = linkedPackage.CreateUseCase();
```

 Některé typy mají složitější metody vytváření, zejména v sekvenčních diagramech. Viz [Úpravy sekvenčních diagramů UML pomocí rozhraní API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 U některých typů element můžete změnit vlastníka elementu během své životnosti pomocí `SetOwner(newOwner)`.

### <a name="set-the-name-and-other-properties"></a>Nastavení názvu a dalších vlastností

```
usecase1.Name = "user logs in";
```

### <a name="example"></a>Příklad

```
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Extensions;
...
 void InstantiateObserverPattern (IPackage package, string namePrefix)
 {    IInterface observer = package.CreateInterface();
      observer.Name = namePrefix + "Observer";
      IOperation operation = observer.CreateOperation();
      operation.Name = "Update";
      IClass subject = package.CreateClass();
      subject.Name = namePrefix + "Subject"; ...
```

## <a name="create-an-association"></a>Vytvořit přidružení

#### <a name="to-create-an-association"></a>Vytvoření přidružení

1. Získejte vlastníka přidružení, což je obvykle balíček nebo model obsahující zdrojové zakončení relace.

2. Vyvolejte požadovanou metodu create pro vlastníka.

3. Nastavte vlastnosti vztahu, jako je jeho název.

     Příklad:

    ```
    IAssociation association = subject.Package.CreateAssociation(subject, observer);
    association .Name = "Observes";
    ```

4. Nastavte vlastnosti všech konců relace. K dispozici jsou vždy dvě `MemberEnds`. Příklad:

    ```
    association .MemberEnds[0].Name = "subject";   // role name
    association .MemberEnds[1].Name = "observers"; // role name
    association .MemberEnds[1].SetBounds("0..*");
                // multiplicity defaults to "1"
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;
    ```

## <a name="create-a-generalization"></a>Vytvoření generalizace

```
IGeneralization generalization =
  subclass.CreateGeneralization(superClass);
```

## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Odstranění elementu, vztahu nebo generalizace z modelu

```
anElement.Delete();
```

 Při odstranění elementu z modelu:

- Odstraní se také všechny relace, které na ni odkazují.

- Odstraní se také všechny obrazce, které ho představují v diagramu.

## <a name="see-also"></a>Viz také
 [Rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md)
