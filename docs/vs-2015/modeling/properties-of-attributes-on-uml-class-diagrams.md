---
title: Vlastnosti atributů v UML diagramech tříd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0129242593596ea7e3875db2a748045c50863c4c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817357"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Vlastnosti atributů v diagramech tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu tříd UML lze přidat *atributy* u tříd a rozhraní. Atribut definuje hodnoty, které lze připojit k instancím typu třídy nebo rozhraní.  

 Chcete-li přidat atribut, klikněte pravým tlačítkem na třídu nebo rozhraní, přejděte na **přidat**a potom klikněte na tlačítko **atribut**.  

 Pokud se atributy třídy v diagramu se nezobrazí, klikněte na dvojitou šipku v horní části třídy nebo rozhraní a rozbalte ho. Pokud se zobrazí **atributy** záhlaví, klikněte na tlačítko **[+]** tím rozbalíte atributy.  

## <a name="signature-of-an-attribute"></a>Signatura atributu  
 Signatura atributu je řádek, který představuje třídu nebo rozhraní v diagramu tříd UML. Má tento formát:  

```  
+ AttributeName : TypeName [*]  
```  

 \+ označuje public viditelnost. Povolené hodnoty jsou – (privátní), # (chráněný), ~ (balíček).  

 `AttributeName` je podtržený, pokud atribut není statické.  

 `: TypeName` je vynechána, pokud atribut nemá žádný typ.  

 `[*]` označuje násobnosti. To je vynechána, pokud je násobnost 1.  

## <a name="properties"></a>Vlastnosti  
 Následující tabulka popisuje vlastnosti atribut ve třídě nebo rozhraní v diagramu tříd UML.  

 Můžete zobrazit vlastnosti atributu, klikněte pravým tlačítkem na atribut v dané třídy nebo rozhraní v diagramu a klikněte na **vlastnosti**. Vlastnosti se zobrazí v okně Vlastnosti.  

 Chcete-li zobrazit vlastnosti atributu, pravým tlačítkem myši a potom klikněte na **vlastnosti**.  


|   **Vlastnost**    | **Default**  |                                                                                                                                                                                                         Popis                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Výchozí hodnota** |   (prázdné)    |                                                                                                                                                                               Hodnota atributu při vytváření instance klasifikátoru.                                                                                                                                                                                |
| **Je jen pro čtení**  |    False     |                                                                                                                                                                                    Při hodnotě true nelze změnit hodnotu atributu.                                                                                                                                                                                    |
|   **Je statická**   |    False     |                                                                                                                    Při hodnotě true se jednu hodnotu pro tento atribut sdílí mezi všechny instance tohoto typu.<br /><br /> Při hodnotě true je podtržený název atributu, kde se zobrazí v diagramu.                                                                                                                    |
|     **Jméno**      | (nové jméno) |                                                                                                                                                                                        Musí být jedinečné v rámci vlastnící třídění.                                                                                                                                                                                        |
|     **Typ**      |    (žádné)    |                                                Primitivní typ, jako **celé číslo**, nebo typ, který je definován v modelu. Neprimitivní typy nelze používat jako **desítkové** vzhledem k tomu, že hodnota musí být kódovány v metadatech. Pokud zadáte název pro nový typ této vlastnosti, typ se přidají do **nespecifikované typy** části Průzkumníku modelů UML.                                                 |
|  **Viditelnost**   |    Public    |                                     Povolené hodnoty a znaků, které se zobrazí v signatuře jsou následující:<br /><br /> **+ Veřejné** – viditelné globálně<br /><br /> **-Privátní** – nejsou viditelné mimo vlastnící typ<br /><br /> **# Chráněné** – viditelné pro typy odvozené od vlastníka<br /><br /> **~ Balíček** – viditelné pro ostatní typy v rámci stejného balíčku.                                      |
|  **Pracovní položky**   | související 0 |                                                                                                                          Počet přidružené pracovní položky. Jen pro čtení.<br /><br /> Další informace najdete v tématu [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **List**    |    False     |                                                                                                                                                                    Pokud je hodnota true, není určený k tomu předefinování tento atribut v odvozených typech.                                                                                                                                                                     |
|  **Je odvozen**   |    False     |                                                                                                              Při hodnotě true se tento atribut se počítá od jiné atributy. Úhlopříčně, například počítají na základě šířku a výšku. Podrobnosti by měly být napsány v **popis** nebo připojeného komentáře.                                                                                                              |
|  **Popis**  |   (prázdné)    |                                                                                                                                                                        Pro obecné poznámky nebo k definování omezení hodnot v atributu.                                                                                                                                                                        |
| **Násobnost**  |      1       | **1** – tento atribut je samostatná hodnota ze zadaného typu.<br /><br /> **0..1** – tento atribut může mít hodnotu `null`.<br /><br /> **\\**\* – Hodnota tohoto atributu je kolekce hodnot.<br /><br /> **1..\\**  \* – hodnota tohoto atributu je kolekce, která obsahuje alespoň jednu hodnotu.<br /><br /> *n* **...** *m* – hodnota tohoto atributu je kolekce, který obsahuje od *n* a *m* hodnoty. |
|  **Je seřazen**   |    False     |                                                                                                                                                                    Při hodnotě true se vytváří kolekce sekvenční seznamu. Pro **násobnost** více než 1.                                                                                                                                                                     |
|   **Je jedinečný**   |    False     |                                                                                                                                                                Pokud je hodnota true, nejsou v kolekci žádné duplicitní hodnoty. Pro **násobnost** více než 1.                                                                                                                                                                |

## <a name="see-also"></a>Viz také  
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Vlastnosti typů v diagramech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)   
 [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)



