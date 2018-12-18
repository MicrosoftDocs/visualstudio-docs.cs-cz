---
title: Vlastnosti elementů v UML použijte diagramy případu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a81f7630a1a903af2f9c21aee3249ea6fe156af2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762826"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Vlastnosti elementů v diagramech případů použití UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Každý prvek v diagramu v diagramu případu použití UML má vlastnosti. Pokud chcete zobrazit vlastnosti elementu, klikněte pravým tlačítkem na elementu v diagramu nebo v **Průzkumníku modelů UML** a potom klikněte na tlačítko **vlastnosti**. Vlastnosti se zobrazí v **vlastnosti** okna.  
  
> [!NOTE]
>  Toto téma se věnuje vlastnosti elementů v diagramech případů použití UML. Další informace o tom, jak přečíst diagramy činnosti UML, naleznete v tématu [diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md). Další informace o tom, jak nakreslit diagramy činnosti UML, naleznete v tématu [diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Vlastnosti elementů  
  
|Vlastnost|Výchozí|Prvek|Popis|  
|--------------|-------------|-------------|-----------------|  
|**Jméno**|Výchozí název|Všechny|Určuje element.|  
|**Kvalifikovaný název**|Balíček:: název|Všechny|Jednoznačně identifikuje elementu. Předponu úplný název balíčku, který jej obsahuje.|  
|**Pracovní položky**|související 0|Všechny|Počet pracovních položek, které jsou spojené s tímto prvkem. Přidružení pracovních položek, naleznete v tématu [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|  
|**Popis**|(žádné)|Všechny|Můžete nastavit obecné poznámky o prvku tady.|  
|**Barva**|(výchozí)|Všechny|Barva obrazce. Na rozdíl od dalších vlastností, to není vlastnost elementu, který tvar zobrazí.|  
|**Cesta k bitové kopii**|(žádné)|objekt actor|Cesta k souboru obrázku, který se má použít místo výchozí ikona objektu actor. Ikona by měl být soubor prostředků v rámci projektu sady Visual Studio.|  
|**Témata**|(žádné)|Případ použití|Podsystém nebo jiný typ, který vlastní případu použití.<br /><br /> Můžete ho nastavit tak, že v podsystému v diagramu případu použití.|  
|**Viditelnost**|Public|Používat subsystém případu, objekt Actor|**Veřejné** – viditelné globálně.<br /><br /> **Balíček** – viditelné v rámci balíčku.|  
|**IsAbstract**|False|Používat subsystém případu, objekt Actor|Při hodnotě true se typ nedá vytvořit instance a slouží jako základ pro specializaci pomocí jiné definice.|  
|**Instance je vytvořena nepřímo**|Hodnota TRUE|Subsystém|Subsystém existuje pouze jako artefakt návrhu. V době běhu existují jen jeho části.|  
|**Hypertextový odkaz**|(žádné)|Artefakt|Adresa URL nebo cesta diagramu nebo dokument, ke kterému artefaktu s odkazem.|  
  
 Seznam vlastností asociace, naleznete v tématu [vlastnosti přidružení v UML diagramech tříd](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Viz také  
 [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)



