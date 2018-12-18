---
title: 'Postupy: Vizualizace asociace kolekce (návrhář tříd)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24dc8b21fbdacb5da2795b215cd8503b08cf3449
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33995878"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Postupy: vizualizace asociace kolekce v Návrháři tříd

Vlastnosti a pole, které jsou kolekce položek dalších typů lze zobrazit v diagramu tříd jako asociace kolekce. Na rozdíl od regulární přidružení, který zobrazí pole nebo vlastnost jako řádek propojení vlastnícím – třída typu pole, asociace kolekce se zobrazí jako řádek propojení vlastnícím třída shromážděných typu.

## <a name="to-create-a-collection-association"></a>Chcete-li vytvořit asociace kolekce

1.  V kódu vytvořte vlastnost nebo pole s typem je sám vytvořit kolekci silného typu.

2.  V diagramu tříd rozbalte třídy tak, aby se zobrazují vlastnosti a pole.

3.  Ve třídě, klikněte pravým tlačítkem na pole nebo vlastnost a zvolte **zobrazit jako asociace kolekce**.

Vlastnost nebo pole se zobrazí jako propojení s shromážděných typ řádek přidružení.

## <a name="see-also"></a>Viz také

- [Postupy: vytvoření přidružení mezi typy](how-to-create-associations-between-types.md)
- [Navrhování tříd a typů](designing-and-viewing-classes-and-types.md)
- [Zobrazování typů a vztahů](viewing-types-and-relationships.md)
