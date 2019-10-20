---
title: Čtení modelů a diagramů v jiných edicích sady Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6a7c944eb3d5378ad0fc1542b90ad182f7eb976
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671281"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Čtení modelů a diagramů v jiných edicích sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když otevřete model ve verzi sady Visual Studio, která nepodporuje vytváření modelů, model se otevře v režimu jen pro čtení. V tomto režimu můžete změnit rozložení diagramů, ale model nemůžete změnit.

 Chcete-li zjistit, které verze sady Visual Studio podporují vytváření modelů, přečtěte si téma [podpora verzí pro architektury a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Získání přístupu k modelu a diagramům
 Chcete-li si přečíst diagram UML nebo Diagram vrstev, je nutné nejprve pomocí sady Visual Studio otevřít projekt modelování a potom v něm otevřít diagram.

 Z tohoto důvodu, pokud chcete číst diagram UML nebo Diagram vrstev, musíte mít také přístup k projektu modelování, ve kterém byl vytvořen. To lze provést buď přístupem k projektu z [!INCLUDE[esprscc](../includes/esprscc-md.md)], nebo získáním kopie souborů projektu.

> [!NOTE]
> To se nevztahuje na mapy kódu a diagramy tříd .NET vygenerované z kódu. Tyto diagramy lze zobrazit nezávisle na projektu modelování.

 Chcete-li si přečíst diagram UML nebo Diagram vrstev, minimální sada souborů, které potřebujete, je následující:

- Dva soubory diagramu pro diagram, který chcete číst, například **MyDiagram. classdiagram a MyDiagram. classdiagram. Layout**.

    > [!NOTE]
    > Pro diagramy vrstev byste měli mít také soubor s názvem _MyDiagram_ **. layerdiagram. potlačení**.

- Soubor projektu modelování (**MyModel. modelproj**)

- Soubor kořenového modelu (**ModelDefinition\MyModel.UML**)

- Soubory balíčku pro každý balíček, na který se odkazuje v diagramu (**ModelDefinition\MyPackage.UML**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Změny, které lze provést v režimu jen pro čtení
 Pokud otevřete model a jeho diagramy ve verzi sady Visual Studio, která nepodporuje vytváření modelů, nelze model změnit. To znamená, že nemůžete změnit prvky a vztahy, které jsou zobrazeny v diagramech nebo v Průzkumníku modelů. V rozložení diagramů ale můžete udělat nějaké změny:

- Uspořádejte obrazce a spojnice v diagramu.

- Rozbalí a sbalí obrazce.

  Tyto změny můžete uložit. Pokud chcete, aby se změny projevily ostatním uživatelům, musíte aspoň odeslat aktualizované soubory **. Layout** .

## <a name="RelatedTopics"></a>Příbuzná témata

|Název|Popis|
|-----------|-----------------|
|[Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)|Diagram vrstev zobrazuje strukturu existující nebo navržené architektury. Při zápisu kódu je možné jej automaticky ověřit proti diagramu vrstev.|
|[Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)|Diagram aktivity znázorňuje pracovní postup, a to v obchodním procesu nebo v softwaru.|
|[Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)|Diagram tříd zobrazuje typy a vztahy používané v mnoha kontextech, jako jsou kód, schémata databáze, komunikační protokoly nebo Glosář termínů používaných k popisu obchodní domény.|
|[Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)|Diagram komponent zobrazuje oddělitelné části v návrhu softwaru a jejich rozhraních.|
|[Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)|Sekvenční diagram znázorňuje interakce mezi prvky v rámci návrhu softwaru.|
|[Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)|Diagram případu použití znázorňuje uživatele systému a aktivity, které mohou provádět, aby dosáhly konkrétních cílů.|

## <a name="see-also"></a>Viz také
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)
