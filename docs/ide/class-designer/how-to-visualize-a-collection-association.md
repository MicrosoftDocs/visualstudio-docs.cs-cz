---
title: 'Postupy: Vizualizace asociace kolekce (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ba237b9c763421287e3878a6a98f59032bfd092
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590771"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Postup: Vizualizace přidružení kolekce v Návrháři tříd

Vlastnosti a pole, které jsou kolekce jiných typů lze zobrazit v diagramu třídy jako přidružení kolekce. Na rozdíl od pravidelného přidružení, které zobrazuje pole nebo vlastnost jako řádek spojující vlastnící třídu s typem pole, je přidružení kolekce zobrazeno jako řádek spojující vlastnící třídu se shromážděným typem.

## <a name="to-create-a-collection-association"></a>Vytvoření přidružení kolekce

1. V kódu vytvořte vlastnost nebo pole, jehož typ je sám o sobě kolekcí silného typu.

2. V diagramu třídy rozbalte třídu tak, aby byly zobrazeny vlastnosti a pole.

3. Ve třídě klepněte pravým tlačítkem myši na pole nebo vlastnost a zvolte **Zobrazit jako přidružení kolekce**.

Vlastnost nebo pole je zobrazeno jako asociační čára, která odkazuje na shromážděný typ.

## <a name="see-also"></a>Viz také

- [Postup: Vytvoření přidružení mezi typy](how-to-create-associations-between-types.md)
- [Navrhování tříd a typů](designing-and-viewing-classes-and-types.md)
