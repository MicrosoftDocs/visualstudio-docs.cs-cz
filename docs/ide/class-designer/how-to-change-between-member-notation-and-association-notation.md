---
title: Změna mezi zápisem přidružení člena & (Návrhář tříd)
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 9f706acfbaee7c6170f74bc655f9172ff6bdd3b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592266"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Postup: Změna mezi zápisem člena a zápisem přidružení v Návrháři tříd

V **Návrháři tříd**můžete změnit způsob, jakým diagram třídy představuje vztah přidružení mezi dvěma typy od zápisu člena k zápisu přidružení a naopak. Členové zobrazené jako asociační čáry často poskytují užitečnou vizualizaci toho, jak typy souvisejí.

> [!NOTE]
> Vztahy přidružení mohou být reprezentovány jako vlastnost člena nebo pole. Chcete-li změnit zápis člena na zápis přidružení, musí mít jeden typ člena jiného typu. Chcete-li změnit zápis přidružení na zápis člena, musí být tyto dva typy propojeny asociační čárou. Další informace naleznete v [tématu How to: Create associations bBetween types](how-to-create-associations-between-types.md). Pokud projekt obsahuje více diagramů tříd, změny provedené ve způsobu, jakým diagram zobrazuje vztahy přidružení, ovlivní pouze tento diagram. Chcete-li změnit způsob, jakým jiný diagram zobrazuje vztahy přidružení, otevřete nebo zobrazte tento diagram a proveďte tyto kroky.

## <a name="to-change-member-notation-to-association-notation"></a>Změna zápisu člena na zápis přidružení

1. Z uzlu projektu v Průzkumníku řešení otevřete soubor diagramu tříd (.cd).

2. V obrazci typu v diagramu třídy klepněte pravým tlačítkem myši na vlastnost člena nebo pole představující přidružení a zvolte **Zobrazit jako přidružení**.

    > [!TIP]
    > Pokud v obrazci typu nejsou viditelné žádné vlastnosti nebo pole, mohou být oddíly v obrazci sbaleny. Chcete-li obrazec typu rozbalit, poklepejte na název oddílu nebo klepněte pravým tlačítkem myši na textový obrazec a zvolte **Rozbalit**.

    Člen zmizí z prostoru v obrazci typu a zobrazí se asociační čára, která spojuje dva typy. Řádek přidružení je označen názvem vlastnosti nebo pole.

## <a name="to-change-association-notation-to-member-notation"></a>Změna zápisu přidružení na zápis člena

V diagramu třídy klikněte pravým tlačítkem myši na řádek přidružení a podle potřeby zvolte **Zobrazit jako vlastnost** nebo Zobrazit jako **pole.** Asociační čára zmizí a vlastnost se zobrazí v příslušném prostoru v rámci svého tvaru typu v diagramu.

## <a name="see-also"></a>Viz také

- [Postup: Vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md)
- [Postup: Zobrazení dědičnosti mezi typy](how-to-view-inheritance-between-types.md)
- [Zobrazování typů a vztahů](designing-and-viewing-classes-and-types.md)
- [Postup: Vizualizace přidružení kolekce](how-to-visualize-a-collection-association.md)
