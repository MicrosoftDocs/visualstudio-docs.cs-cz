---
title: Vlastnosti typů v UML diagramech tříd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e8baad41658cc6144f08d0b6b4d415aa4ff6e499
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750104"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Vlastnosti typů v diagramech tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu tříd UML *typ* třída, rozhraní nebo výčet.  
  
> [!NOTE]
>  Toto téma se věnuje vlastnosti typů v diagramech tříd UML. Další informace naleznete v následujících tématech:  
  
-   [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)  
  
-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)  
  
-   [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
-   [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
## <a name="properties"></a>Vlastnosti  
 Toto jsou vlastnosti třídy, rozhraní nebo výčet.  
  
 Pokud chcete zobrazit vlastnosti typu, klikněte pravým tlačítkem na typu v diagramu nebo v **Průzkumníku modelů UML**a potom klikněte na tlačítko **vlastnosti**. Vlastnosti se zobrazí v **vlastnosti** okna.  
  
|**Vlastnost**|**Default**|Zobrazí se v|Popis|  
|------------------|-----------------|----------------|-----------------|  
|**Jméno**|Výchozí název|Všechny elementy|Určuje element.|  
|**Kvalifikovaný název**|Balíček obsahující:: Název typu|Všechny elementy|Jednoznačně identifikuje elementu. Předponu úplný název balíčku, který jej obsahuje.|  
|**Barva**|Výchozí hodnota pro druh typu.|Všechny elementy|Barva obrazce. Na rozdíl od dalších vlastností to není vlastnost základního prvku modelu. Různá zobrazení stejného typu může mít různé barvy.|  
|**Je abstraktní**|False|Třída|Při hodnotě true se třídu nelze vytvořit instanci a je určena pro použití jako základní třídu.|  
|**List**|False|Třída, rozhraní|Při hodnotě true je typ není určen pro mají odvozené typy.|  
|**Je aktivní**|False|Třída|Při hodnotě true se každá instance tohoto typu je přidružené vlákno ovládacího prvku.|  
|**Viditelnost**|Public|Třída, rozhraní, výčet|-Public - viditelné globálně.<br />-Soukromá: Tento typ je viditelný v rámci balíčku, který ho vlastní.<br />-Package - viditelné v rámci balíčku.|  
|**Pracovní položky**|související 0|Všechny elementy|Počet pracovních položek, které jsou spojené s tímto prvkem. Přidružení pracovních položek, naleznete v tématu [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|  
|**Popis**|(prázdné)|Všechny elementy|Můžete nastavit obecné poznámky o položce tady.|  
|**Vazba šablony**|(žádné)|Třída, rozhraní, výčet|Pokud není prázdná, tento typ je definován pomocí vytvoření vazby hodnoty parametrů do této třídy šablony. Rozbalte vlastnost zobrazíte vazby parametrů šablony.|  
|**Parametry šablony**|(žádné)|Třída, rozhraní, výčet|Pokud není prázdná, toto je třída šablony, která má uvedené parametry. Pokud chcete přidat parametry nebo zobrazit vlastnosti jednotlivé parametry, klikněte na tlačítko **[...]** .|  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)



