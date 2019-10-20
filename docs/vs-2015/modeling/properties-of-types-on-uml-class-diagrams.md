---
title: Vlastnosti typů v diagramech tříd UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9881393e792cf8bf49dc6d0b9459b18969dea171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671319"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Vlastnosti typů v diagramech tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu tříd UML *typ* je třída, rozhraní nebo výčet.

> [!NOTE]
> Toto téma se týká vlastností typů v diagramech tříd UML. Další informace naleznete v následujících tématech:

- [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)

- [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)

- [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

## <a name="properties"></a>Vlastnosti
 Jedná se o vlastnosti třídy, rozhraní nebo výčtu.

 Chcete-li zobrazit vlastnosti typu, klikněte pravým tlačítkem myši na typ v diagramu nebo v **Průzkumníku modelů UML**a poté klikněte na možnost **vlastnosti**. Vlastnosti se zobrazí v okně **vlastnosti** .

|**Majetek**|**Default**|Zobrazuje se v|Popis|
|------------------|-----------------|----------------|-----------------|
|**Jméno**|Výchozí název|Všechny elementy|Identifikuje element.|
|**Kvalifikovaný název**|Obsahující balíček:: název typu|Všechny elementy|Identifikuje element jedinečně. Předpona s úplným názvem balíčku, který jej obsahuje.|
|**Barevných**|Výchozí pro druh typu|Všechny elementy|Barva tohoto obrazce Na rozdíl od ostatních vlastností to není vlastnost podkladového prvku modelu. Různá zobrazení stejného typu mohou mít různé barvy.|
|**Je abstraktní**|False|Třída|Pokud má hodnotu true, nemůže být vytvořena instance třídy a je určena pro použití jako základní třída.|
|**Je list**|False|Třída, rozhraní|Je-li nastavena hodnota true, typ není určen pro odvozený typ.|
|**Je aktivní**|False|Třída|Pokud je nastaveno na true, každá instance tohoto typu je přidružena k vláknu ovládacího prvku.|
|**Viditelnost**|Public|Třída, rozhraní, výčet|– Public-globaled Visible.<br />-Private – tento typ je viditelný v rámci balíčku, který vlastní.<br />-Package-Visible v rámci balíčku.|
|**Pracovní položky**|0 přidruženo|Všechny elementy|Počet pracovních položek spojených s tímto prvkem. Chcete-li přidružit pracovní položky, přečtěte si téma [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|
|**Popis**|trhnout|Všechny elementy|Zde můžete vytvořit Obecné poznámky k položce.|
|**Vazba šablony**|nTato|Třída, rozhraní, výčet|Pokud není prázdné, tento typ je definován pomocí hodnoty parametrů vazby k této třídě šablony. Rozbalením vlastnosti zobrazíte vazby parametrů šablony.|
|**Parametry šablony**|nTato|Třída, rozhraní, výčet|Pokud není prázdné, jedná se o třídu šablony, která obsahuje níže uvedené parametry. Chcete-li přidat parametry nebo zobrazit vlastnosti jednotlivých parametrů, klikněte na položku **[...]** .|

## <a name="see-also"></a>Viz také
 [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) vlastnosti [operací v](../modeling/properties-of-operations-on-uml-class-diagrams.md) diagramech tříd UML [Vlastnosti přidružení v](../modeling/properties-of-associations-on-uml-class-diagrams.md) diagramech tříd UML diagramy [tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)
