---
title: Vlastnosti prvků v diagramech případů použití UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671418"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Vlastnosti elementů v diagramech případů použití UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu případu použití UML mají jednotlivé prvky v diagramu vlastnosti. Chcete-li zobrazit vlastnosti prvku, klikněte pravým tlačítkem myši na prvek v diagramu nebo v **Průzkumníku modelů UML** a poté klikněte na možnost **vlastnosti**. Vlastnosti se zobrazí v okně **vlastnosti** .

> [!NOTE]
> Toto téma se týká vlastností prvků v diagramech případů použití UML. Další informace o tom, jak číst diagramy činnosti UML, najdete v tématu [Diagramy případů použití UML: referenční informace](../modeling/uml-use-case-diagrams-reference.md). Další informace o tom, jak kreslit diagramy činnosti UML, najdete v tématu [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Vlastnosti prvků

|Vlastnost|Výchozí|Element|Popis|
|--------------|-------------|-------------|-----------------|
|**Name**|Výchozí název|Vše|Identifikuje element.|
|**Kvalifikovaný název**|Balíček:: Name|Vše|Identifikuje element jedinečně. Předpona s úplným názvem balíčku, který jej obsahuje.|
|**Pracovní položky**|0 přidruženo|Vše|Počet pracovních položek spojených s tímto prvkem. Chcete-li přidružit pracovní položky, přečtěte si téma [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|
|**Popis**|(žádná)|Vše|Zde můžete vytvořit Obecné poznámky k elementu.|
|**Color**|(výchozí)|Vše|Barva obrazce Na rozdíl od jiných vlastností není to vlastnost elementu, který obrazec zobrazuje.|
|**Cesta k obrázku**|(žádná)|Actor (Herec/herečka)|Cesta k souboru obrázku, který má být použit místo výchozí ikony objektu actor Ikona by měla být soubor prostředků v projektu sady Visual Studio.|
|**Studijní**|(žádná)|Případ použití|Podsystém nebo jiný typ, který vlastní případ použití.<br /><br /> Můžete ji nastavit umístěním případu použití na podsystém v diagramu.|
|**Přehlednost**|Veřejná|Případ použití, objekt actor, podsystém|**Public** Celosvětově viditelné.<br /><br /> **Balíček** – viditelné v rámci balíčku.|
|**-Abstract**|Ne|Případ použití, objekt actor, podsystém|Je-li nastavena hodnota true, nelze vytvořit instanci typu a je určena jako základ pro specializaci jinými definicemi.|
|**Je nepřímo vytvořena instance**|Ano|Provozuschopn|Podsystém existuje pouze jako artefakt návrhu. V době běhu pouze jeho části.|
|**Hypertextový odkaz**|(žádná)|Artefakt|Adresa URL nebo cesta k souboru diagramu nebo dokumentu, ke kterému artefakt poskytuje odkaz|

 Seznam vlastností přidružení naleznete v tématu [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

## <a name="see-also"></a>Viz také
 [Diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)
