---
title: Vlastnosti prvků v sekvenčních diagramech UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671430"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Vlastnosti elementů v sekvenčních diagramech UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sekvenčním diagramu UML mají jednotlivé prvky v diagramu vlastnosti. Chcete-li zobrazit vlastnosti prvku, klikněte pravým tlačítkem myši na prvek v diagramu nebo v **Průzkumníku modelů UML** a poté klikněte na možnost **vlastnosti**. Vlastnosti se zobrazí v okně **vlastnosti** .

> [!NOTE]
> Toto téma se týká vlastností prvků v sekvenčních diagramech UML. Další informace o tom, jak číst sekvenční diagramy UML, najdete v tématu [sekvenční diagramy UML: referenční informace](../modeling/uml-sequence-diagrams-reference.md). Další informace o vykreslování sekvenčních diagramů UML najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Vlastnosti prvků

|Vlastnost|Výchozí|Element|Popis|
|--------------|-------------|-------------|-----------------|
|**Name**|Výchozí název|Vše|Identifikuje element.|
|**Kvalifikovaný název**|Balíček:: Name|Vše|Identifikuje element jedinečně. Předpona s úplným názvem balíčku, který jej obsahuje.|
|**Pracovní položky**|0 přidruženo|Vše|Počet pracovních položek spojených s tímto prvkem. Chcete-li přidružit pracovní položky, přečtěte si téma [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|
|**Popis**|trhnout|Vše|Zde můžete vytvořit Obecné poznámky k položce.|
|**Color**|(výchozí pro typ prvku)|Životnost, zpráva|Barva obrazce Toto je vlastnost tvaru namísto prvku, který je zobrazen.|
|**Typ**|trhnout|Životnost|Typ instance, kterou představuje životnost.<br /><br /> Pokud je v záhlaví životnosti zobrazen symbol odkazu, pak tato třída nebo rozhraní existují samostatně v Průzkumníku modelů UML a lze je zobrazit v diagramu tříd.|
|**Actor** (Herec/herečka)|Ne|Životnost|Určuje, zda životnost představuje uživatele, zařízení nebo softwarovou součást, která je externí pro komponentu, o které diagram probíhá.|
|**Druh**|**Complete** – zpráva, která má odesílatele i příjemce.<br /><br /> **Nalezeno** – zpráva, která má nespecifikovaného odesílatele.<br /><br /> **Ztráta** – zpráva, která má nespecifikovaného příjemce.|Zpráva|Označuje, které konce zprávy jsou připojeny k životnosti.<br /><br /> Tuto vlastnost nelze změnit. Nastavuje se při vytváření zprávy.|
|**Seřadit**|**AsynchCall** – asynchronní zpráva.<br /><br /> **SynchCall** – synchronní zpráva.<br /><br /> **Reply** – návratová část synchronní zprávy<br /><br /> **CreateMessage** – zpráva vytvoření instance.|Zpráva|Typ zprávy Tuto vlastnost nelze změnit. Určuje ho nástroj, který použijete k vytvoření zprávy.|
|**Operace**|obsahovat|Zpráva|Metoda, kterou zpráva volala v přijímací životnosti.<br /><br /> Viditelné pouze v případě, že je přijímající životnost propojena s rozhraním nebo třídou.|
|**Odkazuje na**|Sekvenční diagram|Použití interakce|Sekvenční diagram volaný pomocí této interakce.|
|**Operátor interakce**|Nastavit při použití příkazu **Surround with**|Kombinovaný fragment|Operátor reprezentovaný tímto fragmentem nebo kolekcí fragmentů.|
|**Chráněn**|obsahovat|Operand interakce v kombinovaném fragmentu|K sekvenci v fragmentu nedojde, pokud není hodnota Guard pravdivá.<br /><br /> Pokud chcete vybrat horní fragment všech kombinovaných fragmentů, klikněte pod nadpisem fragmentu.|
|**Minimum, maximum**|(bez omezení)|Kombinovaný fragment smyčky|Minimální a maximální počet, kolikrát je smyčka provedena.|
|**Zprávy**|obsahovat|Vezměte v úvahu a<br /><br /> Ignorovat kombinované fragmenty|Zprávy, které jsou v tomto fragmentu zvažovány nebo ignorovány.|

## <a name="see-also"></a>Viz také
 [Sekvenční diagramy UML: odkazy](../modeling/uml-sequence-diagrams-reference.md) na [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md) [popisují tok řízení pomocí fragmentů v sekvenčních diagramech UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
