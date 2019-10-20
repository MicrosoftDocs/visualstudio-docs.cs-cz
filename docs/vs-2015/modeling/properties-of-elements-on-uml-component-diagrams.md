---
title: Vlastnosti prvků v diagramech komponent UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671452"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Vlastnosti elementů v diagramech komponent UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu komponent UML mají jednotlivé prvky v diagramu vlastnosti. Chcete-li zobrazit vlastnosti prvku, klikněte pravým tlačítkem myši na prvek v diagramu nebo v **Průzkumníku modelů UML** a poté klikněte na možnost **vlastnosti**. Vlastnosti se zobrazí v okně **vlastnosti** .

> [!NOTE]
> Toto téma se týká vlastností prvků v diagramech komponent UML. Další informace o tom, jak číst diagramy komponent UML, najdete v tématu [diagramy komponent UML: referenční informace](../modeling/uml-component-diagrams-reference.md). Další informace o tom, jak kreslit diagramy komponent UML, najdete v tématu [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Vlastnosti prvků

|Vlastnost|Výchozí|Prvek|Popis|
|--------------|-------------|-------------|-----------------|
|**Jméno**|Výchozí název|Všechny|Identifikuje element.|
|**Kvalifikovaný název**|Obor názvů:: Name|Všechny|Identifikuje element jedinečně.<br /><br /> Název komponenty nebo typu je předponou s kvalifikovaným názvem balíčku, který jej obsahuje.<br /><br /> Název součásti nebo portu je předponou kvalifikovaného názvu komponenty, která ji vlastní.|
|**Pracovní položky**|0 přidruženo|Všechny|Počet pracovních položek spojených s tímto prvkem. Chcete-li přidružit pracovní položky, přečtěte si téma [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|
|**Popis**|nTato|Všechny|Zde můžete vytvořit Obecné poznámky k elementu.|
|**Barevných**|(výchozí pro typ)|Komponenta, součást, delegování, sestavení součásti|Barva obrazce Na rozdíl od jiných vlastností je to barva tvaru namísto prvku modelu, který obrazec zobrazuje.|
|**Je nepřímo vytvořena instance**|Podmínka|Součást|Komponenta existuje pouze jako artefakt návrhu. V době běhu pouze jeho části.|
|**Je abstraktní**|False|Součást|Definice komponenty se dá použít jenom jako generalizace, ze které můžou být specializované jiné komponenty.|
|**Viditelnost**|Public|Součást, součást, port|Celosvětově viditelné.<br /><br /> **Balíček** – viditelné v rámci balíčku.<br /><br /> **Soukromý** – viditelné v rámci vlastnící součásti.<br /><br /> **Protected** -Visible pro součásti odvozené od vlastníka.|
|**Textový**|Typ při vytváření|Částí<br /><br /> Přístavní|Typ součásti je komponenta nebo třída.<br /><br /> Typ portu je rozhraní.|
|**Násobnost**|první|Částí<br /><br /> Přístavní|Určuje, kolik instancí zadaného typu tvoří část nadřazené komponenty.<br /><br /> `1` – právě jeden.<br /><br /> `0..1`-One nebo None.<br /><br /> `*` – kolekce libovolného čísla.<br /><br /> `n..m` – kolekce z n až m instancí.|
|**Je chování**|False|Přístavní|Je-li nastavena hodnota true, zprávy na tento port jsou zpracovávány aktivitami nebo operacemi, které jsou popsány jako součást komponenty, namísto jejích částí.|
|**Je služba**|False|Přístavní|Pokud je nastaveno na true, tento port je součástí publikovaného rozhraní této součásti.|
|**LinkedPackage**|Vzorový|diagram|Výchozí obor názvů pro prvky přidané do tohoto diagramu.|

## <a name="see-also"></a>Viz také
 [Diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)
