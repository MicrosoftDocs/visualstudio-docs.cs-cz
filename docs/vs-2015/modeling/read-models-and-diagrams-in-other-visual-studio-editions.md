---
title: Čtení modelů a diagramů v jiných edicích nástroje Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6d104d8d92345ba56d390fdd7ad9b856432b4c92
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757358"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Čtení modelů a diagramů v jiných edicích sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při otevření modelu ve verzi sady Visual Studio, který nepodporuje vytvoření modelu, model otevře v režimu jen pro čtení. V tomto režimu můžete změnit rozložení diagramy, ale nemůže změnit model.  
  
 Které verze sady Visual Studio podporují vytváření modelu najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Získání přístupu k modelu a diagramů  
 Číst diagramu UML nebo diagramu vrstvy, musíte nejdřív pomocí sady Visual Studio otevřete projekt modelování a otevřete diagram v něm.  
  
 Z tohoto důvodu Pokud si chcete přečíst diagramu UML nebo diagramu vrstev musí máte také přístup k projektu modelování, ve kterém byla vytvořena. Uděláte to buď díky přístupu do projektu z [!INCLUDE[esprscc](../includes/esprscc-md.md)], nebo prostřednictvím provedeného kopírování souborů projektu.  
  
> [!NOTE]
>  Tato akce není požadována kódu mapy a .NET třídy diagramy generované z kódu. Tyto diagramy lze zobrazit nezávisle na projektu modelování.  
  
 Další UML diagram nebo diagramu vrstvy, je minimální sadu souborů, které budete potřebovat:  
  
-   Dva soubory pro diagram, který si chcete přečíst, například diagramů **MyDiagram.classdiagram a MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Pro diagramy vrstev, také byste měli mít soubor s názvem _MyDiagram_**. layerdiagram.suppressions**.  
  
-   Soubor projektu modelování (**MyModel.modelproj**)  
  
-   V kořenovém souboru modelu (**ModelDefinition\MyModel.uml**)  
  
-   Soubory balíčku pro všechny balíčky odkazované v diagramu (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Změny provedené v režimu jen pro čtení  
 Pokud otevřete modelu a jeho diagramy v verzi sady Visual Studio, která nepodporuje vytváření modelu, nelze změnit model. To znamená nelze změnit na prvky a vztahy, které jsou zobrazeny v diagramech nebo v Průzkumníku modelů. Můžete ale proveďte nějaké změny rozložení diagramy:  
  
- Změna uspořádání obrazců a konektorů v diagramu.  
  
- Rozbalit nebo sbalit obrazce.  
  
  Je-li uložit tyto změny. Pokud chcete provádět změny viditelné pro ostatní uživatele, minimálně, odešlete aktualizovaný **.layout** soubory.  
  
##  <a name="RelatedTopics"></a> Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)|Diagram vrstvy znázorňuje strukturu existující nebo navrhovaný architektury. Při zápisu kódu ho dala automaticky ověřit proti diagramu vrstev.|  
|[Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)|Diagram činnosti ukazuje tok práce, v procesu podnikání nebo softwaru.|  
|[Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)|Diagram tříd se zobrazí typy a relace se používá v mnoha kontextech, například kód, databázová schémata, komunikační protokoly nebo Glosář termínů použitých k popisu obchodní domény.|  
|[Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)|Diagram komponent ukazuje oddělitelných částí v návrh softwaru a jejich rozhraní.|  
|[Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)|Sekvenční diagram ukazuje interakce mezi prvky návrhu softwaru.|  
|[Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)|Diagram případu použití zobrazuje uživatele systému a aktivity, které můžete provést k dosažení specifickým cílům.|  
  
## <a name="see-also"></a>Viz také  
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)



