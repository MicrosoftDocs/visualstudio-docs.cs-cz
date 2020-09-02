---
title: 'Postupy: vizualizace přidružení kolekce (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 434cfc541da3c670d8d444b9a4259b33476a17d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670512"
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Postupy: Vizualizace asociace kolekce (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vlastnosti a pole, které jsou kolekcemi jiných typů, lze v diagramu tříd zobrazit jako přidružení kolekce. Na rozdíl od pravidelného přidružení, které zobrazuje pole nebo vlastnost jako čáru spojující vlastnící třídu s typem pole, je přidružení kolekce zobrazeno jako čára spojující vlastnící třídu s typem, který je k disřádku.

### <a name="to-create-a-collection-association"></a>Vytvoření přidružení kolekce

1. V kódu vytvořte vlastnost nebo pole, jejichž typ je sám kolekcí silného typu.

2. V diagramu tříd rozbalte třídu tak, aby se zobrazily vlastnosti a pole.

3. Ve třídě klikněte pravým tlačítkem myši na pole nebo vlastnost a vyberte možnost **Zobrazit jako přidružení kolekce**.

     Vlastnost nebo pole se zobrazí jako asociační čára, která se připojuje ke shromážděnému typu.

## <a name="see-also"></a>Viz také
 [Postupy: vytváření asociací mezi typy (návrhář tříd)](../ide/how-to-create-associations-between-types-class-designer.md) [navrhování tříd a typů (návrhář tříd)](../ide/designing-classes-and-types-class-designer.md) [zobrazení typů a vztahů (návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md)
