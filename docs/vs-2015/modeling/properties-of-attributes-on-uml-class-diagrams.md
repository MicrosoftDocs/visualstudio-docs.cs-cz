---
title: Vlastnosti atributů v diagramech tříd UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: de32eba5fc6e4afc21d62f4432d9317d85408ffd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652070"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Vlastnosti atributů v diagramech tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu tříd UML lze přidat *atributy* do tříd a rozhraní. Atribut definuje hodnoty, které mohou být připojeny k instancím třídy nebo rozhraní.

 Chcete-li přidat atribut, klikněte pravým tlačítkem myši na třídu nebo rozhraní, přejděte na **Přidat**a potom klikněte na **atribut**.

 Pokud atributy třídy v diagramu nejsou viditelné, rozbalte kliknutím na dvojitou šipku v horní části třídy nebo rozhraní. Pokud vidíte záhlaví **atributů** , kliknutím na **[+]** rozbalte oddíl atributy.

## <a name="signature-of-an-attribute"></a>Podpis atributu
 Signatura atributu je řádek, který představuje v třídě nebo rozhraní v diagramu tříd UML. Má tento formát:

```
+ AttributeName : TypeName [*]
```

 \+ označuje veřejnou viditelnost. Ostatní povolené hodnoty jsou-(Private), # (Protected), ~ (Package).

 `AttributeName` je podtržena, pokud je atribut statický.

 `: TypeName` se vynechá, pokud atribut nemá žádný typ.

 `[*]` označuje násobnost. Pokud je násobnost 1, je vynechána.

## <a name="properties"></a>Vlastnosti
 Následující tabulka popisuje vlastnosti atributu v třídě nebo rozhraní v diagramu tříd UML.

 Chcete-li zobrazit vlastnosti atributu, klikněte pravým tlačítkem myši na atribut ve třídě nebo rozhraní v diagramu a potom klikněte na příkaz **vlastnosti**. Vlastnosti se zobrazí v okno Vlastnosti.

 Chcete-li zobrazit vlastnosti atributu, klikněte na něj pravým tlačítkem myši a poté klikněte na příkaz **vlastnosti**.

|   **Majetek**    | **Default**  |                                                                                                                                                                                                         Popis                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Výchozí hodnota** |   obsahovat    |                                                                                                                                                                               Hodnota atributu při vytvoření instance třídění.                                                                                                                                                                                |
| **Je jen pro čtení**  |    False     |                                                                                                                                                                                    Při hodnotě true se hodnota atributu nedá změnit.                                                                                                                                                                                    |
|   **Je statický**   |    False     |                                                                                                                    Je-li nastavena hodnota true, je jedna hodnota pro tento atribut sdílena mezi všemi instancemi tohoto typu.<br /><br /> Je-li nastavena hodnota true, název atributu je podtržen, kde se zobrazí v diagramu.                                                                                                                    |
|     **Jméno**      | (nový název) |                                                                                                                                                                                        By měl být jedinečný v rámci vlastnícího třídění.                                                                                                                                                                                        |
|     **Textový**      |    nTato    |                                                Primitivní typ, jako je například **celé číslo**nebo typ, který je definován v modelu. Nemůžete použít neprimitivní typy, jako je například **Decimal** , protože hodnota musí být kódována v metadatech. Pokud zadáte název nového typu v této vlastnosti, bude do oddílu **neurčené typy** v PRŮZKUMNÍKOVI modelů UML přidán typ.                                                 |
|  **Viditelnost**   |    Public    |                                     Povolené hodnoty a znaky, které se zobrazí v signatuře, jsou následující:<br /><br /> **+ Veřejný** – viditelné globálně<br /><br /> **-Private** -není viditelné mimo vlastnící typ<br /><br /> **# Protected** – Visible s typy odvozenými od vlastníka<br /><br /> **~ Balíček** – viditelný pro jiné typy v rámci stejného balíčku.                                      |
|  **Pracovní položky**   | 0 přidruženo |                                                                                                                          Počet přidružených pracovních položek Jen pro čtení.<br /><br /> Další informace naleznete v tématu [propojování prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Je list**    |    False     |                                                                                                                                                                    Je-li nastavena hodnota true, není určena k povolení předefinování tohoto atributu v odvozených typech.                                                                                                                                                                     |
|  **Je odvozen**   |    False     |                                                                                                              Je-li nastavena hodnota true, je tento atribut vypočítán z jiných atributů. Například úhlopříčně počítané z šířky a výšky. Podrobnosti by měly být zapsány v **popisu** nebo připojeném komentáři.                                                                                                              |
|  **Popis**  |   obsahovat    |                                                                                                                                                                        Pro obecné poznámky nebo pro definování omezení pro hodnoty v atributu.                                                                                                                                                                        |
| **Násobnost**  |      první       | **1** – tento atribut má jednu hodnotu zadaného typu.<br /><br /> **0.. 1** – tento atribut může mít hodnotu `null`.<br /><br /> **\\** \* – hodnota tohoto atributu je kolekcí hodnot.<br /><br /> **1.. \\** \* – hodnota atributu je kolekce, která obsahuje alespoň jednu hodnotu.<br /><br /> *n* **...** *m* – hodnota tohoto atributu je kolekce, která obsahuje hodnoty *n* a *m* . |
|  **Je seřazen**   |    False     |                                                                                                                                                                    V případě hodnoty true tvoří kolekce sekvenční seznam. Pro **násobnost** větší než 1.                                                                                                                                                                     |
|   **Je jedinečný**   |    False     |                                                                                                                                                                Pokud má hodnotu true, v kolekci nejsou žádné duplicitní hodnoty. Pro **násobnost** větší než 1.                                                                                                                                                                |

## <a name="see-also"></a>Viz také
 [Diagramy tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) [vlastnosti typů v](../modeling/properties-of-types-on-uml-class-diagrams.md) diagramech tříd UML [vlastnosti operací v](../modeling/properties-of-operations-on-uml-class-diagrams.md) diagramech tříd UML [Diagram tříd: pokyny](../modeling/uml-class-diagrams-guidelines.md) [diagramy](../modeling/uml-class-diagrams-guidelines.md) tříd UML: pokyny
