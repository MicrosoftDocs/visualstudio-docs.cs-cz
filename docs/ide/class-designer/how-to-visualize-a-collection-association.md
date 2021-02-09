---
title: Vizualizace asociace kolekce
description: Naučte se vizualizovat přidružení kolekce v Návrhář tříd.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e4e446925b2ee46bc846a3edfbf09fb2eb695ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912635"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Postupy: vizualizace přidružení kolekce v Návrhář tříd

Vlastnosti a pole, které jsou kolekcemi jiných typů, lze v diagramu tříd zobrazit jako přidružení kolekce. Na rozdíl od pravidelného přidružení, které zobrazuje pole nebo vlastnost jako čáru spojující vlastnící třídu s typem pole, je přidružení kolekce zobrazeno jako čára spojující vlastnící třídu s typem, který je k disřádku.

## <a name="to-create-a-collection-association"></a>Vytvoření přidružení kolekce

1. V kódu vytvořte vlastnost nebo pole, jejichž typ je sám kolekcí silného typu.

2. V diagramu tříd rozbalte třídu tak, aby se zobrazily vlastnosti a pole.

3. Ve třídě klikněte pravým tlačítkem myši na pole nebo vlastnost a vyberte možnost **Zobrazit jako přidružení kolekce**.

Vlastnost nebo pole se zobrazí jako asociační čára, která se připojuje ke shromážděnému typu.

## <a name="see-also"></a>Viz také

- [Postupy: vytváření přidružení mezi typy](how-to-create-associations-between-types.md)
- [Navrhování tříd a typů](designing-and-viewing-classes-and-types.md)
