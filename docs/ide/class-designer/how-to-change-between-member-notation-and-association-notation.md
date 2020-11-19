---
title: Změna mezi zápisem přidružení člena & (Návrhář tříd)
description: Naučte se, jak změnit způsob, jakým diagram tříd představuje vztah přidružení mezi dvěma typy ze zápisu členů k zápisu přidružení a naopak.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64d26b6ca1c71fe3484544f02006a27866ff4843
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901658"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Postupy: Změna mezi zápisem člena a zápisem přidružení v Návrhář tříd

V **Návrhář tříd** můžete změnit způsob, jakým diagram tříd představuje vztah přidružení mezi dvěma typy ze zápisu členů na notaci přidružení a naopak. Členy zobrazené jako řádky přidružení často poskytují užitečnou vizualizaci způsobu, jakým jsou typy spojeny.

> [!NOTE]
> Vztahy přidružení mohou být reprezentovány jako vlastnost nebo pole člena. Chcete-li změnit zápis členů na zápis přidružení, jeden typ musí mít člena jiného typu. Chcete-li změnit notaci přidružení na zápis členů, musí být tyto dva typy propojeny asociační linkou. Další informace naleznete v tématu [How to: Create Associations bBetween Types](how-to-create-associations-between-types.md). Pokud projekt obsahuje více diagramů tříd, změny provedené v diagramu způsob zobrazení vztahů přidružení ovlivňují pouze tento diagram. Chcete-li změnit způsob, jakým jiný diagram zobrazuje vztahy přidružení, otevřete nebo zobrazte tento diagram a proveďte tyto kroky.

## <a name="to-change-member-notation-to-association-notation"></a>Změna zápisu členů na notaci přidružení

1. Z uzlu projektu v Průzkumník řešení otevřete soubor diagramu tříd (. CD).

2. V obrazci typ v diagramu tříd klikněte pravým tlačítkem na vlastnost člena nebo pole představující přidružení a vyberte možnost **Zobrazit jako přidružení**.

    > [!TIP]
    > Pokud se v obrazci typu nezobrazí žádné vlastnosti ani pole, mohou být oddíly v tomto tvaru sbaleny. Chcete-li rozbalit tvar typu, poklikejte na název oddílu nebo klikněte pravým tlačítkem myši na obrazec typ a vyberte příkaz **Rozbalit**.

    Člen zmizí z oddílu v obrazovém prvku a zobrazí se čára přidružení pro propojení dvou typů. Asociační čára je označena názvem vlastnosti nebo pole.

## <a name="to-change-association-notation-to-member-notation"></a>Změna zápisu přidružení na zápis člena

V diagramu tříd klikněte pravým tlačítkem na čáru přidružení a v případě potřeby vyberte **Zobrazit jako vlastnost** nebo **Zobrazit jako pole** . Čára přidružení zmizí a vlastnost se zobrazí v příslušném oddílu v rámci jejího typu obrazce v diagramu.

## <a name="see-also"></a>Viz také

- [Postupy: vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md)
- [Postupy: zobrazení dědičnosti mezi typy](how-to-view-inheritance-between-types.md)
- [Zobrazování typů a vztahů](designing-and-viewing-classes-and-types.md)
- [Postupy: vizualizace přidružení kolekce](how-to-visualize-a-collection-association.md)
