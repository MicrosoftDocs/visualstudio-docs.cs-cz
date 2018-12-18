---
title: Vlastnosti elementů v UML sekvenční diagramy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 01d63e39967df361d87ff0182b1c85b6ecd2fdb6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793890"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Vlastnosti elementů v sekvenčních diagramech UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Každý prvek v diagramu v sekvenčním diagramu UML, má vlastnosti. Pokud chcete zobrazit vlastnosti elementu, klikněte pravým tlačítkem na elementu v diagramu nebo v **Průzkumníku modelů UML** a potom klikněte na tlačítko **vlastnosti**. Vlastnosti se zobrazí v **vlastnosti** okna.  
  
> [!NOTE]
>  Toto téma se věnuje vlastnosti elementů v sekvenčních diagramech UML. Další informace o tom, jak číst sekvenčních diagramech UML, naleznete v tématu [sekvenční diagramy UML: referenční](../modeling/uml-sequence-diagrams-reference.md). Další informace o tom, jak nakreslit sekvenční diagramy UML, naleznete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Vlastnosti elementů  
  
|Vlastnost|Výchozí|Prvek|Popis|  
|--------------|-------------|-------------|-----------------|  
|**Jméno**|Výchozí název|Všechny|Určuje element.|  
|**Kvalifikovaný název**|Balíček:: název|Všechny|Jednoznačně identifikuje elementu. Předponu úplný název balíčku, který jej obsahuje.|  
|**Pracovní položky**|související 0|Všechny|Počet pracovních položek, které jsou spojené s tímto prvkem. Přidružení pracovních položek, naleznete v tématu [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|  
|**Popis**|(prázdné)|Všechny|Můžete nastavit obecné poznámky o položce tady.|  
|**Barva**|(výchozí nastavení pro typ prvku)|Životnosti, zprávy|Barva obrazce. Toto je vlastnost obrazce, místo elementu se zobrazí.|  
|**Typ**|(prázdné)|Životnost|Typ instance představující životnost.<br /><br /> Pokud není symbol odkaz zobrazený v záhlaví životnosti, pak tuto třídu nebo rozhraní v Průzkumníku modelů UML, existuje samostatně a lze zobrazit v diagramu tříd.|  
|**objekt actor**|False|Životnost|Určuje, zda životnost představuje uživatele, zařízení nebo softwarové komponenty, která je externí součásti, která spočívá v diagramu.|  
|**Typ**|**Kompletní** – zpráva, která má odesílatel a příjemce.<br /><br /> **Najít** – zprávu, která má neurčené odesílatele.<br /><br /> **Ztráty** – zpráva, která má neurčené příjemce.|Zpráva|Určuje, které končí zprávy jsou připojeny k životnost.<br /><br /> Tuto vlastnost nelze změnit. Nastavení při vytváření zprávy.|  
|**Řazení**|**AsynchCall** -asynchronních zpráv.<br /><br /> **SynchCall** -synchronní zprávy.<br /><br /> **Odpověď** -návratový část synchronní zprávy.<br /><br /> **CreateMessage** – zpráva o vytvoření instance.|Zpráva|Typ zprávy. Tuto vlastnost nelze změnit. Je určen nástroj, který používáte k vytvoření zprávy.|  
|**Operace**|(prázdné)|Zpráva|Metoda volána zprávu v přijímající životnost.<br /><br /> Viditelné pouze v případě, že je propojený přijímání životnost rozhraní nebo třídu.|  
|**Odkazuje na**|Sekvenční diagram|Použitím interakce|Sekvenční diagram, který volá tento použitím interakce.|  
|**Interakce – operátor**|Nastavit, pokud jste použili **obklopit fragmentem** příkaz|Kombinovaného fragmentu|Operátor reprezentována tento fragment nebo kolekci fragmentů.|  
|**Guard**|(prázdné)|Operand interakce do kombinovaného fragmentu|Pořadí ve fragmentu nedojde, není-li ochranného zařízení má hodnotu true.<br /><br /> Vybrat začátek fragmentu jakékoli kombinovaného fragmentu klikněte pod názvem fragment.|  
|**Min, Max**|(bez omezení)|Smyčka kombinovaného fragmentu|Minimální a maximální počet pokusů, které provedení smyčky je.|  
|**Zprávy**|(prázdné)|Vezměte v úvahu a<br /><br /> Ignorovat kombinované fragmenty|Zprávy, které jsou považovány za nebo ignorovat v tomto fragmentu.|  
  
## <a name="see-also"></a>Viz také  
 [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)   
 [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Popis toku řízení pomocí fragmentů v sekvenčních diagramech UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)



