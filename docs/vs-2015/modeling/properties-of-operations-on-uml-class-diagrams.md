---
title: Vlastnosti operací v diagramech tříd UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671352"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Vlastnosti operací v diagramech tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu tříd UML můžete přidat *operace* do tříd a rozhraní. Operace je metoda nebo funkce, kterou lze provést instancí třídy nebo rozhraní.

 Chcete-li přidat operaci, klikněte pravým tlačítkem myši na třídu nebo rozhraní, přejděte na položku **Přidat**a poté klikněte na příkaz **operace**.

 Pokud nejsou operace třídy v diagramu viditelné, klikněte na tlačítko Rozbalit dvojitou šipku v horní části třídy nebo rozhraní. Pokud vidíte hlavičku **operace** , kliknutím na **[+]** rozbalte část operace.

## <a name="signature-of-an-operation"></a>Podpis operace
 Signatura operace je řádek textu, který je reprezentován v třídě nebo rozhraní v diagramu tříd UML. Má následující formát:

 \+ OperationName (parametr1: typ1 [*],...): ReturnType [\*]

 \+ označuje veřejnou viditelnost. Ostatní povolené hodnoty jsou-(Private), # (Protected), ~ (Package).

 `OperationName` je podtržena v případě, že je **statická** vlastnost true a je kurzívou, pokud je hodnota **abstract** vlastnosti true.

 `: ReturnType` je vynechán, pokud není definován žádný návratový typ.

 `[*]` označuje násobnost parametru nebo návratového typu. Pokud je násobnost 1, je vynechána.

 Úplný popis těchto vlastností najdete v další části.

## <a name="properties"></a>Vlastnosti
 Jedná se o vlastnosti operace v rámci třídy nebo rozhraní v diagramu tříd UML.

 Chcete-li zobrazit vlastnosti operace, klikněte pravým tlačítkem myši na operaci ve třídě nebo rozhraní v diagramu a potom klikněte na příkaz **vlastnosti**. Vlastnosti se zobrazí v okně **vlastnosti** .

|      Vlastnost       |   Výchozí    |                                                                                                                                                                                 Popis                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Jméno**       | (nový název) |                                                                                                                                                                By měl být jedinečný v rámci nadřazeného typu.                                                                                                                                                                 |
|   **Parametry**    |    nTato    |      Seznam s <em>názvem</em>**formuláře:** <em>typ</em> **,** <em>název</em> **:** <em>typ</em> **,....** Seznam upravíte kliknutím na **[...]** .<br /><br /> Typy mohou být primitivní typy nebo typy, které jsou definovány v modelu. Pokud zadáte název nového typu v této vlastnosti, bude do oddílu **neurčené typy** v PRŮZKUMNÍKOVI modelů UML přidán typ.      |
|   **Návratový typ**   |    nTato    |                                                                               **(žádný)** , nebo primitivní typ, nebo typ, který je definován v modelu. Pokud zadáte název nového typu v této vlastnosti, bude do oddílu **neurčené typy** v PRŮZKUMNÍKOVI modelů UML přidán typ.                                                                                |
| **Následné podmínky**  |    nTato    |                                                                                                                         Volitelná podmínka určující vztah mezi stavem systému před a po provedení operace.                                                                                                                         |
|  **Předběžné podmínky**  |    nTato    |                                                                                                                            Volitelná podmínka určující předpoklady stavu systému před zahájením operace.                                                                                                                            |
| **Podmínky textu** |    nTato    |                                                                                                                                                       Volitelné omezení pro hodnoty vrácené operací.                                                                                                                                                       |
|   **Viditelnost**    |    Public    |                  Povolené hodnoty a znaky, které se zobrazují v signatuře, jsou:<br /><br /> **+ Veřejný** – viditelné globálně<br /><br /> **-Private** -není viditelné mimo vlastnící typ<br /><br /> **# Protected** – Visible s typy odvozenými od vlastníka<br /><br /> **~ Balíček** – viditelný pro jiné typy v rámci stejného balíčku.                   |
|    **Označení**    |  *název*+ ()   |                                                                                      Shrnuje viditelnost, název, parametry a návratový typ této operace. Tyto vlastnosti můžete změnit úpravou signatury v diagramu nebo úpravou jednotlivých vlastností.                                                                                      |
|   **Pracovní položky**    | 0 přidruženo |                                                                                                  Počet přidružených pracovních položek Jen pro čtení.<br /><br /> Další informace naleznete v tématu [propojování prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Souběžnost**   |  Navazující  | **Sekvenční** – operace je nebo bude navržena bez řízení souběžnosti. Volání této operace současně může vést k chybám.<br /><br /> **Guard** – operace se automaticky zablokuje, dokud se nedokončí jiné instance.<br /><br /> **Souběžná** operace je navržena tak, aby bylo možné současně spustit více volání. |
|    **Je statický**    |    False     |                                                                                                  Pokud má hodnotu true, tato operace se sdílí mezi všemi instancemi tohoto typu.<br /><br /> Pokud je hodnota true, název operace bude podtržen, kde se zobrazí v diagramu.                                                                                                   |
|   **Je abstraktní**   |    False     |                                                                                                                                        Pokud je nastaveno na true, k této operaci není přidružen žádný kód. Vlastnící třída proto je abstraktní.                                                                                                                                         |
|     **Je list**     |    False     |                                                                                                                                              Návrhář chce, aby tato operace nemohla být přepsána v odvozených třídách.                                                                                                                                              |
|    **Je dotaz**     |    False     |                                                                                                 V případě hodnoty true nejsou touto operací provedeny žádné významné změny stavu systému. Proto jej lze použít například v testu ke kontrole stavu systému.                                                                                                  |
|  **Násobnost**   |      první       |                                 **1** – jediná hodnota zadaného typu.<br /><br /> **0.. 1** – lze `null`.<br /><br /> \* – kolekce hodnot zadaného typu.<br /><br /> **1.. \\** \*-kolekce obsahující alespoň jednu hodnotu.<br /><br /> *n* `..` *m* – kolekce, která obsahuje hodnoty `n` a `m`.                                  |
|   **Je seřazen**    |    False     |                                                                                                                                             V případě hodnoty true tvoří kolekce sekvenční seznam. Pro **násobnost** větší než 1.                                                                                                                                              |
|    **Je jedinečný**    |    False     |                                                                                                                                         Pokud má hodnotu true, v kolekci nejsou žádné duplicitní hodnoty. Pro **násobnost** větší než 1.                                                                                                                                         |

## <a name="see-also"></a>Viz také
 [Diagramy tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) [vlastnosti typů v diagramech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [vlastnosti atributů v](../modeling/properties-of-attributes-on-uml-class-diagrams.md) diagramech tříd UML [Vlastnosti přidružení v diagramech](../modeling/properties-of-associations-on-uml-class-diagrams.md) tříd UML diagramy tříd [UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)
