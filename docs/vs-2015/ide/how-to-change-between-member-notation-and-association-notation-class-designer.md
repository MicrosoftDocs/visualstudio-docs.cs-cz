---
title: 'Postupy: Změna mezi zápisem člena a zápisem přidružení (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6a9a15b7284c647cb115c34b5655bdcaa7402ce0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663571"
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Postupy: Změna mezi zápisem člena a zápisem asociace (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V Návrhář tříd můžete změnit způsob, jakým diagram tříd představuje vztah přidružení mezi dvěma typy ze zápisu členů na notaci přidružení a naopak. Členy zobrazené jako řádky přidružení často poskytují užitečnou vizualizaci způsobu, jakým jsou typy spojeny.

> [!NOTE]
> Vztahy přidružení mohou být reprezentovány jako vlastnost nebo pole člena. Chcete-li změnit zápis členů na zápis přidružení, jeden typ musí mít člena jiného typu. Chcete-li změnit notaci přidružení na zápis členů, musí být tyto dva typy propojeny asociační linkou. Další informace naleznete v tématu [How to: Create Associations Between Types (návrhář tříd)](../ide/how-to-create-associations-between-types-class-designer.md). Pokud projekt obsahuje více diagramů tříd, změny provedené v diagramu způsob zobrazení vztahů přidružení ovlivňují pouze tento diagram. Chcete-li změnit způsob, jakým jiný diagram zobrazuje vztahy přidružení, otevřete nebo zobrazte tento diagram a proveďte tyto kroky.

### <a name="to-change-member-notation-to-association-notation"></a>Změna zápisu členů na notaci přidružení

1. Z uzlu projektu v Průzkumník řešení otevřete soubor diagramu tříd (. CD).

2. V obrazci typ v diagramu tříd klikněte pravým tlačítkem na vlastnost člena nebo pole představující přidružení a vyberte možnost **Zobrazit jako přidružení**.

    > [!TIP]
    > Pokud se v obrazci typu nezobrazí žádné vlastnosti ani pole, mohou být oddíly v tomto tvaru sbaleny. Chcete-li rozbalit tvar typu, poklikejte na název oddílu nebo klikněte pravým tlačítkem myši na obrazec typ a vyberte příkaz **Rozbalit**.

     Člen zmizí z oddílu v obrazovém prvku a zobrazí se čára přidružení pro propojení dvou typů. Asociační čára je označena názvem vlastnosti nebo pole.

### <a name="to-change-association-notation-to-member-notation"></a>Změna zápisu přidružení na zápis člena

- V diagramu tříd klikněte pravým tlačítkem na čáru přidružení a v případě potřeby vyberte **Zobrazit jako vlastnost** nebo **Zobrazit jako pole** .

     Čára přidružení zmizí a vlastnost se zobrazí v příslušném oddílu v rámci jejího typu obrazce v diagramu.

## <a name="see-also"></a>Viz také
 [Postupy: vytvoření dědičnosti mezi typy (návrhář tříd)](../ide/how-to-create-inheritance-between-types-class-designer.md) [Postupy: zobrazení dědičnosti mezi typy (návrhář tříd)](../ide/how-to-view-inheritance-between-types-class-designer.md) [zobrazení typů a vztahů (návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md) [postupy: vizualizace přidružení kolekce (návrhář tříd) ](../ide/how-to-visualize-a-collection-association-class-designer.md)
